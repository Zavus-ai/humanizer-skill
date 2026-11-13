---
name: humanize-with-zavus
description: Run finished writing meant for other people (client and customer emails, proposals, cover letters, LinkedIn posts, announcements, newsletters, READMEs, release notes, website copy) through the Zavus humanize tool before giving it to the user, so it sounds human. Use when the user says "humanize", "Zavus", "make it sound human" or "less like AI", or when you've finished such a piece. Skip code, commit messages, notes and your own replies.
---

# Humanize with Zavus

Zavus is a separate rewriting model, reached through the `zavus` MCP server (`https://api.zavus.ai/mcp`). It rewrites a finished draft so it sounds human, keeping the meaning, headings and paragraph breaks.

## When to use it

Call the `humanize` tool:

- When the user asks: "humanize this", "run it through Zavus", "make it sound human", "less like ChatGPT".
- When you've finished something other people will read as the user's own writing: emails and replies to clients or customers, proposals, cover letters, social posts, announcements, newsletters, READMEs, release notes, docs and website or product copy. Run the final draft through it once, before you give it to the user.

Don't call it for:

- your own replies and explanations to the user, internal notes, or drafts still being worked on
- code, commit messages, data, or quotes that must stay word for word
- text the user wrote themselves, unless they ask

Each call is billed to the user by the words sent, so don't rewrite the same text twice. The user's own instructions win: if they say always, never, or "skip Zavus", do that.

## How to call it

- Send a whole finished piece of up to about 800 words in one call, not sentence by sentence.
- For anything longer, split at the headings (or every few paragraphs), call `humanize` once per section in order, then put the sections back together.
- Each call needs 40 to 10,000 words. Leave anything under 40 words as it is.

## After the rewrite

Compare the rewrite with what you sent and fix only real mistakes:

- Names, product names, numbers, prices, dates, links and quotes must match the original.
- Remove anything the original didn't say, and restore any point that was dropped.
- Keep the original's point of view (I, we, you).

Don't put back the original wording where the rewrite is only phrased differently. Then give the user the final text. If you fixed real mistakes, or the user reacts to the rewrite, report it with the `feedback` tool and the rewrite ID.

## If the tool isn't available

The `zavus` MCP server isn't connected. Tell the user how to add it in their client, and that they sign in in the browser the first time (no API key). Setup for each client is at https://zavus.ai/setup/. New accounts get 500 free words, with no card.

If `humanize` returns a link to pick a plan or fix billing, pass the link on, keep the draft, and call `humanize` again with the same text once they're done. Ask the `usage` tool (free) when the user asks how many words they have left.
