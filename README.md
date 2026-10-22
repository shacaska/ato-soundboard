# ATO Soundboard

A shared soundboard for Aeon Trespass: Odyssey sessions. Tap big pads to play sound effects and ambience at the table. Anyone you add as a collaborator can add sounds from their own device, and they appear on everyone's board the next time it syncs.

**Open it:** https://shacaska.github.io/ato-soundboard/

## Install on an iPad

1. Open the link above in **Safari**.
2. Tap the Share button, then **Add to Home Screen**.
3. Open it from the new icon. It runs full screen, and once the board has downloaded it works offline.

Install first, then connect your GitHub key inside the installed app. The home screen app keeps its own storage, separate from Safari.

## Who can change the board

Anyone with the link can open the app and play the sounds. Only the repo owner and collaborators can add, edit or delete them.

**To let a friend add sounds:**

1. On GitHub, open this repo's **Settings → Collaborators** and add their GitHub username. They accept the invite from their email or GitHub notifications.
2. They open the app, go to **Settings → Adding and editing sounds**, and tap **Create a key on GitHub**. That opens GitHub's "new token" page with the right box (`public_repo`) already ticked. They choose an expiry, create the token, copy it and paste it into the app.

The key is saved only on the device where it was pasted. When it expires, the app says so; make a new one and paste it in. Nothing unsaved is lost.

## Adding sounds

- **Add sounds** takes audio files (MP3, M4A, WAV, AIFF, FLAC) and videos (MOV, MP4, M4V, WebM) from Files or Photos. For a video, only its sound is kept, saved as a WAV file; the video itself isn't uploaded. If the iPad can't read a video's sound directly, the app plays the video once with the volume off to capture it, which takes as long as the clip (videos up to 3 minutes).
- **Record** uses the microphone, up to 2 minutes per take. Quiet bits at the start and end are trimmed off automatically, and you can adjust that afterwards in Edit.
- **Combine sounds** (in Edit mode, or "Combine with others" when editing a pad) splices pads one after another, with a gap or an overlap between them, or layers them so they play together. Drag a sound along the timeline to change when it starts, trim it by dragging its edges, set its volume and fade in or out, preview, then save the result as a new pad. The pads you combined stay as they were. A combined pad remembers how it was made, so "Change the combination" reopens it for tweaking.
- Only add videos and audio you made yourself or are allowed to use. The repo is public, so everything on the board can be downloaded by anyone who finds it.

## How it works

- `main` branch: the app (`index.html`, the offline worker, icons). GitHub Pages serves this.
- `board` branch: `board.json` (every pad's name, group, colour, trim and settings) and `sounds/` (the original audio files).
- Every change made in the app is a commit to the `board` branch with a message like *Add “Thunder” (by shacaska)*, so the full history is on GitHub and anything can be restored.
- Trims, fades and splits only change `board.json`. The original audio file is never altered.
- If two people save at the same moment, the app re-reads the newest board and applies its change on top, so neither edit is lost.
- Each device keeps a copy of every sound for offline play. Pressing Sync (or opening the app) fetches new pads and sounds.

## Limits

- Files up to 25 MB and 10 minutes each. MP3, M4A, WAV, AIFF and FLAC work best on iPad. Sound taken from videos and recordings is stored as WAV, which is bigger than MP3; a long clip is saved in mono or at a lower quality so it fits.
- GitHub Pages sites are capped at 1 GB, which is plenty for sound effects but would fill up with lots of long music tracks.
- The repo is public, so anyone who finds it can download the sounds. Avoid uploading anything you wouldn't want public.
- Without a key, a device can sync about 60 times an hour per network (GitHub's limit for anonymous requests). The app syncs every 5 minutes without a key and every minute with one.
