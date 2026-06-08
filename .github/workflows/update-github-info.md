---
name: update-github-info
description: Update site GitHub info from latest blog posts and changelog
on:
  schedule:
    - cron: '0 9 * * *'
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
safe-outputs:
    create-pull-request:
        title-prefix: "[mona] "
        draft: true
        fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
    allowed:
        - github.com
        - github.blog
---

# Update GitHub Info

Fetch the latest GitHub Blog content and update the site's GitHub info section.

## Instructions

You are an AI agent tasked with updating the GitHub information content for the website.

### Steps

1. **Read context**: Start by reading `notes/mona-notes.md` to understand the current context and any specific guidance.

2. **Fetch latest content**:
   - Fetch https://github.blog/latest/ to get the latest GitHub Blog posts
   - Fetch https://github.blog/changelog/ to get recent GitHub changelog updates
   - Extract the most relevant and recent updates (from the last few weeks)

3. **Update content**: Edit `site/content/github-info.md` with:
   - A "Latest GitHub Updates" section containing:
     - Recent blog posts from the GitHub Blog
     - Notable changelog entries
     - Links to the full posts
   - Keep the update date current
   - Maintain the existing structure and format of the file

4. **Create pull request**: Open a pull request with:
   - Title: "chore: update github-info with latest posts and changelog"
   - Description: Brief summary of what was updated (e.g., "Updated with latest GitHub Blog posts and changelog entries")
   - Target branch: main

### Guidelines

- Focus on updates from the last 2-4 weeks
- Only include relevant technical updates, features, or announcements
- Maintain professional and clear formatting
- Do not commit directly to main; use the pull request for review
