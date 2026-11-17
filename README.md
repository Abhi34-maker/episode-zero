# Episode Zero

A prototype that takes a new writer from a rough story idea to a structured story concept, an outline, a gap check, notes on the opening episode and a seven-day writing plan.

Built by Abhinand P Nair for a Pocket FM Growth Manager application. This is an independent prototype. It is not an official Pocket FM product and is not affiliated with Pocket FM.

## View it

- **Demo:** `https://YOUR-USERNAME.github.io/episode-zero/` (replace after you turn on GitHub Pages)
- **What you will see:** a finished, pre-written example run. Open the page and press **See a finished example**.
- **Why there is no live AI here:** the live questions and outputs call Claude, and that only works when the page runs inside Claude. A public GitHub page has no safe way to call an AI service, because any key placed in the page would be visible to everyone. The example run shows exactly what the live version produces, and it is labelled as pre-written.
- **Live version:** `ADD THE CLAUDE ARTIFACT LINK HERE IF YOU SHARE IT`

## The problem

A new writer often has a spark but does not know the genre, how to structure a long story, how to build a hero, or what makes a good first episode. Many stop before they draft anything. This tool covers the first ten minutes: from "I have an idea" to "I know what I am writing and what to do this week."

## What already exists

I checked before building. Pocket FM already offers writer tools, based on public pages and press coverage (I could not see inside the logged-in products):

- **Pocket CoPilot:** idea generation, plot-hole and logic checks, cliffhanger help, character and episode tracking, localisation. A report reposted on [GeekBlog](https://geekblog.net/tech-news/pocket-fm-gives-its-writers-an-ai-tool-to-transform-narratives-write-cliffhangers-and-more/) says writers have had it since 2024. See also the [CoPilot page](https://copilot.pocketfm.com/).
- **Sherpa:** a multi-agent system for long serialized fiction, with ideation, planning, research, drafting and feedback agents and long-term story memory. See [this report](https://www.entangledtext.com/news/pocket-fm-launches-sherpa-an-ai-system-for-hundreds-episode-fiction) and [this one](https://www.newsbytesapp.com/news/science/pocket-fm-launches-sherpa-ai-assistant-for-serialized-fiction-creators/tldr).
- Outside Pocket FM, tools such as Sudowrite, NovelCrafter and Squibler generate outlines and plots, but they are general-purpose, not built for serialized audio.

So an "AI outline and plot-hole generator" is not new. This prototype targets the step before those tools: a first-timer who does not yet have a concept. It ends in a plain-text story brief the writer can take into whatever tool they use next. I do not know whether Pocket FM already has a guided flow for this, so treat the gap as a hypothesis.

## What it does

1. **Spark:** the writer enters a one- or two-sentence idea.
2. **Questions:** the AI asks one question at a time and adapts to each answer. Every question offers three options with examples from the writer's own idea, a free-text box, and a "not sure, suggest for me" path. A live card shows what the AI has understood so far.
3. **Concept and outline:** a script-style title page, the key fields, a four-act outline and a list of every assumption the AI made, so the writer can change them.
4. **Gap check:** possible plot gaps, each pointing to the part of the outline it came from, with a question and two ways to resolve it. The writer marks gaps resolved.
5. **Episode one:** a checklist (strong, risky or missing), three changes worth making, and an idea for how the opening could play.
6. **Roadmap:** seven small daily tasks ending in a finished first-episode draft, plus a copyable story brief.

## Design choices

- **The writer stays in control.** The AI suggests and the writer decides. It does not write the story, and the opening idea is labelled as something to react to, not text to copy.
- **Plain language for beginners.** Terms like genre and stakes are explained, and "I'm not sure" is a first-class answer.
- **Candid, not flattering.** The gap check is told to be specific and to return fewer gaps rather than invent problems.
- **Assumptions are visible.** Anything the AI guessed is listed for the writer to change.
- **No invented specifics.** The prompts forbid episode counts and running times, since those depend on the platform.

## Hypothesis and metric

Writers who reach a clear concept in one sitting are more likely to draft episode one within seven days. The measure would be the share of new writers who go from idea to first-episode draft within seven days. **This has not been tested with real writers.** No results are claimed.

## Limits

- The AI can be wrong or generic. Every output is a prompt for the writer's own judgement.
- The example run was written by hand to show the format. It is not live output.
- Not tested with real writers, and not integrated with any Pocket FM product.
- Not tested on every browser or screen size.

## How it is built

A single `index.html` with plain JavaScript and no build step. The prompts are in the functions `interviewPrompt`, `conceptPrompt` and `secondPrompt`. Inside Claude, the page calls the viewer's own Claude account through Claude's artifact runtime. Outside Claude, it falls back to the example run.

To run it locally, open `index.html` in a browser.
