# noobstr.me
Noobstr.me - An onboarding website / read-onlly client for NOSTR.  Just Go!

Bugs that still exist:
- Settings menu: buttons hang off right side
- Code comments are AI generated, some may not be relevant, some more may be needed to be added by human, and some (most) are commenting on code that I don't understand well enough to audit :D

Best Practices Improvements:

- Contributors much smarter than me that can tell me how I or AI has bungled the code, help with convention, sanitize, reduce vulnerabilities, optimize the code, etc
- Ask AI to further help me optimize and enhance security / remove vulnerabilities
- Add @hodlbod 's book Building Nostr, https://building-nostr.coracle.social/ , https://github.com/nostr-protocol/nips , and other 'nostr best practices' information / primary sources into ai and ask it to look at code and make suggestions
Enhancements planned:
- Check more relays when searching by npub, 3-5.  nostr.band Iris, Coracle, Phoenix
- resolve all media links to just the base domain + …; 'video' 'image' , based on filetype
- scan for strings that are wrapped that are not yet resolved to 'npub' or similar, long links, and garbage text so that they can be ellipsed
- Ability to click on note to go see note on njump.me Also, a 'See whole conversation' button on each… linking to one of a set of random web clients that displays conversations well
- clicking 'just go' with a feed already there, and with the same settings, should only load new notes without disturbing the reading order.  right now it's refreshing the whole page.
- add a few noobie / normie friendly relays to the dropdown.  Although this is prone to hubris and makes maintenance more unwieldy.

Questions:

- Hosting considerations?
- What's an appropriate number of notes to fetch, and how much should i rate limit happy clickers on the load button? It also calls out to fetch usernames and avatars.
- What size should I limit displayed avatars to for general purpose?
- What sort of performance hit will loading usernames on slow connections have?  Think 3rd world older phones (high signal onboarding).
- how should I monitor or accept feedback about performance?  It's hosted on a 3rd party vps right now with other websites.
- Who to talk to about getting this listed at places like https://nostrapps.com/ or grownostr.org at the appropriate time?
