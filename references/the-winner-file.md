# The winner file

`squad/week/<date>-winner.md`, 6 parts, in this order. The raw pulls stay in `squad/week/thumbs/<date>/src/`.

## The pull

1 command (`./yt-dlp` when it was installed in the folder):

    yt-dlp --skip-download --write-subs --write-auto-subs --sub-langs en --sub-format vtt --write-comments --extractor-args "youtube:comment_sort=top;max_comments=100,100,0" -o "squad/week/thumbs/<date>/src/%(id)s" "https://www.youtube.com/watch?v=<id>"

A 429 or "not a bot": the rule in the-hunt.md, wait 10 minutes, retry once.

It writes `<id>.en.vtt` (the captions) and `<id>.info.json` (the numbers and a `comments` list). A video in another language: its language code in place of `en`.

## The template

    # Winner · <date>

    ## 1. The video
    **"<title>"** · <channel> · <link>
    - Views <n> · published <YYYY-MM-DD>, <n> days old · length <m:ss>
    - Usual about <n> (median of <n> long uploads) · **score <n>** · <note, if any>
    - What it does: <the 1-line summary from the table>

    ## 2. The transcript
    <the full text>

    ## 3. The thumbnail
    Words on it: "<exactly as written>"
    What it shows: <the person, the objects, the background, the colors>
    Layout: <where the face, the words and any screen sit, and how big, in % of the frame>

    ## 4. The top 100 comments, by likes
    1. <likes> · "<verbatim>" · @<author>

    ## 5. The angle
    <2 sentences: what this video's audience asked for in the comments and never got, and that the founder's video gives it>

    ## 6. The structure
    | Time | What this part does | Runs | On screen, when the words say |
    |---|---|---|---|
    | 0:00 | <the move, 2 to 6 words: the claim and its number> | 0:35 | <what the words say is on screen, or blank> |
    | 0:35 | ... | ... | ... |

## The rules for each part

1. **The video.** Numbers from the table, the summary line word for word. The next agent reads that line.
2. **The transcript.** The captions file with the timing lines, the tags and the repeated caption lines taken out. Nothing summarized. No captions: the description in its place, labeled `description, not transcript`. Another language: the transcript as it is, plus a short English pass, labeled as a translation. When the last caption ends after the video's duration in info.json, say so in 1 line with both times. Captions never name who is speaking. With 2 or more voices, never give a line to a named person unless the video names them right before it; quote it as the video's words.
3. **The thumbnail.** Read off the downloaded jpg the run opened, never off the title or the numbers. The layout line is what the thumbnails copy, so give sizes. No file: `THUMBNAIL UNREACHABLE`, never a guess.
4. **The comments.** Top-level only, sorted by `like_count`, highest first, verbatim, 100 at most. Fewer than 100 is data: all of them, and the count. The pull failed: say so, write `comments not pulled`, and the angle says it came from the transcript.
6. **The structure.** The winner, section by section, off the `.vtt` times: 8 to 15 rows, a new row
   where the topic turns (a new claim, a new step, a new screen, the ask, the close). `What this part
   does` names the move in 2 to 6 words, read off the words said, never guessed past them: the claim and
   its number, why listen, the problem, step 1, the reveal, the ask, the close. `Runs` is the length of
   that part. `On screen` is only what the words themselves say is on screen ("here's the dashboard"),
   else blank. The rows add up to the video's length. This table is what /execution-content-script
   copies: their order, our substance. No captions: the table has 1 row, `no transcript, no structure`.
5. **The angle.** Only from what is in the file. Fewer than 3 comments from viewers (the channel's own pinned comment does not count): the angle comes from the transcript and says so. Otherwise, from the questions, the complaints, the "you never showed" moments. What the winner's audience asked for and never got is the founder's video.
