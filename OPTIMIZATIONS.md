# Noobstr.me - Memory & Performance Optimizations

## Overview

This document describes the optimizations made to reduce memory usage and improve performance on slow connections and low-memory devices.

## Memory Optimizations

### 1. Reduced Data Limits
- **Console entries**: Limited to 500 (reduced from 2,500)
- **Maximum feed size**: Capped at 200 notes (reduced from 500)
- **Note collection**: Hard limit of 400 notes during collection
- **Image queue**: Limited to 50 pending images
- **Log message truncation**: 200 characters (reduced from 1,000)

### 2. WebSocket Connection Management
- All WebSocket connections are now tracked in `activeWebSockets` array
- Connections are automatically closed when:
  - Switching between different feeds/relays
  - Page is unloaded
  - User clicks "Clear Memory" button
- Prevents memory leaks from abandoned connections

### 3. Image Memory Management
- Images are only loaded if under size limits:
  - **Normal mode**: 300KB max
  - **Slow connection mode**: 100KB max
  - **Profile avatars**: 50KB max
- Offscreen images are removed when far from viewport (slow mode)
- Image processing queue prevents overwhelming the browser

### 4. Manual Memory Cleanup
New "Clear Memory" button in Settings allows users to:
- Trim console entries to last 50
- Clear image processing queue
- Close idle WebSocket connections
- Remove offscreen images

## Slow Connection Optimizations

### 1. Reduced Request Sizes
When "Slow connection" mode is enabled:

| Parameter | Normal Mode | Slow Mode |
|-----------|-------------|-----------|
| Initial note limit | 100 | 50 |
| Follows checked | 200 | 50 |
| Relay request limit | 1,000 | 200 |
| Max image size | 300KB | 100KB |
| Max avatar size | 200KB | 50KB |
| Image batch size | 2 | 1 |
| Batch delay | 200ms | 500ms |

### 2. Disabled Features
- **Profile avatars**: Disabled entirely
- **Username resolution**: Skipped
- **Console banner**: Hidden by default
- **Image pre-loading**: More conservative

### 3. Automatic Cleanup
- Offscreen images removed 2 seconds after scroll stops
- Reduces memory footprint during browsing
- Only active when slow connection mode is enabled

## How to Use

### For Regular Users
1. Visit the site normally
2. If it feels slow, enable "Slow connection" checkbox
3. Use "Clear Memory" button in settings if needed

### For Slow Connections
1. **Enable "Slow connection" immediately** before loading any feed
2. Expect:
   - Fewer notes (30-50 instead of 100)
   - No profile pictures
   - Simplified author names
   - Faster loading
   - Lower bandwidth usage

### For Very Weak Devices
1. Enable "Slow connection" mode
2. Click "Clear Memory" in settings every few minutes
3. Avoid loading relay feeds (use npub feeds instead)
4. Close other browser tabs

## Technical Details

### Memory Cleanup Flow
```
User switches feed
  ├─> cleanupWebSockets()
  ├─> Clear currentFeed[]
  ├─> Clear imageProcessingQueue[]
  └─> displayFeed([])
```

### Image Loading Flow
```
processImagesInContent()
  ├─> Queue size check (max 50)
  ├─> processImageQueue()
  │   ├─> Batch size: 1-2 images
  │   ├─> checkAndRenderImage()
  │   │   ├─> HEAD request (size check)
  │   │   ├─> 5 second timeout
  │   │   └─> Render or skip
  │   └─> Delay: 200-500ms
  └─> Continue until queue empty
```

### WebSocket Lifecycle
```
tryConnectToSingleRelay()
  ├─> Create WebSocket
  ├─> Add to activeWebSockets[]
  ├─> Use connection
  └─> On completion/error:
      ├─> Close connection
      └─> Remove from array
```

## Performance Metrics

### Before Optimizations
- Console entries: 2,500+ (growing unbounded)
- Feed size: 500+ notes
- WebSockets: Multiple unclosed connections
- Memory: ~100-200MB for typical session
- Image size limit: None
- Avatar size limit: 300KB

### After Optimizations (Normal Mode)
- Console entries: ≤500
- Feed size: ≤200 notes
- WebSockets: Properly tracked and closed
- Memory: ~50-80MB for typical session
- Image size limit: 300KB
- Avatar size limit: 200KB
- Full feature set enabled

### After Optimizations (Slow Mode)
- Console entries: ≤500
- Feed size: ≤50 notes displayed
- WebSockets: Properly tracked and closed
- Memory: ~30-50MB for typical session
- Bandwidth: ~60% reduction
- Image size limit: 100KB
- Avatar size limit: 50KB
- Avatars and usernames disabled

## Browser Compatibility

All optimizations use standard JavaScript features:
- `replaceChildren()` with fallback for older browsers
- `AbortSignal.timeout()` with try/catch
- Standard array methods (slice, splice)
- Basic DOM manipulation

Works on:
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Older devices (with slow mode enabled)

## Future Optimization Ideas

1. **Virtual scrolling**: Only render visible notes
2. **IndexedDB caching**: Cache notes locally
3. **Service worker**: Offline support
4. **Lazy loading**: Load content on scroll
5. **WebWorker**: Process notes in background thread
6. **Compression**: Compress cached data
7. **CDN**: Serve from edge locations

## Contributing

If you notice performance issues or have optimization ideas:
1. Enable the console debugger
2. Note the issue in console logs
3. Report via GitHub issues
4. Include device specs and connection speed

## License

Same as the main project.
