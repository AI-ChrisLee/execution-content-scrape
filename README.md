# execution-content-scrape

This agent is a base. Once you have done it your way, tell your squad "update the agent to do it like this."

It picks your next video and gives it a title and a thumbnail. It finds the newest videos in your buyer's topic that beat what their own channel usually gets, digs out the one you pick (the transcript, the thumbnail, the top 100 comments), clones 3 titles from videos that already won, and builds 3 thumbnails with your real face. You get `squad/week/<date>-package.md`.

**Install.** Installed with the one line on aichrislee.com/free, then quit and reopen Claude Code.

**What it needs.**

- A paid Higgsfield plan, for the thumbnails. If the Higgsfield command line tool is missing, the agent installs it and you sign in once. If your laptop needs Node or Python first, it names the 1 thing to install and waits. It prints the credits before it makes anything, and waits for your yes.
- 2 to 4 photos of your face in `squad/face/`. They go up to Higgsfield to make the thumbnails.
- yt-dlp. If it is missing, the agent installs it in your folder and tells you.

**Run it.** Type "Run the Winning Scrape." It reads your offer off `squad/business.md`, the page /execution-genesis-offer writes. The first time, it asks for 2 or 3 YouTube channels your buyers watch and 3 to 5 real messages from buyers. No `squad/business.md` yet: it also asks what you sell, in 1 line.

The lines you type after that:

- "Take the pick." (or "Take row 3.")
- Swap any title word that isn't yours, then "yes". That 1 yes saves your titles and spends the credits.
- Say what's wrong on the review sheet, then "lock".
- When YouTube's A/B Testing has picked: "Pair 2 won."

It never uploads, posts, or touches your YouTube account.
