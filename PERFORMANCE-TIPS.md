# Performance Tips for Noobstr.me

## Quick Start

### ⚡ For Fast Connections & Modern Devices
Just click "Just Go!" and enjoy. Everything works automatically.

### 🐌 For Slow Connections
1. ✅ Check the "Slow connection?" checkbox **before** clicking "Just Go!"
2. You'll see fewer notes (30-50) but they'll load much faster
3. No profile pictures = less bandwidth
4. Automatic memory cleanup keeps things smooth

### 📱 For Old Phones / Tablets
1. ✅ Enable "Slow connection" mode
2. Open Settings ⚙️ → Click "🧹 Clear Memory" every few minutes
3. Avoid switching feeds too often
4. Close other browser tabs

## Common Issues & Solutions

### "The page is using too much memory"
**Solution:**
1. Open Settings (⚙️)
2. Click "🧹 Clear Memory" button
3. Enable "Slow connection" mode
4. Reload the page if needed

### "Images aren't loading"
**Possible causes:**
- Slow connection mode is enabled (images disabled)
- Images are too large (>100-300KB)
- Slow internet connection

**Solution:**
- Disable "Slow connection" mode to enable images
- Wait longer for images to load
- Some images may be too large and are skipped

### "Not many notes showing up"
**In slow mode:**
- Limited to 50 notes max (normal: 100-200)
- Fewer follows checked (50 vs 200)

**Solution:**
- Disable "Slow connection" mode for more notes
- Or accept fewer notes for better performance

### "Page feels sluggish"
**Solution:**
1. Enable "Slow connection" mode
2. Clear memory in settings
3. Close the console debugger (it uses memory)
4. Try a different npub or relay

## Feature Differences by Mode

| Feature | Normal Mode | Slow Connection Mode |
|---------|-------------|---------------------|
| Notes displayed | 100-200 | 30-50 |
| Profile pictures | ✅ Yes (200KB max) | ❌ No |
| Usernames resolved | ✅ Yes | ❌ No (shows pubkey) |
| Images in notes | ✅ Up to 300KB | ✅ Up to 100KB |
| Follows checked | 200 | 50 |
| Relay request limit | 1,000 notes | 200 notes |
| Console debugger | 📊 Visible | 🔇 Hidden |
| Memory usage | ~50-80MB | ~30-50MB |
| Bandwidth usage | Normal | ~60% less |

## Best Practices

### For Everyone
- Clear memory occasionally using the button in settings
- Don't keep dozens of tabs open
- Close the console debugger if you don't need it

### For Slow Connections
- Enable slow mode **before** loading a feed
- Stick to one npub/relay at a time
- Clear memory between different feeds
- Expect fewer notes but faster loading

### For Developers/Power Users
- Check console logs for performance insights
- Monitor WebSocket connections in browser DevTools
- Report performance issues with device/connection details

## Understanding the Indicators

### Console Debugger Messages
- 🔧 **Ready...** - Waiting for you to load something
- 📡 **Checking relay info** - Validating relay before connecting
- 🔑 **Using pubkey** - Successfully decoded your npub
- 📝 **Got a real note** - Found a valid note
- ⚠️ **Image too large** - Skipped an image (too big)
- 🧹 **Clearing memory** - Cleanup in progress
- ✅ **Done getting notes** - Feed loaded successfully

### When Memory is Low
Signs you need to clear memory:
- Page scrolling feels choppy
- Images load very slowly
- Browser shows "page unresponsive" warning
- Console shows "Note limit reached" warnings

**Action:** Click Settings → 🧹 Clear Memory

## Advanced Tips

### Minimize Memory Usage
1. Enable slow connection mode
2. Expand console debugger
3. Watch for "Image too large" warnings
4. Click "Clear Memory" when you see many warnings
5. Scroll slowly to avoid loading too many images at once

### Maximize Performance on Weak Devices
1. Use Chrome or Safari (better memory management)
2. Close other tabs and apps
3. Enable slow connection mode
4. Clear browser cache/cookies regularly
5. Use WiFi instead of mobile data if possible

### When to Use Which Feed Type
- **Npub feeds**: Shows notes from someone's follows
  - More personalized
  - Slightly more bandwidth
  - Best for: Finding interesting people

- **Relay feeds**: Shows all recent notes from a relay
  - Less personalized
  - More bandwidth intensive
  - Best for: Seeing what's happening now

## Troubleshooting

### Nothing loads at all
1. Check your internet connection
2. Try the default "Just Go!" button
3. Try a different relay from nostr.watch
4. Clear browser cache
5. Try a different browser

### Stuck on "Loading notes..."
1. Wait 10-15 seconds
2. Refresh the page
3. Try a different npub/relay
4. Enable slow connection mode
5. Check console for error messages

### Console shows many errors
- **"Invalid event" errors**: Normal, relays send bad data sometimes
- **"Connection timeout"**: Try different relay
- **"Image too large"**: Normal, large images are skipped
- **"Relay connection lost"**: Network issue, try again

## Getting Help

If you're still having issues:
1. Open the console debugger (📊)
2. Expand it and scroll through messages
3. Take a screenshot of errors
4. Check if it's mentioned in this guide
5. Report via GitHub if it's a new issue

## Remember

- **Slow connection mode** is your friend on weak devices
- **Clear Memory** button fixes most memory issues
- **Fewer notes** = better performance
- **No images** = much faster loading

Happy browsing! 🤙
