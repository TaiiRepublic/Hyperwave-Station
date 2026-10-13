Hyperwave — changelog
1.0.1
Overlays that run without Station. Both overlays now come in an overlays folder next to the app, and OBS can load them straight from there as a local file. Close Hyperwave Station and they keep going: chat from Twitch and Kick (plus YouTube through Streamer.bot and TikTok through TikFinity), and your music.
Music overlay: Last.fm and YouTube Music on their own. On the music overlay's Connect tab, Directly from Last.fm shows what any scrobbling player is playing, with album art, and Directly from YouTube Music Desktop connects to the YouTube Music app with one Allow click. Spotify Premium could already do this. Song requests, the DJ page and the deck still use Station.
Scene layouts. A new Scenes tab in both overlay editors saves a look (style, position, animations) for each OBS scene as a file in overlays\layouts. When you switch scenes in OBS the overlay fades into that scene's layout by itself, no Streamer.bot needed. Scenes without a layout use your starting layout, which also carries your connections so the overlay works when OBS loads it from the folder. Without Station, the editor can save straight into the folder you pick, or download the file.
Tips now go to StreamElements. The tip button and QR code point to the TaiiRepublic StreamElements tip page.
1.0.0
Hyperwave's first full release. o7
Your own pictures on deck buttons. Upload a PNG, JPG, WebP or an animated GIF for any My Deck button, reuse pictures across buttons, and choose to show the picture only or the picture with its name.
Sounds and a soundboard. Add sound files (MP3, WAV, OGG, M4A, FLAC) and play them from the Control room's new Sounds section or from My Deck buttons, each with its own volume, plus a Stop sounds button. One click on the dashboard adds the invisible Hyperwave Sounds player to every OBS scene, so viewers hear the sounds and so do you.
Change your category from the deck. The Control room shows your current Twitch and Kick category with box art. Change category searches both at once with small box art pictures and badges for each platform, switches both in one tap, and keeps your recent picks at the top. My Deck buttons can switch category too.
Twitch uses your existing Twitch sign-in (sign in again once to allow category changes).
New Sign in to Kick on the dashboard, using Kick's official API with your own free Kick app.
More button steps: play a sound, stop sounds, show or hide an OBS source, change category, and run a Streamer.bot action.
Drag and drop on the deck.
Rearrange by dragging: in Edit, drag My Deck buttons where you want them (on a phone, hold a button for a moment, then drag). Steps inside a button can be dragged into a new order too, by their number.
Drop files from Windows: drag pictures onto the deck to make a button (or onto a button to give it that picture), and drag sound files on to add them to the soundboard with a button.
Drop programs and games: drag a program, a desktop shortcut or a Steam/Epic game shortcut onto the deck and it becomes a button that opens it, with the program's own icon. There's also a new Open a program or game step. For safety, programs can only be added on the streaming PC itself; phones can press those buttons but can't add or change what they open.
QR code for the DJ page. The Remote DJ section now has a QR code next to the DJ link, so you can open the DJ page on your own phone, already signed in.
0.9.9
Hyperwave Chat: fade messages out after a set time. Under Layout → Fade messages out after, pick seconds (5 to 120) or minutes (1 to 60), or turn on Never hide messages to keep them until newer ones push them out. Messages leave with your chosen Exit animation.
My Deck: longer waits. A wait step can now be anything from 0.1 seconds to 60 minutes, in seconds or minutes (it used to stop at 9.6 seconds). Great for "BRB scene → wait 5 minutes → back to Gameplay".
Long buttons run in the background. A button with more than a few seconds of waiting answers right away, glows while it runs, and stops if you press it again. Works the same from an Elgato Stream Deck.
0.9.8.3
Fixed: album art sometimes missing or wrong after skipping songs with Any player on this PC. Right after a skip, players like Spotify can still hand over the previous song's cover, or no usable cover, for a few seconds. Hyperwave now spots the old cover and waits for the new one, and starts the online cover lookup the moment the song changes, so the right art shows within a couple of seconds.
The online lookup is better at finding remastered and "feat." versions, and tries again if the first lookup fails.
0.9.8.2
Fixed: album art still missing with Any player on this PC (for example Spotify): Windows sometimes handed over cover data that wasn't a usable picture, so the overlay showed a broken image. Hyperwave now tries three ways of reading the cover, keeps only a real picture, and if the player's cover still can't be used, finds the album art online by song and artist.
Players that don't share a cover at all (some browser tabs) now get album art from the online lookup too.
0.9.8.1
Fixed: with Any player on this PC, the Now Playing overlay could show no album art (or the last song's art). Spotify and some other players send the picture a few seconds after the song title, and the overlay only looked once per song. It now picks up the cover as soon as it arrives.
Hyperwave keeps asking the player for the cover until it gets one, and tries a second way of reading it if the first fails. If a player still won't share its picture, the console window says why.
0.9.8
Music without Spotify Premium. Pick where your music comes from under the new Music section of the dashboard:
Any player on this PC (new, no setup): Spotify Free, Apple Music, YouTube or SoundCloud in a browser, TIDAL, Deezer, Amazon Music, foobar2000, MusicBee and most others. Now playing with album art and progress, plus play/pause, skip and back from the deck, chat commands and the DJ page. You can pin it to one player so a video in another tab doesn't take over.
YouTube Music app (new, free): full control, including volume, shuffle, repeat, search, Up next and real song requests that go straight into its queue in the order viewers asked.
Spotify Premium: works exactly as before, with playlists and devices.
Last.fm (new): shows whatever you scrobble from your phone, console, Plex or a record player app.
Request list for players that can't take requests directly. Requests are still checked against your rules (length, explicit, repeats, limits), then wait on a list on the dashboard, the deck and the DJ page. A Find button searches for each one in the player you're using, and Hyperwave ticks it off when it sees the song playing.
Requests can now be a YouTube link as well as a song name or Spotify link.
The deck, DJ page, chat commands and overlay only show the controls your music source can really do, and explain why when something isn't available.
The overlay hides its progress bar when the player doesn't share the song length.
Chat replies that mentioned Spotify now say "the music player" (only if you hadn't changed them).
New installs start on Any player on this PC. If you already use Spotify, nothing changes.
0.9.7
New: My Deck, your own stream deck that works without an Elgato. Design big buttons with a name, icon and color, and make one button do several things in order (switch scene, mute, post in chat, clip, music and more, with waits in between). Optional press-and-hold for risky buttons. Reorder and resize them. Your buttons sync across your PC, phone and tablet. Every button can also go on an Elgato Stream Deck key.
Phone sign-in is easier: the dashboard shows a QR code and a Copy link button that open the deck already signed in.
Pick your own deck passkey, or generate a random one.
What's new on the dashboard lists every update from 0.9.7 on, and a banner tells you when you've just updated.
Fixed: the deck page could lock you out within seconds on a phone. Its background checks were being counted as wrong passkeys.
The Twitch app instructions now say https://localhost for the redirect URL (Twitch rejects an empty extra box).
Clearer message when a music button is pressed before Spotify is connected.
0.9.6
New: Hyperwave Deck, a control panel for your stream at http://127.0.0.1:7575/deck. It works on your PC, a second monitor, or a phone or tablet on your Wi-Fi.
OBS: switch scenes, start and stop recording, go live and end the stream (press and hold), and mute or unmute your audio sources. The scene list follows OBS automatically.
Clips: one Clip button saves OBS's replay buffer to your PC and can also make a Twitch clip. Station can keep the replay buffer running for you.
Chat: Twitch, Kick, YouTube and TikTok chat in one feed, with emotes and name colors. Reply to one platform or all of them, with quick-reply buttons.
Music: play/pause, skip, back, and open or close song requests, with the current song and album art.
Two ways to reply and clip on Twitch: sign in to Twitch inside Station (no Streamer.bot needed), or send through Streamer.bot (also covers Kick and YouTube). Automatic picks whichever is set up.
Phones and tablets on your Wi-Fi can open the deck with a passkey. It refuses connections from outside your home network, and locks out repeated wrong guesses.
Elgato Stream Deck support: build a link for any deck button on the dashboard and paste it into Stream Deck's Website action with "GET request in background".
New OBS & Deck section on the dashboard with step-by-step setup, and a Deck link in the console.
0.9.5
One download for the whole package. Hyperwave Chat is now built into HyperwaveStation.exe at http://127.0.0.1:7575/chat, with its own Hyperwave Chat section on the dashboard. No more copying chat.html into the web folder.
Music in your chat. Hyperwave Chat can show each new song ("Now playing" with album art and who requested it), every song request, and optionally DJ actions. Turn it on under Connect → Hyperwave Station. It's on automatically when the chat is opened from the app.
The chat designer fills in your Twitch and Kick channel names from the dashboard the first time you open it, and links back to the dashboard.
Easier chat settings: tabs (Connect, Style, Motion, Position, Filters), a settings search, a Show all options switch, one-click style cards, undo and redo, per-setting reset, a connection check that confirms real chat is arriving, and a warning when your OBS link is out of date.
Chat placement and motion: drag and resize the chat anywhere on a full-screen canvas at 720p to 4K, ultrawide or vertical; 20 entrance and 8 exit animations; Matrix rain, float up, scrolling and pop-up modes; bubbles, palettes and profile pictures.
Dashboard: "Standalone chat" is renamed Commands without a bot so it isn't confused with Hyperwave Chat.
Version numbers for the app and chat are now shared (0.9.5).
New Hyperwave app icon (the TaiiRepublic glow ring with a hyperwave breaking through it) on the .exe, taskbar and every page: dashboard, chat designer, DJ deck and overlay designer, including browser tabs.
TaiiRepublic is now named in the app itself: right-click HyperwaveStation.exe → Properties → Details shows Company TaiiRepublic, product Hyperwave, version 0.9.5 and the copyright.
Official TaiiRepublic logo: the animated spinning logo in the dashboard's About section (it holds still for people who turn off animations in Windows), plus a Made by TaiiRepublic credit in the dashboard sidebar and the chat designer.
New console welcome screen: the TAii logo drawn in text, a note from Taii with Twitch, Kick and tip links (taken from the dashboard's About settings), a random message from the bridge each launch, and the Hyperwave Chat link alongside the others.
Fixed: the Spotify status flipping between "Connected" and "Connect Spotify". If the app's check with Spotify failed even once (a network hiccup, a rate limit, or Spotify refusing a request), the dashboard kept switching between the two every few seconds. It now stays on Connected and the top bar explains what Spotify is saying, with a fix for the common cases.
When logged in, the button now says Log in again instead of "Reconnect Spotify", which read like a status.
Renewed Spotify logins are saved immediately, and saving dashboard settings can no longer put back an outdated login.
If the app can't write its settings file, the dashboard now says so (otherwise you'd have to log in again after every restart).
0.9.1
The overlay designer preview opens at Actual size again, showing the overlay as big as it appears on stream. Switch to Whole screen (top of the preview) to see where it sits on your stream. Dragging works in both, and your choice is remembered.
0.9.0
Drag to place: the overlay designer now shows your whole stream screen. Drag the overlay anywhere, with snapping to edges and centre, step buttons for fine adjustment (1–50 px), arrow-key nudging, exact X/Y, and quick snap spots. Works at 720p, 1080p, 1440p, 4K and vertical canvases, and scales correctly to the OBS source size.
Cards placed in the bottom half stay pinned by their bottom edge, so they grow upward when a "requested by" line appears.
Visualizer: show a visualizer instead of (or over) the album art. Styles: Bars, Mirror, Wave, Radial, LED meter, Orb. Colour, bar count and speed options.
New layout: Player, a desktop media-player window with a title bar, display screen and buttons.
6 new starting looks: Retro desktop player, Synthwave, Arcade, Pastel pop, Sci-fi HUD, Monochrome.
Older overlay links will move to the new drag placement. Re-copy your OBS link after placing it.
0.8.2
First tester build: Now Playing overlay, song requests (Twitch, Kick, YouTube, TikTok), Remote DJ with passkey and fixed link, About section with feedback and tip links.
