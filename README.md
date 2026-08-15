# Family Chat

Chat for the computers in your house — without the internet.

One Python file is the entire application: server, web page, everything. Run it on
one computer, and every other device on the same Wi-Fi opens a browser bookmark,
picks a name, and chats. No accounts, no installs on the other machines, no cloud,
no data leaving your network.

Built for a family that wanted the kids to message each other (and their parents)
at home and in the car, on computers that deliberately have no internet access.

## What it does

- Buddy list showing who's on the chat right now
- Private messages, or one message to several people at once (checkboxes)
- Popup, sound, and flashing tab title when a message arrives
- Messages sent to someone who's offline are held and delivered when they return
- Each device remembers its person after the first visit
- All messages append to a plain-text log next to the server file, so a parent
  can review them — it's your machine, your rules

## Running it

**Requirements:** Python 3 on the one host computer. Nothing anywhere else.

- **Mac host:** double-click `FamilyChat.command`
  (first time only: control-click → Open → Open)
- **Windows host:** install Python once from the Microsoft Store, then
  double-click `BrotherChat.py`. When the firewall asks, allow on **Private networks**.

The terminal window prints the address for everyone's bookmark, e.g.
`http://your-computer.local:8080` (with a numeric fallback). Other devices browse
there — type it with the `http://` so the browser doesn't treat it as a search.
Keep the window open; closing it stops the chat.

The two files are the same app with different names and separate logs — run one,
or run both on different machines as independent chats.

## No internet required — by design

The chat works on any network the devices share, even one with no internet
behind it:

- A home router with the kids' internet access paused still passes local traffic
- An Android phone's hotspot with mobile data turned off works as a portable
  dead network for the car (Android may require enabling airplane mode first)
- A Mac can broadcast its own no-internet network via Internet Sharing from an
  unused port (e.g. Thunderbolt Bridge)

**Known limitation:** an iPhone hotspot with live cellular data on certain
carriers hands every device a placeholder address (`192.0.0.x`) inside its own
tunnel — devices can't reach each other, so chat won't work there. Use one of
the options above instead. Public Wi-Fi (airports, restaurants) usually blocks
device-to-device traffic too.

## Notes

- The buddy list shows people who have the page open, not every device that exists
- The host's numeric address changes between networks; the `.local` name usually
  doesn't — bookmark that where it works
- `chat_log.txt` and `*_pending.json` contain real conversations; they're
  gitignored on purpose. Don't commit them.
