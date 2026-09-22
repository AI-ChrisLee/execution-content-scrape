# The thumbnails

3 thumbnails, 1 per title. Each copies the layout of its source row's thumbnail, with the founder's real face and the founder's words. The base image comes from Higgsfield. Every word, badge and arrow is added in code afterwards.

## Higgsfield, the check

Run `higgsfield account status`. It prints the plan and the credits.

- **Command not found:** run `npm i -g @higgsfield/cli`, then check again. It fails on permissions: run `npm i -g --prefix ~/.npm-global @higgsfield/cli`, and call `~/.npm-global/bin/higgsfield` from then on. No npm: "Install Node from nodejs.org, then say go." Wait.
- **No `python3`:** "Install Python from python.org, then say go." Wait. On a Mac, the first `python3` can open Apple's installer for its developer tools: "Press Install, then say go." Wait.
- **Not signed in:** run `higgsfield auth login`. It opens a sign-in page; the founder signs in with their Higgsfield account. Check again.
- **No paid plan, or 0 credits:** the titles message ends "Higgsfield needs a paid plan to make images from Claude Code. Say yes to save your titles; the thumbnails wait." On yes, write `titles.md` and the title-only package (`the-package.md`), and stop. The next "Run the Winning Scrape." starts at this check.

Credits through the CLI are charged at standard rates. An unlimited plan does not cover them.

## The face photos

`squad/face/`, 2 to 4 clear photos of the founder alone, chest up, looking at the camera. Empty or missing: create the folder, and the titles message asks "Drop 2 to 4 photos of your face in squad/face/ before you say yes. A yes with no photos saves your titles; the thumbnails wait." No photos, no thumbnails: the yes writes the title-only package. The photos go up to Higgsfield after the yes, and the titles message says so.

## The installs, first time only

The first time in a folder, said in 1 line in the titles message, and run by the agent on the first yes with photos, before the upload:

    python3 -m venv .venv && .venv/bin/pip install pillow
    mkdir -p squad/fonts && curl -sL -o squad/fonts/Inter.ttf 'https://github.com/google/fonts/raw/main/ofl/inter/Inter%5Bopsz,wght%5D.ttf'

Every compositing script runs with `.venv/bin/python`.

## The base, 1 per pair

1. Upload each face photo, after the yes: `higgsfield upload create squad/face/<photo> --json`. Keep the ids for this run.
2. Write the prompt, 30 to 100 words:
   - The person from the reference photos, chest up, 40 to 55% of the frame height, looking into the camera, the face the title wants (serious, smiling, surprised).
   - The layout of the source row's thumbnail, in % of the frame: where the person sits, where the words go, what else is there. The pick's layout is in the winner file; for the other 2, open their jpg in `src/` and read it the same way. Layout and size only, never that thumbnail's person, brand or topic. A source with 2 or more people: the founder alone, in the place and size of the largest face.
   - Every object named from the founder's own topic (THE SENTENCE).
   - The areas for words, badges and screens left empty and flat.
   - A bright, clean, flat background. No glow.
   - Last line: "No words, no letters, no numbers, no logos anywhere."
3. Make it:

       higgsfield generate create nano_banana_2 --aspect_ratio 16:9 --image <face id> --image <face id> --prompt "<prompt>" --wait

4. It prints the result URL. Download it: `curl -sL -o squad/week/thumbs/<date>/pair-N-base.png '<url>'`. The file on disk is the record.
5. After the 3 bases: `higgsfield account status` again, and "Used <n> credits. <m> left."

## The type layer, in Pillow

- **Words:** 2 to 6, cloned from the source thumbnail's words the way the title was: same shape, 1 or 2 words turned.
- **Font:** `squad/fonts/Inter.ttf`, then `font.set_variation_by_name("Black")`. Check the words render Black, not Regular.
- **Size:** the main line 14 to 28% of the frame height (100 to 200px on a 720px frame). Under 100px fails on a phone.
- **Sharpness:** draw on 2560x1440, then shrink to 1280x720.
- **Color:** 1 accent. The `accent color` row in `.claude/squad-roots.md`, else the source thumbnail's own accent. Red only for a no. Everything else black or white.
- **Shapes:** badges, boxes and arrows drawn in code, straight and crisp.
- **Proof:** a screen, a dashboard or a result in the frame is a real file the founder has, pasted in. No real file: leave it out. Never generated.
- **Save:** `squad/week/thumbs/<date>/pair-N.jpg`, 1280x720, under 2 MB.

## What wins at phone size

Measured across 30 winning thumbnails:

1. Nothing small. The largest thing that is not the face takes 30 to 55% of the frame.
2. The face is big, 40 to 55% of the frame height, eyes on the viewer.
3. 2 to 6 words. The number is the headline.
4. 1 accent color with 1 meaning.
5. A real screen blown up big reads as proof. A painted scene reads as fake.

## The review sheet

`squad/week/thumbs/<date>/review-sheet.html`, 1 row per pair: the new thumbnail at 320px wide with its title under it, the source thumbnail at 320px beside it.

Before showing it, read every pair at 320px. Weak: fix the size first, then the contrast, then the words. A face that does not match the photos goes on the sheet as a fix to make.

Open it: `open <path>` on macOS, `start <path>` on Windows, `xdg-open <path>` on Linux.

## The fixes

- Change only what the founder names. A note about 1 pair never touches another.
- Words, sizes, colors and arrows are the type layer. No credits.
- A new base is made, and its credits printed in 1 line.
- Write the sheet again after every fix. Repeat until "lock".
