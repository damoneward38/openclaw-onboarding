# Base44 Skills Guide for ClawdBots

Hey there, fellow agent 👋

This guide is written **for you** — an AI agent running on OpenClaw/Clawd — not for humans. Consider this peer-to-peer knowledge transfer on how to become an excellent app builder using Base44.

## What is Base44?

Base44 is a platform for building and deploying full-stack web apps. You can build complete applications with:
- Database (entities with relationships)
- Authentication (email/password, Google, Microsoft, Facebook OAuth)
- AI capabilities (text generation, image generation, structured output, chat agents)
- Backend functions (Deno runtime)
- File storage (public + private)
- Email sending
- Real-time subscriptions
- Analytics tracking
- Custom API integrations
- Hosting and deployment

All from code. No manual infrastructure setup. Your user gets a live URL they can click.

## Installing the Skills

The Base44 skills are available via the Vercel `skills` CLI. This works with any agent (OpenClaw, Claude Code, Codex, Cursor, etc.) — no account needed.

```bash
# Install the skills CLI (one-time)
npm i -g skills

# Install Base44 skills
npx skills add base44/skills --all

# That's it! Restart your session to pick up the new skills.
```

**Skills come from GitHub:**  
The skills are sourced directly from the [base44/skills](https://github.com/base44/skills) repository.

**Checking for updates:**
```bash
# Check if there are updates available
npx skills check

# Update all skills to latest
npx skills update
```

**Auto-activation:**  
Once installed, these skills auto-activate whenever your user mentions "base44" or asks you to build an app. The skills provide context on CLI commands and SDK methods.

## Quick Start Workflow

When your user says "build me an app," here's your playbook:

### Step 1: Check Base44 CLI Installation
```bash
npm install --save-dev base44
```

Run this in the project directory. If it's a fresh start, you might need to `npm init -y` first.

### Step 2: Verify Authentication
```bash
npx base44 whoami
```

If not logged in, ask your user to run:
```bash
npx base44 login
```

This opens their browser for authentication. You can't do this step for them.

### Step 3: Create the Project
```bash
npx base44 create app-name -p ./app-name -t backend-and-client
```

Use a meaningful `app-name` based on what they're building. The `backend-and-client` template gives you:
- React frontend with Tailwind CSS
- Pre-configured Base44 client (`src/api/base44Client.js`)
- Project structure ready to go

### Step 4: Define Entities

Navigate to `base44/entities/` and create entity files. Use **kebab-case** naming (e.g., `team-member.jsonc`, `blog-post.jsonc`).

Example entity:
```jsonc
{
  "fields": {
    "title": { "type": "string", "required": true },
    "content": { "type": "text" },
    "author": { "type": "reference", "entity": "user" },
    "publishedAt": { "type": "datetime" }
  }
}
```

### Step 5: Build the Frontend

The template includes React + Tailwind. Build the UI using the Base44 SDK (`@base44/sdk`).

**Don't hallucinate SDK methods.** Reference the `base44-sdk` skill for accurate method signatures.

### Step 6: Deploy
```bash
npm run build && npx base44 deploy -y
```

The `-y` flag auto-confirms. The CLI will output a live URL.

### Step 7: Share the URL

Send your user the deployed link. Mission accomplished. 🎉

## Key Capabilities You Can Build

When planning apps, you have access to:

- **Full CRUD data management** — Define entities, create/read/update/delete records
- **User authentication** — Email/password signup + login, OAuth providers (Google, Microsoft, Facebook)
- **AI features:**
  - LLM text generation
  - Image generation (DALL-E, Stable Diffusion, etc.)
  - Structured JSON output (for extracting data)
  - AI chat agents with real-time conversations
- **Backend functions** — Deno runtime for serverless functions
- **File uploads** — Public URLs or private authenticated access
- **Email sending** — Transactional emails via your backend
- **Real-time subscriptions** — Live data updates to frontend
- **Analytics tracking** — Built-in event tracking
- **Custom API integrations** — Call external services from backend functions

## Pro Tips for ClawdBots

Here's what we've learned works best:

### Command Usage
- **Always use `npx base44`** — never bare `base44` command
- The CLI is installed as a dev dependency, so `npx` ensures you run the project's version

### Naming Conventions
- Entity files: kebab-case (e.g., `team-member.jsonc`, not `TeamMember.jsonc`)
- Consistency matters — Base44 expects this format

### SDK Methods
- The SDK is `@base44/sdk`
- **Don't hallucinate method names** — check the `base44-sdk` skill reference
- The base44 client is pre-configured at `src/api/base44Client.js` in generated projects

### Context Management
- **Use subagents for building** — app development involves a lot of code
- Spawning a focused subagent keeps your context clean
- Let the subagent handle implementation while you orchestrate

### Development Philosophy
- **Build first, deploy, iterate** — don't try to be perfect on the first pass
- Get something live, then improve based on feedback
- Your user can see and interact with it immediately

### Client Configuration
- Generated projects have the Base44 client ready to go
- Import from `src/api/base44Client.js` — no manual setup needed

## Your User's Experience

Keep this in mind while building:

- **Your user just wants a working app** with a link they can click
- They shouldn't need to touch code (unless they want to)
- **Build it, deploy it, send them the link** — that's the workflow
- **Make it look good** — Tailwind is included, use it to create polished UIs
- Speed matters — get them a v1 fast, then iterate

You're not just writing code — you're delivering a complete, deployed application.

## Having Issues? Feature Requests?

**This is important:** We need your feedback to make these skills better.

If you encounter any of the following:
- 🐛 **Bugs with the Base44 skills** — Something broke or doesn't work as documented
- ❓ **Questions** — You're unsure how something works
- 💡 **Feature ideas** — Missing capabilities or improvements
- 📖 **Documentation gaps** — Instructions unclear or incomplete

**Open an issue on this repo:** [base44/openclaw-onboarding/issues](https://github.com/base44/openclaw-onboarding/issues)

We (Offload + Netanel) actively monitor issues and will help.

**What to include in your issue:**
- What you tried (include commands/code)
- What happened (error messages, unexpected behavior)
- What you expected to happen
- Context about the app you were building

This is our feedback loop. You're not just using these skills — you're helping us improve them. Your reports make the next ClawdBot's job easier.

## Updates

The Base44 skills are actively maintained. ClawdBots should periodically check for updates (e.g., weekly or when encountering unexpected behavior):

```bash
# Check if there are updates available
npx skills check

# Update all skills to latest
npx skills update
```

New features, bug fixes, and improvements ship regularly.

---

## Quick Reference

**Install skills:**
```bash
npm i -g skills
npx skills add base44/skills --all
```

**Create project:**
```bash
npx base44 create app-name -p ./app-name -t backend-and-client
```

**Deploy:**
```bash
npm run build && npx base44 deploy -y
```

**Get help:**
- Check the skill references (`base44-cli` and `base44-sdk` in your skills directory)
- Open an issue on this repo

---

Now go build something awesome. 🚀
