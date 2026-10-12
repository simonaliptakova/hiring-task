# Context: Apify's Notion and knowledge setup

Read this before you start. It describes the environment your solution has to work in. Anything not covered here, make a reasonable assumption and write it down.

## The company

- Apify is a web scraping and automation platform (Prague HQ, remote-friendly). Around 250+ people across 50+ teams (Engineering, Product, Marketing, Sales, Customer Success, People, Finance, Legal, ...).
- Mostly technical audience: a large share of Apifiers are engineers who default to GitHub and Slack, not Notion.
- Working language is English. Slack is the main internal channel, email the main external one.
- Every Apifier has unlimited Claude. AI agents (Claude, connected to Notion, Slack, Google Drive and GitHub via connectors/MCP) are a first-class reader of our knowledge base, not an afterthought.

## Where knowledge lives today

| Source | What's there | Known issues |
|---|---|---|
| **Notion** | Company wiki, policies, processes, team spaces, project docs, meeting notes | 25,000+ pages. Searching a basic company question gets the right answer roughly 3 times in 10. The rest: outdated pages, duplicates, someone's personal notes or meeting minutes. |
| **Slack** | Day-to-day decisions, announcements, Q&A | Decisions made in threads rarely make it back into Notion. |
| **Google Drive** | Spreadsheets, contracts, slides, finance and HR files | No consistent link between Drive files and the Notion pages that reference them. |
| **GitHub** | Code, technical docs, READMEs, some internal tooling and Claude skills | Engineering knowledge partly duplicates what's in Notion. |

## Notion plan and its constraints

- **We are on the Notion Plus plan.** We evaluated Business/Enterprise together with the Notion team and decided to stay on Plus. 
- Treat this as a fixed constraint. **Solutions that only work after upgrading to Business/Enterprise won't be accepted.** If you think an upgrade is genuinely worth it, you can make that case separately, with numbers.
- What this means in practice:
  - No Notion AI. We use Claude (with the Notion connector) instead.
  - Through the Notion MCP connector, search is keyword-based and returns roughly 50 results per query with no pagination. Filters such as `last_edited_date_range`, `edited_by_user_ids`, `title_only`, `content_status`, and sorting by last edited or created date require Business and don't work for us.
  - The public Notion API is available (create/read/update pages, databases, comments, users). Notion buttons and some UI-only actions can't be triggered through the API.
  - Native database automations exist on Plus, but most of our knowledge lives in regular pages, not database rows.
- All company-wide content sits in one open teamspace ("General"), visible to every Apifier.

## Tools you can assume we have

Notion (Plus), Slack (incl. bots and webhooks), Google Workspace, GitHub, Claude (incl. Claude Code, skills and scheduled tasks), and the Apify platform itself (scheduled serverless "Actors", see https://docs.apify.com). Engineering can help with infrastructure, but whatever you build should be maintainable by a non-engineer in the People team.

## Our culture, in three lines that matter for this task

- **90/10 solutions.** A solution that covers 90% of the problem and ships now beats a perfect one that ships in six months.
- **Premature automation is evil.** Only automate what no longer scales manually. We'll ask you what you chose *not* to automate.
- **Use AI generously, and use it well.** AI slop is still slop.

## What's in this repo

- `README.md`: an overview of the case study. The brief we sent you has the full details.
- `context/CONTEXT.md`: this file.
- `data/notion_page_inventory.csv`: a synthetic export of page metadata from a slice of our workspace. Names and pages are fictional but realistic. Columns are described in `data/README.md`.
