# Chivalry (骑士精神)

An open-source Chivalry skill pack built primarily for Claude Code, with ready-to-use adapters for Cursor and Codex.

This is **not** fake gallantry, macho cosplay, or “be nice at all costs.”
It is a practical honor engine.

English | [简体中文](README.zh-CN.md)

## Compatibility

| Tool | Status | Integration |
| --- | --- | --- |
| Claude Code | First-class | Native skill/plugin files in `plugins/chivalry/skills/chivalry/` |
| Cursor | Supported | Rule file in `.cursor/rules/chivalry.mdc` |
| Codex | Supported | Root-level `AGENTS.md` |

## What it does

The skill looks at a message, decision, or situation and answers two questions:

1. Is this knightly, passable, unknightly, base, or craven?
2. What is the more honorable move right now?

It is designed for modern situations: conflict, apology, leadership, loyalty, romance, bystander moments, public speech, retaliation, status games, and damaged trust.

## Why this idea is fun

A weak “virtue” skill becomes a preachy etiquette bot.
A good chivalry skill has tension.

The interesting part is not politeness. The interesting part is conflict between values:

- loyalty vs justice
- courage vs prudence
- mercy vs accountability
- courtesy vs blunt truth
- devotion vs consent
- service vs self-respect

That gives the skill actual bite.

## The core code

This skill judges by seven tests:

- **Oath** — Did you keep your word, duty, or implied obligation?
- **Courage** — Did you face the rightful burden instead of hiding?
- **Mercy** — Did you avoid needless cruelty or humiliation?
- **Courtesy** — Did you preserve dignity, especially in public?
- **Protection** — Did you shield the more exposed person?
- **Honor** — Did you act fairly, openly, and without cheap tricks?
- **Measure** — Did you show restraint, or did ego take the wheel?

## What it rejects

The skill is deliberately hostile to fake chivalry:

- possessiveness disguised as protection
- jealousy disguised as devotion
- fighting for ego and calling it courage
- white-knighting for applause
- public humiliation as “honest truth”
- grand gestures that create debt
- sexism, paternalism, stalking, coercion, revenge theater

Consent, law, safety, and basic dignity outrank pageantry.

## Repo layout

```text
chivalry/
├── .cursor/
│   └── rules/
│       └── chivalry.mdc
├── .claude-plugin/
│   └── marketplace.json
├── AGENTS.md
├── README.md
├── README.zh-CN.md
├── VERSION
└── plugins/
    └── chivalry/
        ├── .claude-plugin/
        │   └── plugin.json
        └── skills/
            └── chivalry/
                ├── SKILL.md
                ├── principles.md
                ├── scenarios.md
                └── examples.md
```

## Install

### Option 1: use it as a standalone skill

Copy this directory:

```text
plugins/chivalry/skills/chivalry/
```

to:

```text
~/.claude/skills/chivalry/
```

Then use:

```text
/chivalry Your scenario here
```

This is the nicest developer experience because the command is short.

### Option 2: test the plugin locally

Run Claude Code with the plugin directory:

```bash
claude --plugin-dir ./plugins/chivalry
```

Then use:

```text
/chivalry:chivalry Your scenario here
```

### Option 3: publish the marketplace

Once this repo is on GitHub or another git host:

```bash
claude plugin marketplace add <your-repo>
claude plugin install chivalry@chivalry-tools
```

Then invoke the skill:

```text
/chivalry:chivalry I publicly embarrassed a teammate while proving a point. Was that knightly?
```

### Option 4: use it in Cursor

Copy this file into your target project's `.cursor/rules/` directory:

```text
.cursor/rules/chivalry.mdc
```

Then ask normally in Cursor chat, for example:

```text
Is this knightly, or am I dressing up vanity as virtue?
```

### Option 5: use it in Codex

Copy `AGENTS.md` to the root of your target repo, or merge its Chivalry section into an existing `AGENTS.md`.

Then ask normally in Codex, for example:

```text
Give me the Chivalry read on this apology draft.
```

## Example prompts

- “I promised I would help, but now I want out. What is the knightly move?”
- “My boss wants me to cover up a mistake. Is loyalty more important here?”
- “I called someone out in public because they deserved it. Was that honorable?”
- “Someone weaker was being mocked and I stayed quiet. What would a knight have done?”
- “Is ghosting after three dates unchivalrous?”
- “I want to protect my girlfriend by checking who she talks to. Is that chivalry or control?”
- “这算不算骑士精神？”
- “一个体面的骑士在这种局面下该怎么做？”

## Output style

The skill returns a direct ruling, not fake numerical precision.

Typical format:

```text
Verdict: Unknightly
Herald's line: You defended your pride, not the vulnerable.
Passed or failed tests: Mercy, Courtesy, Measure
The more knightly move:
1. Repair the public damage.
2. Address the issue privately and directly.
3. Stop turning authority into theater.
Words you can use:
"I was right about the issue and wrong about the way I handled it. Let me fix that."
If already done, penance:
"Repair it within a day. Restitution delayed becomes vanity."
```

## Customize it

You can tune this skill in three directions:

1. **More Arthurian** — more romance, devotion, and symbolic language.
2. **More practical** — less flavor, more workplace and relationship tactics.
3. **More severe** — harsher rulings on cowardice, vanity, and status abuse.

The current version aims for “practical with a ceremonial edge.”

## My view

The skill becomes memorable only when it is willing to say:

- “That wasn’t noble. That was vanity.”
- “That wasn’t protection. That was control.”
- “That wasn’t courage. That was theater.”
- “That wasn’t mercy. That was weakness dressed as kindness.”

Without that edge, the whole thing dies.


## Codex art assets

Stable relative paths reserved for future README composition:

- [`assets/hero-chivalry.png`](assets/hero-chivalry.png)
- [`assets/seven-tests.svg`](assets/seven-tests.svg)
- [`assets/compatibility-map.svg`](assets/compatibility-map.svg)

<details>
<summary>Reusable prompt for <code>assets/hero-chivalry.png</code></summary>

Create a solemn frontispiece for **Chivalry / 骑士精神** as a public **Iron Law Codex**, not a developer tool landing page, not a fantasy game UI, and not a glossy SaaS illustration. Show a single law-bearer or knight-scribe before an opened codex bound in black iron and worn parchment. Surround the scene with forged iron framing, austere heraldic sigils, wax seals, vellum grain, soot, and restrained old-gold ornament. Light the image only with candlelight and a distant brazier so the atmosphere feels cold, doctrinal, ceremonial, and absolute rather than adventurous. Palette: black, iron gray, old gold, parchment white, ember amber. Composition: wide hero image for a GitHub README, strong central codex, generous negative space for title treatment, cinematic but severe. Avoid neon, bright magic, smiling mascots, game HUD elements, cartoon rendering, or modern product-illustration tropes.

</details>

## License

Use it, fork it, mutate it.
Just do not sand off the teeth.
