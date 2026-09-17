# The hunt

Keyless. Public YouTube pages and yt-dlp. No API key, no paid tool, no account.

## yt-dlp

Check `yt-dlp --version`, then `./yt-dlp --version`. Neither works: install it in the founder's folder with the 1 line for this computer, then say "yt-dlp was missing, so I installed it in this folder." Call it `./yt-dlp` from then on.

- macOS: `curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp_macos -o yt-dlp && chmod +x yt-dlp`
- Linux: `curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o yt-dlp && chmod +x yt-dlp`
- Windows: `curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe -o yt-dlp.exe`

## The searches

- At least 6, in the words the buyer uses, never the category name of what the founder sells. Build them off THE SENTENCE, WHO line 1, THE PROBLEM, BUYER WORDS and the buyer messages in `squad/lane.md`. At least half name the buyer's problem the way the buyer says it.
- Later weeks: the searches in `squad/lane.md` that found rows, plus 2 new ones.
- The channels the founder named count too: their own long uploads from the window are candidates.
- Every search goes into `## Searches` in `squad/lane.md`: the date, the words, how many verified rows it found.

## The commands

Every curl carries a browser user agent:

    UA='Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0 Safari/537.36'

| Need | Command | What to read |
|---|---|---|
| Candidates, each search run 2 times | `curl -sL -A "$UA" -H 'Accept-Language: en-US' 'https://www.youtube.com/results?search_query=<words+joined+by+plus>&sp=EgIIBA%3D%3D'` (upload date: this month), then the same with `&sp=EgIIBQ%3D%3D` (this year) | `grep -o '"videoRenderer":{"videoId":"[^"]*"'` |
| 1 video's numbers | `curl -sL -A "$UA" 'https://www.youtube.com/watch?v=<id>'` | the first `"viewCount":"`, `"publishDate":"`, `"lengthSeconds":"`, `"channelId":"`, `"likeCount":"`, `"title":"`, `"shortDescription":"` |
| The channel's name | `curl -s 'https://www.youtube.com/oembed?url=https://www.youtube.com/watch?v=<id>&format=json'` | `author_name`, `author_url` |
| A channel id from a handle | `curl -sL -A "$UA" 'https://www.youtube.com/@<handle>'` | `"externalId":"UC...` |
| What a channel usually gets | `yt-dlp --flat-playlist --extractor-args "youtubetab:approximate_date" --print "%(id)s %(view_count)s %(duration)s %(upload_date)s %(title)s" --playlist-end 40 'https://www.youtube.com/channel/<id>/videos'` | 1 line per upload: id, views, seconds, date, title |
| Second try, when that list fails | `curl -sL -A "$UA" 'https://www.youtube.com/feeds/videos.xml?channel_id=<id>'` | `<yt:videoId>`, `<media:statistics views=`, `<published>`; each length off its watch page |
| A row's thumbnail | `curl -sfL -o squad/week/thumbs/<date>/src/<id>.jpg 'https://i.ytimg.com/vi/<id>/maxresdefault.jpg'` | fails: the same with `hqdefault.jpg` |

The sp filter only narrows the page. The window is still decided off each watch page's publishDate.

Empty greps on every page mean a consent or bot wall, never a thin topic. Retry with `-H 'Cookie: CONSENT=YES+1'`. An HTTP 429, or "Sign in to confirm you're not a bot" from curl or yt-dlp, means YouTube is slowing this computer down: say "YouTube is slowing down this computer. I'm waiting 10 minutes, then trying once more.", wait 10 minutes, and retry once. Still blocked: say so plainly and stop. The next "Run the Winning Scrape." starts where the files stop. Fetch watch pages 1 at a time, never in parallel.

## A verified row

A row counts only when its own watch page gave the views, the publish date and the length, and its channel has a usual number.

- **Window:** published in the last 60 days. Under 8 verified rows: 90 days, said in 1 line.
- **Long only:** over 4 minutes (240 seconds). Shorts are never ranked.
- **Dropped, each with its reason in 1 line:** bought reach (views far above what the likes and comments show, against the likes off the watch pages of its 3 uploads before it, or the video runs as an ad; a row with 1,000 views or more and fewer than 1 like per 500 views is bought reach even when its 3 uploads before it look the same, because a channel that pays for every upload paid for those too), a score under 0.5, a channel with no usual number. A watch page with no likeCount (likes hidden): the 1 like per 500 views line does not apply; the check against its 3 uploads before it still does.
- **The channel is the right one:** its own recent titles talk to the buyer on WHO line 1 (the owner or the staff of that business), not to that business's customers, another trade or a general audience. Checked off the titles in its usual-views list (the same pull), never its name. Every channel in the table and the pick's is checked. Dropped as `wrong channel: its recent uploads are <topic>`.
- **Enough views to mean something:** a video under 7 days old is listed with the note too new, never ranked, and only after the same channel check. When none of the 12 table rows has 1,000 views or more, widen once (the No winner yet step). After that, whenever the pick itself has under 1,000 views, its 2 lines add "Your buyers' channels are small. This pick rests on <n> views, so treat it as a lead, not a vote."

## Usual views

1 list pull per channel (the command above), then:

1. Keep uploads over 4 minutes. Leave out the video being scored and anything under 7 days old, because its views are still climbing.
2. The list comes newest first. Its dates are rounded: 5 weeks old or newer to the week, older to the month, and always later than the real day. So keep the list's own order and never re-sort it by date. An upload counts as after 2026-08-24 only when its date is still after 8/24 once its rounding comes off: 7 days for a week date, 1 month for a month date. YouTube changed how it counts a view on 2026-08-24, so a median across that date mixes 2 kinds of view. When 8 or more kept uploads came out after 2026-08-24, the usual is the median views of those, the newest 20 at most.
3. Fewer than 8 after that date: the usual is the median of the newest 20 kept uploads, and the row's note says `usual spans 8/24`. The row stays.
4. Fewer than 8 kept uploads in all, or a usual under 10 views: no usual number. Drop the row and say so. A score on 3 or 4 views is noise.

The list gives rounded views and dates, so a usual is always said as "about". The row's own views come off its watch page, exact.

## The score

    score = the video's views / its channel's usual views

1 decimal. To the founder it is "N times what that channel usually gets".

## The table

Ranked by score, 12 rows at most, every row a link. Download every row's thumbnail into `src/` (the titles and thumbnails clone from them).

    | # | Title | Channel | Views | Days old | Length | Usual (n) | Score | Link | Note |

Under it, 1 line each for the top 5, and for the pick when it sits below row 5: what the video does, read off its title and description, never guessed past them.

## The pick

Start from the score. Pick the highest-scoring row whose own topic is THE PROBLEM on `squad/business.md`, told to WHO line 1. A row about the buyer's wider business can be a title source, never the pick. No row passes: No winner yet, below. A title shape that repeats across 2 or more rows beats 1 lucky row. A row that answers a buyer message breaks a tie.

Say it in 2 lines: the row, and why. Write the table, the summary lines and the pick into `squad/week/thumbs/<date>/src/rows.md`. Then stop with 1 line: "Type Take the pick., or Take row N."

## No winner yet

No row at 1x or over: widen once, 1 step out to the buyer's wider problem, same buyer, same window. Still none: print the table and "No winner yet. Nothing beat its own channel this week." Stop. The founder can still type "Take row N."
