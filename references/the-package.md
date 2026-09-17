# The titles, the package file, and "Pair N won."

## The titles

3 titles. Each is a clone of a verified row in `squad/week/thumbs/<date>/src/rows.md`, never an invented one.

- **Title 1, the main:** clones the pick. From week 2, when `squad/lane.md` has a row under `## Your own winners`, the newest one's shape takes title 1 (fill the [brackets] with this video) and the pick moves to title 2.
- **Titles 2 and 3:** the next highest-scoring rows whose promise this video can keep, on a title shape different from title 1.
- **The clone:** cut the source title at its first `|`, and drop episode numbers and guests' names; a stranger's name never lands in the founder's title. Then keep every word of the source title except 1 or 2. Those turn into up to 3 of the words the buyer uses (BUYER WORDS on `squad/business.md`, the buyer messages, the searches that found rows). "He" or "she" turning to "I" does not count as a turned word.
- **Never smarter.** The shape already won on real viewers. Improve it and the proof is gone.
- **A receipt for every number:** a line on `squad/business.md`, or a count the pick's own transcript already holds, named next to the title with where it is said. A count the video "will show" is not a receipt, because the script keeps the pick's order and cannot add one. No receipt: turn that number into words that need none, or clone the next row.
- **The video keeps the promise.** A title whose promise the pick's transcript does not hold goes to the next row, because the script changes only the example, the claims and the endings.
- **The founder's swapped word wins** over the shape.

Print them as a table, in the message that carries the cost line:

    | # | Title | Cloned from | Score | Words turned | Receipt |
    |---|---|---|---|---|---|
    | 1 | <title> | [<source title>](<link>) | <n> | "<old>" to "<new>" | <receipt, or no number> |

On yes, write the same table into `squad/week/thumbs/<date>/titles.md`, under `# Titles · <date> · yes`.

## The package file

On "lock", write `squad/week/<date>-package.md`. The first 2 lines are the join lines the next agents read, exactly in this form:

    episode: squad/episodes/epNN/
    source winner: <date>-winner.md

    # Package · <date> · locked

    | Pair | Title | Thumbnail | Cloned from | Words turned | Receipt |
    |---|---|---|---|---|---|
    | 1 (main) | <title> | squad/week/thumbs/<date>/pair-1.jpg | [<source title>](<link>) · score <n> | "<old>" to "<new>" | <receipt, or no number> |
    | 2 | <title> | squad/week/thumbs/<date>/pair-2.jpg | ... | ... | ... |
    | 3 | <title> | squad/week/thumbs/<date>/pair-3.jpg | ... | ... | ... |

    A/B test: Upload with pair 1. Once the video is public, open it in YouTube Studio on a computer and press A/B Testing. Add all 3 pairs, title and thumbnail together. YouTube keeps the pair people watch longest and tells you in a few days to 2 weeks. Then type "Pair N won." No A/B Testing button (it needs the channel's advanced features, and a public long video): keep pair 1.

- **epNN:** `ep01` the first time, else 1 more than the highest `squad/episodes/epNN/` on disk. Create the empty folder.
- **A package file for this winner already there, marked title-only:** overwrite it in place and keep its 2 join lines as they read. 1 episode, 1 folder, 1 package file.

## The title-only package

Written on the yes when `squad/face/` is empty or Higgsfield has no paid plan. The same file and the same 2 join lines, heading `# Package · <date> · title-only`, the Thumbnail column reading `not built`, and no A/B test line. Create the episode folder. The lock later overwrites it in place.

## "Pair N won."

1. Take the newest `squad/week/*-package.md` with no `won:` line.
2. Add `won: pair N · <today>` on the line right after the 2 join lines.
3. Append 1 row under `## Your own winners` in `squad/lane.md`:

       | <today> | <the winning title> | <its shape: the title with this video's words in [brackets]> | <source link> | <thumbnail path> |

4. Print the row with the video's main title, so the founder can say it was a different video. Stop.

## squad/lane.md

The agent's memory between weeks. Only this agent writes it.

    # Lane

    ## What you sell
    <only when squad/business.md was missing: the founder's 1 line>

    ## Channels
    - <channel name> · https://www.youtube.com/channel/<id>

    ## Buyer messages
    1. "<verbatim>" · <where it came from>

    ## Searches
    | Date | Search | Verified rows |
    |---|---|---|

    ## Your own winners
    | Date | Title | Shape | Cloned from | Thumbnail |
    |---|---|---|---|---|
