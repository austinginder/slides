# Build Anything With Claude And WordPress

**WordPress Lancaster Meetup - Thursday, July 16, 2026 - 7:00pm**

The through-line: with AI agents, the code output isn't the valuable part
anymore. The *direction* is. A few conversations with Claude Design and a few
conversations with Claude Code, and an idea becomes a real WordPress site. Three
recent real-world projects, the workflow that makes them fast, and the tips that
make it repeatable.

---

## 1. Title

Build Anything With Claude And WordPress
Austin Ginder · WordPress Lancaster Meetup · July 16, 2026

## 2. Quick who / why me

- I run Anchor Hosting - a few thousand WordPress sites, mostly solo
- Developer first, one laptop since 2012
- Since February 2026, I build almost everything with Claude Code
- Tonight isn't theory. It's what I actually shipped this spring.

## 3. The one idea to take home

- With open source, the valuable thing was the code. You shared the code.
- With AI, the code output isn't the valuable part anymore
- What's valuable is *how you directed the agent to get there*
- "Build anything" is real now. The bottleneck moved from typing to steering.

## 4. What "a conversation" actually produces

- Not a chatbot answer. A running WordPress site.
- Custom plugins, custom database tables, REST APIs, themes, WP-CLI commands
- Real WordPress, all the way down. No lock-in, no new framework to learn.
- The same skills you already have (WP-CLI, PHP, git) are now the steering wheel

## 5. What the direction looks like

- The whole skill is *directing* the agent: a couple of sentences, then it builds for 30 minutes to an hour on its own.
- Verbatim shape: "Take this design and make a custom WordPress theme. Build a custom plugin for the engine - it should have a custom database table."
- A simple landing page is a quick run; a custom plugin/engine runs much longer - but it's not much more direction.
- Name the architecture. A few key terms ("custom theme", "custom plugin", "custom database table") drive some very complicated programming.

## 6. The workflow: idea to live site

The repeatable pipeline behind every project tonight:

1. **Design in Claude** - mock the whole UI as a Claude Design project (a `.dc.html` prototype)
2. **Pull it into Claude Code** - DesignSync reads the design; Claude translates it to WordPress
   - `sc-for` becomes a PHP loop, `onClick` becomes a real route, hover styles become CSS
3. **Build & run locally on Cove** - every project runs locally on my Mac via cove.run before it ever touches production. You don't even need to know what Cove is; Claude does.
4. **Verify in a real browser** - Claude drives Chrome, screenshots light + dark, catches what code review misses
5. **Ship via self-hosted updates** - GitHub release + a `manifest.json` self-updater. The release is the deploy.

- No wp.org, no CI pipeline. Idea in a conversation, live site by end of the session.

## 7. Project 1 - League Report. The real-world rescue.

- The setup: LeagueLineup / Stack Sports announced they were shutting down
- Years of amateur softball league history about to be deleted
- First prompt, verbatim: "The platform is going away in the next few months. I'd like to build a custom WordPress theme and a custom WordPress plugin to power the team engine. Can you help plan this out."
- Started in plan mode with subagents reading the existing league content

Source: https://league.report

## 8. League Report - what got built

- A platform where each league gets its own private, secret URL
- Schedule, standings, results, rosters, photos, news, files, member directory
- Non-technical commissioners edit scores and rosters **inline on the live page** - no wp-admin
- 14 custom database tables · 22 REST controllers · 19 page templates
- Crawled the dying platform into SQLite, imported **3,045 leagues**
- Claude even named the project (I asked - "league report" was a placeholder)

## 9. League Report - what it took

- 92 days · 30 Claude Code sessions · 561 human turns of direction
- ~5,900 lines of working code by the end of session one
- 103 screenshots handed over · 26 hard interrupts · 7 course-corrections
- v2 redesign started as a Claude-designed mockup: "overhaul the interface using this Claude design. Is it possible to develop this new design as the v2?"
- Real human moments: "Bah... I think it was better before. Can we revert?"
- Solo, no git repo, ships by zipping and `wp ... install --force` over SSH

## 10. Project 2 - Dismissed.FYI. Designed in a morning.

- A public hall of shame for WordPress admin-notice spam
- Every license nag, review beg, telemetry opt-in, and upsell - catalogued
- Each one pinned to the exact plugin `file:line` that renders it
- Ranked by intent: Critical = pure vendor benefit. Low = actually serves you.

Source: https://dismissed.fyi

## 11. Dismissed.FYI - the design-to-code story

- Started as a single Claude Design mockup one morning (Jun 5)
- The WordPress build is a direct port - the code comments literally say "mirrors the design's data.js"
- 28 days · 20 Claude Code sessions · 269 turns of direction
- 11 of 20 sessions opened with a saved slash-command workflow I'd codified

## 12. Dismissed.FYI - the clever part

- Admin notices are just callbacks. Enumerate them, then use PHP Reflection to pin the exact `file:line`
- Not scraping HTML - reflecting into the code itself
- Severity = how much of wp-admin it hijacks. Renders on 3+ unrelated screens = auto-critical.
- Everything renders in a throwaway local sandbox, fed plugin *files* from a wp.org mirror. Never a live site.

## 13. Dismissed.FYI - the responsible-building beat

- Early versions rendered notices against live sites
- One nag baked a real customer's account name into a public card
- July 1: hard architecture pivot - retired all live-site rendering, moved to local sandboxes
- Building fast with AI still means catching your own mistakes. The agent will do what you steer it to.

## 14. Project 3 - Rutter. Built in one evening.

- The idea that ties this whole talk together
- "The code output isn't actually that valuable. What is valuable is how the user directed the AI agent to get to the completed project."
- Rutter = open source for AI builds. Browsable recaps of *how* a human steered an agent.
- GitHub shares the code. Rutter shares the flow.

Source: https://rutter.run

## 15. Rutter - conceived and built in a single session

- One 22-turn Claude Code session, one evening (~2.5 hours)
- Idea to design to named product to working WordPress site, all in one sitting
- Design as a `.dc.html` in Claude Design, imported over the design MCP, hand-built into a theme + plugin
- `rutter-core` plugin: a custom table, its own `/r/<slug>/` routing, a WP-CLI command
- Nautical vocabulary: a rutter is a sailor's book of directions. Fitting.
- Dogfooded immediately - the first recap was Rutter's own build data

## 16. The spectrum

- League Report: 92 days, a full platform for real clients
- Dismissed.FYI: 28 days, designed in a morning
- Rutter: one evening
- Same workflow, wildly different scope. Build anything means anything.

## 17. Built the same way - the lightning roster

Three tonight. But the same pipeline runs across everything I ship:

- **WP Beacon** (wpbeacon.io) - plugin supply-chain intelligence, backed by a full git mirror of wp.org
- **WP Registry** (wpregistry.io) - a content-addressed WordPress security registry
- **Minn Admin** - a reimagined wp-admin, served as a no-build SPA alongside the classic one
- **Disembark** (disembark.host) - dark single-page marketing site for the backup product
- **Seafloor** - page content as structured JSON, edited entirely from WP-CLI
- **Anchor Blocks** - custom server-rendered Gutenberg blocks for the blog
- **Cove** (cove.run) - the local WordPress dev CLI every one of these runs on
- **CaptainCore** (anchor.host) - the fleet control plane behind the whole operation

- Same design-in-Claude, build-in-Claude-Code, real-WordPress recipe every time

## 18. Tips & tricks - getting the most out of Claude Code

- **Design first.** Mock the UI in Claude Design, then let Claude translate it to PHP. Implement against a spec, not a guess.
- **Develop locally, never touch prod directly.** Every project gets a `*.localhost` site first.
- **Make it verify in a browser.** Have Claude drive Chrome and screenshot both themes before calling a screen "done."
- **Persist hard-won architecture as memory.** Gotchas survive across sessions instead of being rediscovered.
- **Standardize your commits** (Emoji-Log: NEW / IMPROVE / FIX / DOC / RELEASE). Clean, scannable history for free.
- **Self-host updates** with a `manifest.json` self-updater. The GitHub release is the deploy - no wp.org needed.
- **Mine your own history.** command-center indexes 1,400+ past sessions - your prior AI work becomes a reusable knowledge base.

## 19. One skill, the whole release

- The payoff of "write a skill per project." Example: `/dev-minn-admin`.
- One runbook holds every workflow, deploy, and release step. Then I just say "cut a release."
- That one phrase runs the whole pipeline:
  1. Runs the full Playwright test suite - green, or no release.
  2. Bumps the version in all four places, dates the changelog.
  3. Commits, zips, and publishes the GitHub release.
  4. Regenerates the marketing screenshots from the live app.
  5. Refreshes the marketing homepage - new plugins, updated feature claims.
  6. Deploys the landing site, purges cache, verifies it's live.
- Direction once, automation forever. Steering compounds into leverage.

## 20. Takeaways

- The code is cheap now. The direction is the craft.
- WordPress is the perfect target - plugins, tables, REST, CLI, all buildable in a conversation
- Design in Claude, build in Claude Code, run it on real WordPress
- You already have the skills to steer. Start with one small idea.

## 21. Q&A + demo

Questions, discussion, and a live look at any of the three.
