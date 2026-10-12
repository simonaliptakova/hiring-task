# notion_page_inventory.csv

Synthetic export of page metadata from a slice of Apify's Notion (export date 2026-10-01). People and pages are fictional. Treat it as you would a real, imperfect export: it has gaps and noise.

| Column | Meaning |
|---|---|
| `page_id` | Notion page ID |
| `title` | Page title |
| `path` | Breadcrumb from the teamspace root. `General / ...` = company-wide teamspace; `Personal / <name>` = someone's private-then-shared page |
| `created_by` | Who created the page. Note: moving or duplicating a page can change this. `(left YYYY)` = no longer at Apify |
| `created_time`, `last_edited_time` | ISO dates |
| `last_edited_by` | Last editor |
| `views_last_90d` | Page views in the last 90 days |
| `backlinks` | Number of other pages linking to this page |
| `word_count`, `image_count` | Rough size of the page content |
