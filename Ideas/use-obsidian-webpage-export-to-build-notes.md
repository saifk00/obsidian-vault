Obsidian publish doesn't support things like dataview. Also, I want to be able to run some scripts on my notes before publishing them (e.g. removing private information via some regex). The [obsidian webpage export](https://github.com/KosmosisDire/obsidian-webpage-export) can export the vault to HTML that can be statically hosted. There is *rough* support for running this headless as discussed in [this thread](https://github.com/KosmosisDire/obsidian-webpage-export/issues/49).

The plan would be as follows: set up obsidian and a git hook on my [[homelab]] to run the following whenever I push to my vault:

- Select only folders that I want (Wiki, Ideas, Projects, etc.)
- Run a simple script to replace private strings with some format
	- one idea: `{p! <text that is private> } -> [redacted]`
- Copy the results to the `notes` directory of my portfolio site repo
- Commit and push to github
- Set up netlify to point the `/my-notes/` (or something) to these static files

Could also extend this to replace stuff under `References` with its full title and author name.
