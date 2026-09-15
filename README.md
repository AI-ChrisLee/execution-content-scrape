# The Winning Scrape

This skill is a base. Once you have done it your way, tell your squad "update the skill to do it like this."

Decides your next video off what is already winning with your buyers. It hunts the last 60
to 90 days, ranks every video against what its own channel usually gets, picks one winner
and digs it out: transcript, thumbnail, comments.

## Install

Say this to Claude Code, in the folder your squad lives in:

    Install this skill: https://github.com/AI-ChrisLee/the-winning-scrape. Clone the whole folder into .claude/skills as the-winning-scrape, without the .git folder.

## Run

    Run the Winning Scrape.

It asks one thing: which channels your buyers watch. Back comes the pick and how far it
beat its own channel. You take the pick, change any word that is not yours, and it writes
`squad/week/YYYY-MM-DD-winner.md` (and `squad/lane.md` on the first run).

The full procedure is `SKILL.md`. Stuck? Reply to the email that sent you here.
