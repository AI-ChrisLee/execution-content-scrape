---
name: the-winning-scrape
description: Use this when the founder needs this week's video picked and packaged, when they type "/the-winning-scrape" or say "Run the Winning Scrape.", then "Take the pick." (or "Take row N."), "yes" to the titles, "lock" on the review sheet, and later "Pair N won." after YouTube's A/B Testing. It finds the newest videos in the buyer's topic that beat their own channel's usual views, digs out the pick (transcript, thumbnail, top 100 comments), clones 3 titles from winning rows, builds 3 thumbnails with the founder's real face through the Higgsfield CLI, and writes squad/week/<date>-package.md. It never uploads, posts or touches YouTube.
---

# The Winning Scrape

1 output: `squad/week/<date>-package.md`, 3 locked title and thumbnail pairs, with the winner file `squad/week/<date>-winner.md` behind it.

**The first message of a fresh run** (no week in progress) carries this line, word for word:

> This agent is a base. Once you have done it your way, tell your squad "update the agent to do it like this."

Open the 4 files in `references/` first: `the-hunt.md`, `the-winner-file.md`, `the-thumbnails.md`, `the-package.md`. Missing: say the agent folder came without its `references/`, and stop.

## The lines the founder types

| The founder says | What runs |
|---|---|
| "Run the Winning Scrape." | the table below picks the step |
| "Take the pick." or "Take row N." | 4, then 5 |
| any swapped title word, then "yes" | 5.5, then 6 (no face photos or no paid plan: 5.5, then stop) |
| a fix, or "lock" | 7, then 8 on lock |
| "Pair N won." | 9, then stop |

## Where a run starts

Read the newest week folder `squad/week/thumbs/<date>/`. Files decide, never what a session remembers.

| On disk | Start at |
|---|---|
| no week folder, or the newest `squad/week/<date>-package.md` reads `locked`, or reads `title-only` and is 7 or more days old | 1, a new week dated today |
| a `title-only` package under 7 days old, `squad/face/` empty | say "Drop 2 to 4 photos of your face in squad/face/, then say Run the Winning Scrape." and stop |
| a week folder with no `src/rows.md` | 1, in that folder |
| `src/rows.md`, no `squad/week/<date>-winner.md` | 3, the table and the stop again |
| the winner file, no `titles.md` | 5 |
| `titles.md`, a `pair-N-base.png` missing | 5.2 and 5.3 (the check, the cost line), then 6 on yes, only the missing bases |
| all 3 bases, a `pair-N.jpg` missing | 6, the type layer only |
| all 3 `pair-N.jpg`, no package file | 7 |

## Never

- Never uploads, posts, publishes or schedules. Never touches YouTube.
- Never invents a row, a number, a quote, a comment or a thumbnail read. A row without a link does not exist. A search snippet is not a number.
- Never generates a face, a screen, a number or a word inside an image. Faces come only from `squad/face/`. Words are composited in code.
- Never spends a Higgsfield credit before the cost line and the founder's yes.
- Never forces a pick. A forced pick is worse than an honest miss.

## 1. Read

- `squad/business.md`: THE SENTENCE, WHO line 1, THE PROBLEM, BUYER WORDS. The offer comes from this page and nothing else.
- `squad/lane.md`: channels, buyer messages, searches, your own winners.
- `.claude/squad-roots.md`: the `accent color` row, when there is one.

## 2. The ask

1 numbered message, only the questions the files do not answer:

1. Name 2 or 3 YouTube channels your buyers watch. Your buyers are the people you want to pay you, even if nobody has yet.
2. Paste 3 to 5 real messages from buyers. None yet? Say "none", and the top comments on the winning video stand in.
3. Only when `squad/business.md` is missing: What do you sell, and who buys it, in 1 line?

Write the answers into `squad/lane.md` (template in `the-package.md`). A later week with channels on file asks nothing: 1 line, "Channels: <names>.", and the hunt starts. Channels or messages typed with the trigger replace the ones on file.

## 3. The hunt, the table, the stop

Detail: `references/the-hunt.md`.

1. yt-dlp: check it. Missing: install it with the 1 line for this computer and say "yt-dlp was missing, so I installed it in this folder."
2. At least 6 searches in the buyer's words, keyless: the results page, then each watch page, then oembed for the channel.
3. Keep long videos (over 4 minutes) from the last 60 days. Under 8 verified rows: 90 days, said in 1 line.
4. Usual views per channel off its yt-dlp upload list, RSS only as a second try. The 2026-08-24 rule: the uploads after that date when there are 8 or more, else the row's note says `usual spans 8/24` and the row stays.
5. Score = views divided by the channel's usual. Rank. Print the table, every row a link and a score, the top 5 (and the pick, when it sits below row 5) with a 1-line summary each, then the pick and why in 2 lines. Save it all to `squad/week/thumbs/<date>/src/rows.md`.
6. Stop: "Type Take the pick., or Take row N."

Nothing at 1x or over after 1 widen: "No winner yet. Nothing beat its own channel this week." Print the table and stop.

## 4. The winner file

Detail: `references/the-winner-file.md`. 1 yt-dlp pull, then `squad/week/<date>-winner.md` in 5 parts: the video and its numbers with its 1-line summary · the full transcript · the thumbnail read off the downloaded image · the top 100 comments by likes, verbatim · the angle, 2 sentences on what its audience asked for and never got.

Print the path and the angle. No buyer messages: 1 line, "No buyer messages yet, so the top comments stand in.", or, with fewer than 3 viewer comments, "No buyer messages yet, and this video has almost no comments, so the angle comes from its transcript." Go straight on to 5.

## 5. The titles, and the 1 yes

Detail: `references/the-package.md` (titles) and `references/the-thumbnails.md` (the check and the cost).

1. 3 titles, each cloned from a verified row in `rows.md`: keep the shape, turn 1 or 2 of its words into up to 3 of the buyer's words. The main clones the pick. From week 2, when `squad/lane.md` has a row under `## Your own winners`, the newest one's shape takes the main and the pick moves to title 2. Every title links its source. Every number carries its receipt, a line on `squad/business.md` or a count the pick's transcript already holds, or it goes.
2. Run `higgsfield account status` and `python3 --version`. Higgsfield not installed, no Node, no Python, or not signed in: the fix in `the-thumbnails.md`, then run them again. No paid plan, or 0 credits: send the titles message with no cost line, ending "Higgsfield needs a paid plan to make images from Claude Code. Say yes to save your titles; the thumbnails wait." On yes, 5.5.
3. `higgsfield generate cost` for 1 base, times 3.
4. 1 message: the 3 titles with source, words turned and receipt · "3 thumbnails cost <n> credits. You have <m>." · "Your face photos go up to Higgsfield to make them." · `squad/face/` empty: "Drop 2 to 4 photos of your face in squad/face/ before you say yes. A yes with no photos saves your titles and spends nothing." · first time here: "Your first yes with photos also installs Pillow and the Inter font in this folder." · photos in `squad/face/`: "Swap any word that isn't yours, then say yes. That 1 yes saves your titles and spends the credits." · `squad/face/` empty: "Swap any word that isn't yours, then say yes."
5. On yes: the founder's words win over the shape. Write `squad/week/thumbs/<date>/titles.md`. `squad/face/` still empty, or no paid plan (5.2): spend nothing, write the title-only package (`references/the-package.md`), create the episode folder, and print: "Your titles are saved. The script can start now: Write the money script. The thumbnails wait for your face photos in squad/face/ and a paid Higgsfield plan. Then say: Run the Winning Scrape." Stop.

## 6. The thumbnails

Detail: `references/the-thumbnails.md`.

0. First time in this folder: run the 2 install lines in `the-thumbnails.md`.
1. Upload each face photo: `higgsfield upload create squad/face/<photo> --json`.
2. 1 base per pair: `higgsfield generate create nano_banana_2 --aspect_ratio 16:9 --image <face ids> --prompt "<prompt>" --wait`. The layout copies the source row's thumbnail, described in words. No words anywhere in the image.
3. Download each result to `squad/week/thumbs/<date>/pair-N-base.png`.
4. Type layer in Pillow: the words, badges and arrows composited, Inter Black. Any screen or number shown is a real file the founder has, or it is left out.
5. Save `pair-N.jpg`, 1280x720. Print "Used <n> credits. <m> left."

## 7. The review sheet, the fixes, the lock

1. Write `squad/week/thumbs/<date>/review-sheet.html`: each pair at 320px wide with its title, the source thumbnail beside it. Read it at that size first, fix what is weak. Open it for the founder.
2. "Tell me what's wrong, or say lock."
3. A fix changes only what the founder names. A new base prints its credits in 1 line and waits for yes.
4. Repeat until "lock".

## 8. The package file

Detail and template: `references/the-package.md`.

Write `squad/week/<date>-package.md`: the 2 join lines first (`episode: squad/episodes/epNN/`, `source winner: <date>-winner.md`), the 3 pairs, the A/B test line. Create the episode folder. Print the path, the main title, and `Next: "Write the money script."` Done.

## 9. Pair N won.

The newest package file with no `won:` line. Add `won: pair N · <date>` under its join lines. Append 1 row under `## Your own winners` in `squad/lane.md`: date, the winning title, its shape with the turned words in [brackets], the source link, the thumbnail path. Print the row, naming the video so the founder can correct it. Stop. Next week's main title starts from that shape.
