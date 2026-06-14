# current-advisor
storing code for the currents widget displayed on marinopenwaterswim.org
How to edit the Paradise Beach Current Advisor widget
A plain-language guide for making changes to the currents widget. No coding required. Keep this file in your Claude Project (as your starting point) and as the README in the GitHub repo.

The big picture (how the pieces fit together)
The widget lives in three places, each with one job:
	•	GitHub — holds the actual code. This is the single source of truth. The version here is the real one.
	•	Cloudflare — a small "proxy" that fetches the tide-current data from NOAA. It's the gatekeeper that decides which websites are allowed to use it.
	•	GoDaddy (marinopenwaterswim.org) — just displays the widget. It points at the GitHub file with one line of code, so it updates automatically.
You only ever edit the code in GitHub. The live site updates on its own within a minute.

To make an edit, start here
Begin in the Claude Project (this is where this file lives). Then:
	1	Get the current code from GitHub.
	◦	Go to the current-advisor repository on GitHub.
	◦	Click the file paradise-beach-current-advisor.html.
	◦	Click the Raw button (top right of the file). This shows just the plain code.
	◦	Select all (Cmd+A) and copy (Cmd+C).
	2	Ask Claude.
	◦	Open the Claude Project and start a chat.
	◦	Describe what you want in plain English, then paste the code underneath.
	◦	Example: "Here's my current widget code. Please add a station for Angel Island." (paste code)
	3	Get the updated code back.
	◦	Claude returns the complete updated file. You don't have to find or change anything yourself.
	◦	Copy all of it.
	4	Put it back in GitHub.
	◦	In the repo, open paradise-beach-current-advisor.html.
	◦	Click the pencil icon (top right) to edit.
	◦	Select all the old code, delete it, and paste the new code.
	◦	Click Commit changes (and confirm if asked).
	5	Done. The live site updates automatically within a minute. There is no GoDaddy step.
Short version: GitHub → copy (Raw) → paste to Claude → Claude edits → paste back to GitHub → Commit.

Helpful to know
	•	You never need to read the code. Just describe the change you want ("add this station," "make the title bigger," "change the default time to 9am") and Claude handles it.
	•	GitHub remembers every version. If an edit ever looks wrong, tell Claude — you can roll back to the previous working version in a couple of clicks. So it's safe to experiment.
	•	Adding a station is a one-line change. When you're comfortable, Claude can show you which line to copy and edit yourself.

If something breaks
	•	Widget shows but no data loads ("Could not load NOAA data"): this is almost always the Cloudflare proxy's "allowed websites" list. The proxy only lets approved sites use it. Currently allowed: marinopenwaterswim.org, jenniefoconnor.github.io, and local testing. If you add the widget to a new website, that new address has to be added to the proxy too.
	•	To check the real error: open the page, press Cmd+Option+J (Chrome) for the console, reload, and look for a red line mentioning workers.dev. Paste that to Claude.

Key details (for reference)
	•	GitHub repo: jenniefoconnor / current-advisor
	•	Live widget file: https://jenniefoconnor.github.io/current-advisor/paradise-beach-current-advisor.html
	•	What GoDaddy uses: a single <iframe> pointing at the live widget file above.
	•	Cloudflare proxy: the noaa-currents-proxy worker (you control this account). Its job is fetching NOAA data and allowing approved websites.
	•	Data note — Yellow Bluff: its numbers come from the nearby NOAA station SFB1203 (Golden Gate Bridge, 0.46 nm E of), not the bluff itself. It's a good planning guide, but Yellow Bluff's real ebb runs stronger. Getting the exact Yellow Bluff data would require a change to the Cloudflare proxy — ask Claude if you ever want that.

A safety reminder
This widget is a planning aid, not a guarantee. Currents at the Golden Gate and Yellow Bluff can be strong and are affected by wind and weather the predictions don't capture. Always use your own judgment in the water.
