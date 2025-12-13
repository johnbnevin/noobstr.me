# noobstr.me
Noobstr.me - An onboarding website / read-only client for NOSTR.  Just Go!

See an example of what gets posted on NOSTR in one click!

Intuitive onboarding website that functions as a basic read-only client for NOSTR.

Q: "What is NOSTR?" A: "I dunno.  Look @ noobstr.me and see."

## Features

✅ **One-Click Demo** - Click "Just Go!" to see real Nostr notes immediately
✅ **Save Favorites** - Save your favorite npubs and relays for quick access
✅ **Multiple Themes** - Light, dark, and clown mode (because why not? 🤡)
✅ **Read-Only** - Browse safely without needing a Nostr account
✅ **Mobile-Friendly** - Works great on phones and tablets
✅ **Performance Optimized** - Special "Slow connection" mode for weak devices

## Performance & Compatibility

Noobstr.me is optimized to work on:
- 📱 Old phones and tablets
- 🐌 Slow internet connections
- 💻 Low-memory devices
- 🌍 Any modern browser

**Enable "Slow connection" mode** for best performance on weak devices!

See [PERFORMANCE-TIPS.md](PERFORMANCE-TIPS.md) for detailed guidance.

## How It Works

1. **Default Feed**: Click "Just Go!" to see notes from a curated list of follows
2. **Custom Npub**: Enter someone's npub to see who they follow
3. **Relay Browsing**: Enter a relay URL to see all recent notes from that relay
4. **Save & Reuse**: Save your favorites in Settings for one-click access

## Technical Details

- Single HTML file (~40KB)
- No dependencies or build process
- Pure vanilla JavaScript
- Works offline after first load
- Privacy-focused (no tracking, no ads)

### Memory & Bandwidth Optimizations

For technical details about the optimizations, see [OPTIMIZATIONS.md](OPTIMIZATIONS.md).

Key features:
- Automatic WebSocket connection cleanup
- Intelligent image loading with size limits
- Memory-efficient note rendering
- Configurable feed sizes
- Manual memory cleanup button

## Development

This is a single self-contained HTML file. To modify:

1. Edit `Noobstr-1.3.html`
2. Open in browser to test
3. Deploy anywhere (GitHub Pages, Netlify, etc.)

No build process required!

## Contributing

Issues and pull requests welcome! Please include:
- Device/browser information
- Connection speed (if relevant)
- Screenshots of any issues
- Steps to reproduce

## License

Open source - use freely!

## Support

Having performance issues? Check out [PERFORMANCE-TIPS.md](PERFORMANCE-TIPS.md) for help!

---

Made with 🤙 for Nostr newbies everywhere
