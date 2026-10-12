Hyperwave — Setup Guide
Version 0.9.9 (early test release). If something doesn't work, please click Send feedback in the About section at the bottom of the dashboard.
Hyperwave is one small Windows app, HyperwaveStation.exe, that runs your stream's chat overlay and your music. It works with almost any music player: Spotify (Free or Premium), YouTube Music, Apple Music, a browser tab, and more. It gives you:
Hyperwave Deck — a control panel for your stream on your PC, phone, tablet or Elgato Stream Deck: switch OBS scenes, clip, record, go live, mute, run your music, and read and reply to chat from every platform.
Hyperwave Chat — Twitch, Kick, YouTube and TikTok chat in one OBS overlay, with emotes, 20 animations, rain and scrolling modes, bubbles, profile pictures, and new songs and song requests shown right in chat.
Now Playing overlay for OBS — song, artist, album art, live progress bar, "requested by" name. Fonts, colours, sizes and 7 layouts are all yours to change.
Song requests from Twitch channel points, Kick channel rewards, YouTube `!sr`, and TikTok (through TikFinity), all with the same rules.
Remote DJ — a mod controls your music from any browser or phone: search, queue, playlists, play/pause, skip, volume, shuffle, devices.
Mod chat commands — `!skip` `!pause` `!play` `!vol 40` `!playlist <name or link>` `!sron` `!sroff` and more.
You need: Windows 10/11 and OBS. No paid music account needed: pick any player on your PC, the free YouTube Music app, Spotify Premium or Last.fm (see section 2 for what each one can do). Streamer.bot is optional but recommended — it's what posts replies in chat.
---
1. Install
Make a folder: `C:\Hyperwave\`
Copy `HyperwaveStation.exe` and the `web` folder into it.
Double-click HyperwaveStation.exe.
Windows may show "Windows protected your PC" because the app isn't code-signed. Click More info → Run anyway. (The full source code is in the `source` folder if you want to check or build it yourself.)
A small console window opens and your browser opens the dashboard at `http://127.0.0.1:7575`. Keep the console window open while you stream — closing it quits the app.
> Tip: to start it with Windows, press `Win + R`, type `shell:startup`, and drop a shortcut to `HyperwaveStation.exe` in that folder.
---
2. Pick your music
Dashboard → Music. Pick where your music comes from. Everything else (the overlay, requests, the deck, the DJ page, chat commands) follows it and only shows controls your player allows. You can switch any time.
	Any player on this PC	YouTube Music app	Spotify Premium	Last.fm
Setup	none	~2 minutes	~3 minutes	~2 minutes
Account needed	no	free YouTube account	Premium	free Last.fm account
Now playing + album art	✓	✓	✓	✓
Progress bar	✓ (most players)	✓	✓	–
Play / pause / skip / back	✓	✓	✓	–
Volume, shuffle, repeat	– (some players: shuffle/repeat)	✓	✓	–
Song requests	request list	straight into its queue	straight into its queue	request list
Search, Up next, Play now	–	✓	✓	–
Playlists, devices	–	–	✓	–
2a. Any player on this PC (no setup)
Works with Spotify Free, Apple Music, YouTube or SoundCloud in a browser, TIDAL, Deezer, Amazon Music, foobar2000, MusicBee and most other players. Hyperwave reads the same song info Windows shows when you press a media key.
Pick Any player on this PC.
Play music. The bar at the top of the dashboard shows the song.
Optional: under Follow, pick one player (for example Spotify) so a YouTube video in another tab doesn't take over the overlay.
Windows only lets apps press play, pause, skip and back, so viewers' song requests go on a request list (see Song requests below).
2b. YouTube Music app (free, full control)
Install the free YouTube Music desktop app from github.com/th-ch/youtube-music/releases (the `.exe` setup; it's a community app, also called Pear Desktop) and sign in.
In its top menu: Plugins → API Server [Beta] → Enabled. Leave Port `26538` and Authorization strategy Authorize at first request.
Dashboard → Music → YouTube Music app → Connect YouTube Music.
YouTube Music asks "Allow hyperwave-station to access the API?" → Allow.
Requests go straight into YouTube Music's queue, in the order viewers asked, ahead of its autoplay songs.
2c. Spotify Premium (full control, plus playlists)
Go to developer.spotify.com/dashboard and log in with your Premium account.
Click Create app and fill in:
Field	Value
App name	`Hyperwave Station`
App description	`Now playing overlay and song requests`
Redirect URI	`http://127.0.0.1:7575/callback` → click Add
Which API/SDKs	tick Web API
Tick the terms box and click Save.
Already have a Spotify developer app from an older song-request setup? You can reuse it — just add the redirect URI above to it.
On the app page click Settings and copy the Client ID. (You don't need the Client Secret.)
Dashboard → Music → Spotify Premium: paste it into Paste your Client ID → Save Client ID.
Click Connect Spotify and approve.
Open Spotify on your PC and play anything. The bar at the top of the dashboard goes live.
Spotify's 2026 rules for developer apps, in plain terms: the app owner must keep Premium, a developer app can have at most 5 Spotify users (you only need 1 — yourself), and search returns at most 10 results per query. None of this limits normal streaming use. No Premium? Use Any player on this PC with the free Spotify app.
2d. Last.fm (show what you scrobble from any device)
For music on your phone, a console, Plex or a record player app that scrobbles to Last.fm.
While signed in to Last.fm, open last.fm/api/account/create. Application name `Hyperwave Station`; leave Callback URL and Homepage empty. Submit and copy the API key.
Dashboard → Music → Last.fm: type your username and the API key, then Save.
Last.fm can only show the song (no pause or skip, no progress bar). Requests go on a request list.
---
3. Add the Now Playing overlay to OBS
Dashboard → Now Playing overlay → Open the overlay designer (or go to `http://127.0.0.1:7575/overlay`).
Style tab: pick a Starting look, then tune layout, fonts, sizes, colours, artwork/visualizer, progress bar and behaviour. The preview shows your real song if music is playing, otherwise a demo.
Position: drag the overlay in the preview to where you want it. The preview opens at Actual size (how big it looks on stream); click Whole screen at the top of the preview to see where it sits on your stream.
It snaps to the edges and centre. Hold Alt while dragging to place it freely.
Fine adjust arrows move it by the amount in Each click moves (1–50 px). You can also click the overlay and use the arrow keys (Shift = 10× further), or type exact X / Y numbers.
Snap to a spot jumps to a corner, edge or the centre, using Gap from the screen edge.
Set Screen size to match your OBS canvas (Settings → Video → Base Canvas Resolution).
Click Copy OBS link.
In OBS: Sources → + → Browser → name it `Now Playing` → OK.
OBS setting	Value
Local file	unticked
URL	paste the link
Width / Height	the same as Screen size in the designer — `1920` / `1080` for most people
Refresh browser when scene becomes active	ticked
Leave the source covering the whole screen (right-click → Transform → Fit to screen). The overlay sits exactly where you placed it in the designer.
Changed the style or position later? Copy the link again and paste it into the OBS source — the link is the settings.
Prefer a small source sized to the overlay? Position → How it's placed → Pin it to a corner of a small source.
Layouts
Card · Strip (slim bar) · Stack (big art, vertical) · Vinyl (spinning record) · Minimal (text only) · Ticker (scrolling marquee) · Glass (blurred album art background) · Player (a little desktop media-player window with a title bar, display screen and buttons)
Starting looks
Hyperwave · Clean light · Neon · Retro terminal · Glass · Minimal text · Vinyl lounge · Ticker · Retro desktop player · Synthwave · Arcade · Pastel pop · Sci-fi HUD · Monochrome
Visualizer
Style tab → Artwork & visualizer → Show in the artwork area: Album art, Visualizer, or Visualizer over dimmed album art. Styles: Bars, Mirror, Wave, Radial (spins around the album art), LED meter, Orb. You can pick the colour (accent, gradient, rainbow, match album art), the number of bars and the speed.
The visualizer moves with play/pause and each song gets its own tempo and character, but music players don't let apps hear the audio, so it doesn't follow the real beat.
Running it without the app (standalone, Spotify Premium only)
The overlay also works on its own, e.g. hosted on GitHub Pages next to Hyperwave Chat:
Upload `for-github-pages/nowplaying.html` to your GitHub Pages repo.
Open it → Connect tab → Directly from Spotify → paste your Client ID.
Add the page's address (e.g. `https://yourname.github.io/hyperwave/nowplaying.html`) as a second Redirect URI in your Spotify app.
Click Connect Spotify, then copy the OBS link. That link contains your Spotify login — never show it on stream.
Standalone shows the song and progress only. Requests, "requested by" names, pop-ups and the DJ deck need the app.
---
4. Song requests
Rules (dashboard → Song requests)
Setting	Default	What it does
Requests are open	on	Master switch. Mods can flip it with `!sron` / `!sroff` or the DJ deck.
Songs waiting per viewer	3	Stops one viewer flooding the queue.
Longest song allowed	8 min	Blocks 20-minute ambient tracks.
Same song again within	30 min	Stops repeats.
Per-viewer cooldown	0 s	Optional time between a viewer's requests.
Block explicit songs	off	Uses the explicit flag from Spotify, YouTube Music or the song lookup.
Blocklist	empty	Words, artists or track IDs, one per line.
Viewers can request by name (`Mr. Blue Sky`), by `song - artist`, `song by artist`, or by pasting a Spotify or YouTube link. Use Try it on the dashboard to test.
The request list (any player on this PC, Last.fm)
These can't take songs from other apps, so requests wait on a request list: in the Song requests section of the dashboard, under Music on the deck, and in the DJ page's Requests tab. Each request has a Find button that searches for it in the player you're using (Spotify, YouTube, Apple Music and others). When Hyperwave sees the song playing, it ticks it off and the overlay shows who requested it. You can also tick songs off yourself, remove them, or clear the list. Songs are looked up in Apple's free music catalog, so the length and explicit rules still work.
Chat replies (dashboard → Chat replies)
Every reply is editable. Placeholders: `{user}` `{title}` `{artist}` `{pos}` (queue position) `{max}`; the `!song` line also takes `{req}` and `{link}`.
---
5. Streamer.bot (Twitch, Kick, YouTube, TikTok)
Streamer.bot catches the redeem or command, asks Hyperwave Station to do the work, and posts the reply in the right chat. One action handles everything.
5a. Create the action
Streamer.bot → Actions → right-click → Add → Name: `Hyperwave - Spotify` → OK. (The name is from when Hyperwave only did Spotify. It works with every music source, so keep it as is.)
In Sub-Actions, right-click → Core → C# → Execute C# Code.
Open `streamerbot\Hyperwave-Spotify.cs` from this package in Notepad, select all, copy, and paste it over everything in the code window.
Click Compile. The log at the bottom must say Compiled successfully.
If it fails to compile, click the Add refs button in the code window, then click Compile again. That adds the references the code needs, and it should compile with no problem.
Still failing? Open the References tab, right-click → Add reference from file…, and add `System.dll` from `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\`. Then compile again.
Click Save and Compile, then OK.
> Moving from an older Spotify song-request action? Remove its trigger (or disable that action) so requests aren't queued twice.
5b. Twitch channel points
Twitch dashboard → Viewer Rewards → Channel Points → Manage Rewards → + Add Custom Reward:
Name `Song Request` · Require Viewer to Enter Text: ON · Prompt `Song name, "song - artist", or a song link`
Streamer.bot → `Hyperwave - Spotify` → Triggers → right-click → Add → Twitch → Channel Reward → Reward Redemption → pick Song Request → OK.
Refunds: if a request fails (not found, too long…), the code refunds the points automatically — but Twitch only allows that for rewards created in Streamer.bot (Platforms → Twitch → Channel Point Rewards → Add). Rewards made on the Twitch dashboard still work; they just won't auto-refund.
5c. Kick channel rewards
Kick creator dashboard → Channel Rewards → create `Song Request` with user input required.
Streamer.bot → `Hyperwave - Spotify` → Triggers → Add → Kick → Channel Reward → Reward Redemption → pick it.
(Requires Streamer.bot 1.0.2 or newer with your Kick account connected.)
5d. YouTube (command + optional points cost)
YouTube has no channel points, so viewers type `!sr song name`.
Streamer.bot → Commands → right-click → Add:
Field	Value
Name	`Song Request`
Commands	`!sr` (add `!songrequest` on a new line if you like)
Location	Start
Sources	tick YouTube (tick Twitch/Kick chat too if you want `!sr` there)
Permitted	everyone
Cooldowns	e.g. user cooldown 60 s
`Hyperwave - Spotify` → Triggers → Add → Core → Commands → Command Triggered → pick Song Request.
Charging points: after the C# sub-action, add Logic → If/Else: `hwResult` Equals `added` → run whatever takes your points currency. Every result code is listed at the top of the `.cs` file.
5e. TikTok (through TikFinity)
TikTok has no chat API, so TikFinity bridges it (same as Hyperwave Chat).
TikFinity must be connected to Streamer.bot's WebSocket Server (Streamer.bot Servers/Clients → WebSocket Server, `127.0.0.1:8080`, Auto Start on).
TikFinity → Actions & Events → new action → Streamer.bot: Run Action → `Hyperwave - Spotify`. Create an event that fires it on the command `!sr` (or on a gift, if you'd rather sell requests for gifts).
Redeem it once, then in Streamer.bot open Action History → Inspect Variables and note which variables hold the TikTok user name and comment text. If they aren't `nickname` / `comment`, add a Core → Arguments → Set Argument sub-action above the C#: `hwUser` = `%theirNameVariable%`, `hwInput` = `%theirCommentVariable%`.
TikTok can't receive bot replies, so the result shows as a pop-up on the Now Playing overlay instead.
5f. `!song` and mod DJ commands
Commands → Add → Name `Now Playing`, Commands `!song` and `!np`, Sources: all your chats, Permitted: everyone.
Commands → Add → Name `DJ`, one command per line:
```
   !skip
   !prev
   !pause
   !play
   !vol
   !shuffle
   !repeat
   !playlist
   !playnow
   !sron
   !sroff
   ```
Sources: all your chats. Permissions: Moderators only (plus the broadcaster).
Add both commands as Command Triggered triggers on `Hyperwave - Spotify`.
Command	Example	Does
`!skip` / `!prev`	`!skip`	Next / previous track
`!pause` / `!play`	`!play`	Pause / resume
`!play <song>` / `!playnow <song>`	`!playnow sandstorm`	Play a song right now
`!vol`	`!vol 40`, `!vol up`, `!vol -5`	Volume
`!shuffle`	`!shuffle on`	Toggle shuffle
`!repeat`	`!repeat track`	off / track / playlist
`!playlist`	`!playlist boss fight` or a link	Start one of your playlists (by name) or any playlist/album link
`!sron` / `!sroff`		Open / close viewer requests
`!song` / `!np`		Everyone: what's playing
Replies always go back to the chat the command came from. If one ever lands in the wrong chat, put a Set Argument `hwPlatform` = `kick` / `youtube` / `twitch` above the C#.
---
6. Remote DJ (a mod runs your music from anywhere)
Your mod gets a link and a passkey. They type the passkey once and their phone or PC remembers it.
Set your passkey
Dashboard → Remote DJ → Passkey. Type your own (6–64 letters, numbers, dashes or underscores, e.g. `fleet-radio-o7`) and click Save passkey, or click Random. It never changes on its own. Changing it signs every DJ out instantly.
Pick a link type
Same link every stream (recommended). Your mod bookmarks it once. Free with Tailscale Funnel:
Install Tailscale from tailscale.com/download and sign in (free Personal plan).
Press `Win + R`, type `cmd`, press Enter, and run: `tailscale funnel --bg 7576`
The first time, it prints a link to enable HTTPS and Funnel. Open it, approve, and run the command again.
It prints `Available on the internet: https://yourpc.tailXXXX.ts.net/`. Paste that into Your permanent DJ address → Save address.
`--bg` keeps the address working after restarts. Your mod doesn't need Tailscale. To remove it completely: `tailscale funnel reset`.
Own a domain on Cloudflare? Expand I have my own domain on Cloudflare on the dashboard instead: make a tunnel in Zero Trust, paste its token, point a hostname like `dj.yourdomain.com` at `HTTP 127.0.0.1:7576`. The app runs the tunnel for you.
New link each time. No account needed: put `cloudflared-windows-amd64.exe` (from github.com/cloudflare/cloudflared/releases/latest) next to the app. You'll get a new random link every time you open DJ access.
Open and close DJ access
Open DJ access / Close DJ access on the dashboard. While closed, your link only shows "DJ access is closed", even with a permanent address. A mod who has the page open is let in automatically the moment you open it.
Tick Open DJ access automatically when Hyperwave Station starts if you want it always on while the app runs.
Send it to your mod
Copy link (they type the passkey once) or Copy with passkey (signs them in with one tap). Send it by Discord DM, never in public chat.
Your mod gets:
play / pause / skip / back, volume, shuffle, repeat, device picker (only the ones your music source allows)
Search → Queue or Play now (with a request list: Add to list); paste a Spotify or YouTube link
Up next (the player's queue, or the request list), Playlists (Spotify only, with Play and Shuffle), Requests (who asked for what, from which platform)
a switch to open or close viewer requests
Security: anyone with the passkey controls your music while DJ access is open. The link only exposes the DJ deck — never your dashboard or settings. After 8 wrong passkeys a visitor is locked out for 10 minutes (40 wrong tries from anyone locks the deck for everyone for 10 minutes), so pick something that isn't easy to guess.
You can also use the DJ deck yourself at `http://127.0.0.1:7575/dj` (great on a second monitor or Stream Deck browser button).
---
7. Commands without a bot (no Streamer.bot)
Dashboard → Commands without a bot: the app can read your Twitch and Kick chat itself and act on `!sr` and mod commands. It can't post replies (it doesn't log in as a bot), so new requests and DJ actions appear as pop-ups on the overlay.
Leave this OFF if you use Streamer.bot, or every command runs twice.
If Kick blocks the automatic chatroom lookup, find your chatroom ID by opening `https://kick.com/api/v2/channels/YOURNAME` in your browser and copying the number after `"chatroom":{"id":`.
---
8. Hyperwave Chat
Hyperwave Chat is built in. Open the dashboard → Hyperwave Chat → Open the chat designer (or go to `http://127.0.0.1:7575/chat`).
Connect tab: under Chat sources, Twitch works straight away with your channel name (it's filled in from the dashboard if you set one there). Set Kick, YouTube and TikTok the same way. YouTube needs Streamer.bot; TikTok needs TikFinity.
Hyperwave Station (also on the Connect tab): Show music from Hyperwave Station is on when you open the designer from the app. Each new song appears in chat as "Now playing" with its album art, and every song request shows who asked for it. Turn on Show DJ actions to also show skips, pauses and volume changes.
Style tab: click a starting style. Position tab: pick your stream resolution and drag the dashed box to where chat should sit.
Want old messages to disappear? Under Layout → Fade messages out after, turn off Never hide messages and pick a time in seconds or minutes. Each message fades away that long after it arrives.
Click Copy link. In OBS add a Browser source named `Hyperwave Chat`: untick Local file, paste the link into URL, Width `1920`, Height `1080` (or your stream resolution), leave Shutdown source when not visible unticked. Then right-click it → Transform → Fit to screen.
Changed something? Click Copy link again (the designer warns you when your OBS link is out of date), paste it into the source, then right-click it → Refresh.
The Connection check on the Connect tab tells you if each source is working, and says "Real chat is arriving" once your viewers' messages come through.
Prefer not to run the app? `for-github-pages/index.html` works on its own from any web host (GitHub Pages is free). Music messages still work from there whenever Station is running on the same PC.
Upgrading from 0.9.1 or earlier: if you copied a `chat.html` into the `web` folder, delete it. Files in that folder replace the built-in pages, so an old copy would hide the new chat. Then copy your chat link again, because the designer now places chat on the whole screen: set the OBS source to your full stream size and use Fit to screen.
---
9. Hyperwave Deck (OBS, clips, chat, Stream Deck)
Open it from the dashboard → OBS & Deck → Open the Hyperwave Deck, or go to `http://127.0.0.1:7575/deck`.
Connect OBS (OBS 28 or newer)
In OBS: Tools → WebSocket Server Settings → tick Enable WebSocket server → Show Connect Info → copy the Server Password.
Dashboard → OBS & Deck → tick Connect to OBS, paste the password, Save. It shows "Connected to OBS" with your scene and audio counts.
For clips: in OBS Settings → Output → Replay Buffer, turn it on (30–60 seconds). Leave Keep the replay buffer running ticked in Hyperwave.
The Clip button saves the OBS replay to your PC and, if you tick it, also makes a Twitch clip (Twitch clips only work while you're live).
Replies and Twitch clips — pick one under step 2 (Automatic uses whichever is set up):
Twitch sign-in in Station: make a free app at dev.twitch.tv/console/apps (Redirect URL `https://localhost`, Client Type Public), paste its Client ID, Save, then Sign in to Twitch and enter the code at twitch.tv/activate. Twitch only.
Streamer.bot: turn on its WebSocket Server with Authentication and a password, then tick Connect to Streamer.bot and type the password. Posts to Twitch, Kick and YouTube. For Twitch clips, make an action named `Hyperwave - Twitch Clip` with the sub-action Twitch → Clips → Create Clip.
Chat in the deck — Twitch and Kick use the channel names under Commands without a bot. YouTube comes through Streamer.bot, TikTok through TikFinity. Quick replies are buttons above the reply box.
My Deck (your own stream deck, no Elgato needed) — the deck opens on My Deck: big buttons you design yourself. Tap Edit, then Add button: give it a name, an icon and a colour, and list what it does. One button can do several things in order (for example: switch to the BRB scene → mute the mic → post "be right back" in chat), with optional waits between steps (in seconds or minutes, up to an hour each, e.g. BRB scene → wait 5 minutes → back to Gameplay). Buttons with long waits keep running in the background; press the button again to stop it early. Tick Press and hold to run for buttons you don't want to bump. Use the arrows to reorder and the Size slider to fit your screen. Your buttons are saved in Hyperwave Station, so your PC, phone and tablet all show the same deck. An old tablet makes a great dedicated deck.
Phones and tablets — tick Let phones and tablets on my Wi-Fi open the deck and Save. The dashboard shows a QR code: point your phone's camera at it and the deck opens already signed in (or use Copy link and open it on your phone). Set your own deck passkey and click Save passkey, or click Generate. When Windows asks, allow Hyperwave Station on Private networks. It never works from outside your home network.
Elgato Stream Deck — in OBS & Deck → Elgato Stream Deck, pick what the key does and click Copy link. For your own My Deck buttons, open the button in Edit; its Elgato link is at the bottom. In the Stream Deck app drag System → Website onto a key, paste the link into URL, and tick GET request in background.
Going live and ending the stream need a 1-second press-and-hold on the deck so they can't be bumped by accident.
---
10. Troubleshooting
Problem	Fix
Overlay blank in OBS	Is music playing and the app open? Designer → Behaviour → tick Show connection errors, re-copy the link. Right-click the OBS source → Refresh.
"the music player isn't open right now"	Open your player (Spotify needs an active device, so press play once).
Any player: nothing shows	Play a song, then check the dashboard's Music section. If Follow is set to one player, that player must be open. Some very old players don't talk to Windows; update them.
Any player: the overlay shows a YouTube video instead of my music	Dashboard → Music → Follow → pick your music player.
YouTube Music: "isn't open"	Open the YouTube Music app and check Plugins → API Server is enabled.
YouTube Music: "needs you to allow Hyperwave"	Click Connect YouTube Music again and choose Allow in YouTube Music.
Last.fm: "hides its listening"	Last.fm → Settings → Privacy → untick Hide recent listening information.
"Premium required" / 403	Reconnect Spotify with the Premium account that owns the developer app.
`INVALID_CLIENT: Invalid redirect URI`	The Redirect URI in your Spotify app must be exactly `http://127.0.0.1:7575/callback` (not `localhost`).
Streamer.bot says "music system is offline"	HyperwaveStation.exe isn't running, or you changed its port (edit `STATION` at the top of the `.cs`).
Request queued twice	An old song request action still has the same trigger, or Commands without a bot is on alongside Streamer.bot.
"Port 7575 is busy"	The app is already running (check the taskbar).
Mod sees "DJ access is closed"	Click Open DJ access (or tick auto-open). Their page connects by itself.
Mod gets "That passkey didn't work"	You changed the passkey. Send them the new one; it's case-sensitive.
Permanent address says it can't reach your PC	Run `tailscale funnel status` in cmd. If nothing shows, run `tailscale funnel --bg 7576` again. Some networks can't test their own address, so ask your mod to try the link.
"New link each time" link stopped working	You closed DJ access or quit the app. Open it again and resend the new link.
Wrong song found	Ask viewers for `song - artist`, or a Spotify or YouTube link.
Settings are saved in `hyperwave-station.json` next to the exe. It holds your Spotify, YouTube Music and Twitch logins — don't share that file.
---
Example: a themed reply pack
The default replies are neutral so the package works for anyone. Here's how a themed channel might set them (Homeworld fleet voice):
Reply	Text
Song added	`🛰️ {title} by {artist} locked into the fleet playlist (#{pos}) — o7 @{user}!`
Not found	`@{user} sensors found no match, pilot. Try "song - artist" or a Spotify link.`
Requests closed	`@{user} comms are locked — song requests are closed right now.`
Too long	`@{user} that track exceeds jump range (max {max} min).`
Too many waiting	`@{user} you already have {max} tracks in hyperspace — let one arrive first.`
Already requested	`@{user} that one's already in the fleet queue, pilot.`
Player not open	`@{user} the fleet radio is offline right now.`
`!song`	`🛰️ Now playing on fleet comms: {title} by {artist}{req}`
---
For package maintainers: the About section
The About section at the bottom of the dashboard reads `web\about.json`. Edit it in Notepad (no rebuild needed) and reload the dashboard. Leave a link as `""` to hide its button.
Field	What it is
`about`	The paragraph shown
`tip` / `tipLabel` / `tipQr`	Tip link, its button text, and the QR image file in `web\`
`feedback`	Link for the Send feedback button (e.g. a Google Form)
`twitch` / `kick`	Channel buttons
