---
name: the-winning-scrape
description: Use this when the founder says "Run the Winning Scrape.", every week, to decide the video. It hunts the last 60 to 90 days, ranks every candidate against what its own channel usually gets, then picks ONE winner and digs it out completely (transcript, thumbnail, comments). First run also sets the lane: the niche and the search vocabulary every later run reuses.
---

# The Winning Scrape

One purpose: pick this week's video off other people's numbers and dig it out. One
output: `squad/week/YYYY-MM-DD-winner.md`, the file the Proven Package (c2) packages and
the Money Driven Script (c3) writes from.

Say this line once, in the first message of a fresh run:

> This skill is a base. Once you have done it your way, tell your squad "update the skill to do it like this."

Read `.claude/squad-roots.md` first, the per-repo instance file every member-run skill
shares. Its values win over the `squad/` paths below, which are worked examples; the lane
above all. Fill any field this run learns, and never re-ask one it answers. A repo
carrying the legacy `.claude/spine-roots.md` keeps working: read that when no
squad-roots.md exists.

## What this never does

Never invents an angle, a shape or a number. Never sends, never posts, never uploads,
never publishes, never schedules. Never describes a thumbnail it did not view, never
fabricates a search it could not run, never presents a substitute as the real thing. Real
numbers only: a row without a link does not exist, anything not recorded prints
`not recorded`, and search snippets never count as verification. A declined permission is
stated plainly in the output as a gap in the data, never silently worked around. A forced
pick is worse than an honest miss.

## The first message

Read `squad/business.md`, `squad/lane.md`, `squad/offer-research.md` and
`squad/credibility-bank.md` first, and never ask what they answer. Then ask one thing:

1. Name 2 or 3 YouTube channels your buyers watch.

Never ask whether they already have an idea. The numbers pick.

Ask what you sell and who buys it only when `squad/business.md` is missing. Where
`squad/offer-research.md` mined channel names, play those back and ask only whether to
add or drop any; its quotes and its `## BUYER LANGUAGE` section count as pasted buyer
language, its `## CHANNEL BASELINES` as numbers to re-verify.

In the same message: ask for 3 to 5 real buyer replies, DMs or comments, because real
buyer language outranks everything you find; say in one line that the run will ask to
allow web search, page fetches, shell commands and one transcript tool install, each
allowed once; and from week 2, put last week's published row and the latest `## Sundays`
row of `squad/content-log.md` above question 1, with the shape it cloned, the layer it
was recorded on (that episode's `00_PREP.md`) and how many times the founder's OWN usual
views it did. No log file or no published row yet: skip it silently. A proven winner of
your own outranks a fresh hunt.

First run only (no `squad/lane.md` yet): name the lane too, the niche in one line plus
the search vocabulary, after reading the offer document's SWITCHING ITCH and ANSWER lines
and the research file's direction call. Its week-one attack weights the pick and rides
into the winner file.

## The hunt

Search at least 6 ways, last 60-90 days only. Later runs use the vocabulary saved in
`squad/lane.md`. First run: derive the 6 or more queries from the answers, seeded by the
buyer channels, at least half naming the BUYER's problem in the buyer's words, not the
service category.

For every promising video: title, channel, subscribers, views, age, URL. Identify
channels by searching and confirming, never by guessing a handle.

The zero-quota toolkit IS the primary path. The numbers live in JSON embedded in the raw HTML (`ytInitialData`
/ `ytInitialPlayerResponse`); a plain markdown fetch strips them, so raw curl is the
method, curl the page and grep the field. A markdown-fetch miss is a tooling miss, never
evidence the niche is thin.

- Candidates: curl `youtube.com/results?search_query=<the+query>`, grep `videoRenderer`
  for video ids, then date-verify each row on its watch page. Web search supplements it;
  it cannot filter by upload date.
- Channel identity: `youtube.com/oembed?url=<video-url>&format=json`.
- Channel id from a handle: curl the channel page, grep `"channelId":"UC`.
- What a channel usually gets: `youtube.com/feeds/videos.xml?channel_id=UC...`, the last
  ~15 uploads with per-video view counts.
- Views, date, duration on one video: curl the watch page, grep `viewCount`,
  `publishDate`, `lengthSeconds`.
- Subscribers: the channel about page, grep `subscriberCountText`.
- Likes (the bought-reach test): the watch page again, grep `likeCount`.
- Thumbnails: download `i.ytimg.com/vi/<id>/hqdefault.jpg` into
  `squad/week/thumbs/<winner-date>/src/` (this run's date, the date the winner file
  carries), then Read the local file.
- The transcript: `yt-dlp`, installed once at the winner file.

Empty greps on EVERY page mean a consent or bot wall (common outside North America),
never a thin niche: retry with a `CONSENT=YES+1` cookie header, and say so plainly if it
persists. Keyless public pages are the path, and the run never needs a paid tool.

## The ranking

One number:

    breakout = views divided by that channel's usual views
    (usual views = the median of that channel's last 10-20 comparable long-form uploads)

To the founder a breakout is said as "N times what that channel usually gets", in those
words.

Long-form means over 4 minutes. A one-minute vertical upload YouTube does not call a
Short still drags a median far enough down to turn a loser into next week's winner: on
the author's own channel the unfiltered median reads 1,007.5 against a true 2,207.5. So
on **the founder's OWN channel, verify every upload's real duration on the watch page**,
once per run, before anything is ranked; it is the number every breakout divides by.
**A competitor's channel keeps the priced rule**: no duration filter, the median marked approximate, real durations verified
only for the top 3 candidates' channels.

**No usual number, no row.** Under 8 comparable long-form uploads, a window straddling
2026-08-24 (the day YouTube began counting a view from the first frame, so a median across
it mixes 2 definitions of the word), stats unpullable, zeroed counts, or a broken uploads
list: print `no usual number` and drop the row. There is no second number to rank it on.

Discard below 0.5x, and discard bought reach: a spike with almost no likes or comments
relative to its views, or a video running as an ad, is not a winner; drop it and say why.
Keep the top 8 to 12, sizes noted, links attached.

Nothing clears 1x = no winner yet: say so and widen one notch, the single widen this run
gets. A notch is one step up the specificity ladder, the buyer's wider job or the parent
category of the problem, in the buyer's own words, same 60-90 day window, same vocabulary
discipline, never a jump to a different market (bookkeeping for dental practices widens
to running a dental practice's money, not to bookkeeping for small businesses). Still
under 1x: carry the best row forward flagged as a CONTENT FIT pick running under what its
channel usually gets, and the founder decides with the number in view.

## The shape

Name what repeats across the survivors: topic angle, title shape, promise. 3 videos at 2x
sharing one shape beat 1 lucky 10x. Write each winning title shape as a skeleton with
slots, next to the linked video that proved it, the niche it proved in, how many times
its channel's usual views it did, the usual number it was measured against, and today's
date as the date measured. The Proven Package ranks shapes on those written numbers
instead of recomputing them.

## The pick

Pick ONE winner, the best intersection of breakout, shape and the founder's business.
Present the pick, the 3 to 5 runner-ups one line each and why, plus the top 8 to 12 as a
table with a number and a link on every row. Then stop: the founder takes the pick, or
names the runner-up they want and why, in plain words.

## The winner file

Build ONE file, `squad/week/YYYY-MM-DD-winner.md`, 5 parts in this order:

1. **The winner**: title, channel, numbers, URL.
2. **The transcript**, pulled in full. Install the tool once here, on the allow the first
   message named. One line per OS, no package manager, the binary in the repo root:
   `curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos -o yt-dlp && chmod +x yt-dlp`
   on macOS, the same with `.../yt-dlp` on Linux, the same with `.../yt-dlp.exe` on
   Windows. The watch page alone returns no captions on a fresh keyless install.
3. **The thumbnail, described**: exactly what text it carries and what it shows, from the
   downloaded file the run actually Read, never from the title or the numbers. Download
   failed = the THUMBNAIL UNREACHABLE label, never a guess.
4. **The comments**: top questions, complaints and "you never showed X" moments, verbatim
   with like counts, capped to the top 100 by likes. Uncapped, a popular winner pulls for
   silent minutes and reads as a broken run. The exact command, so every session behaves
   the same: `yt-dlp --write-comments --extractor-args
   "youtube:comment_sort=top;max_comments=100,all" <url>`
5. **The angle**: what we add or fix, 2 sentences, at the bottom of the file. The offer
   document's week-one attack line goes here too; c2 and c3 read this file, not the offer
   document.

Keep the top 8 to 12 ranked survivors' jpgs in
`squad/week/thumbs/<winner-date>/src/`, the winner's among them, delete only the unranked
rest, and say in the winner file how many survivor jpgs the folder holds; those jpgs are
what the Proven Package distills this lane's thumbnail cages from. First run: write
`squad/lane.md` too.

One gate, the last thing in the run: the founder changes any word in a title that does
not sound like them, then says yes. Close in one line: c2 packages this file, c3 writes
from it.

## The outputs

`squad/week/YYYY-MM-DD-winner.md` every run, `squad/lane.md` on the first run, and the
survivor jpgs it keeps. The lane file holds still between runs and refreshes at a season
boundary or when the shape shifts; the Proven Package appends its own rows under a
`## Your own winners` heading in the same file. The template:

    # THE LANE
    <the niche, one line>

    ## SEARCH VOCABULARY
    <the 6+ queries that found winners>

    ## SHAPE TEMPLATES
    <one block per shape: the full skeleton text with slots, the niche that proved it,
    the link to the proving video, how many times its channel's usual views it did, the
    usual number it was measured against, and the date measured (worked example: 4.1x
    the channel's usual 38,000 views, measured 2026-08-26). A multiple with no skeleton
    is not a shape.>

## Edge rules

- **What the usual number excludes**: the candidate video itself, confirmed bought-reach
  spikes, and anything not comparable (long-form with long-form, same topic). Those
  uploads may be older than 90 days; only the WINNER pick must be recent.
- **Shorts never get ranked**, being cuts OF the long-form made later, and their low
  engagement breaks the bought-reach test. Keyless test: `youtube.com/shorts/<id>`
  returns the short directly and redirects to `/watch` for long-form.
- **Channel identity needs a topical check**: read a sample of actual content, not just
  the name. A right-named channel can belong to a different industry.
- **Unreachable, never substituted silently.** No transcript (the tool failed, or no
  captions): the description plus its on-screen text, labeled description-not-transcript.
  No comments (the `--write-comments` pull failed; tooling, not scarcity): the visible
  total count if a surface shows it, plus the transcript's sharpest lines, labeled
  transcript-not-comments. No thumbnail: the THUMBNAIL UNREACHABLE label. Say the
  failure, and mark every substitution for a re-pull before the Package finalizes.
- **Comment-poor winner** (quiet B2B niches): every comment verbatim, the shortfall
  stated as a finding. Near-zero comments is data, not failure.
- **Non-English winner**: the full transcript plus a condensed English pass, saying which
  parts are translation.
- **Season refresh**: the founder says so at a season boundary. The first-run hunt reruns
  on fresh data and `squad/lane.md` is rewritten. Between seasons the lane holds still.

## Rules

- Every message to the founder is scannable: a short header, then bullets or a table. The
  ranked candidates and the shape templates go in TABLES; findings go in short bullets
  with the key number in bold. Never a wall of paragraphs.
- Unverifiable rows get dropped. Every row carries its URL.
- Buyer language wins ties: an angle answering a real pasted reply beats a higher
  breakout that answers none.
- Clone the shape, never the words. The one-variable swap IS the difference.
- Weekly, and the hunt is always fresh.
