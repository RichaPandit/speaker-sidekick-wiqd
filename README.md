# 🎤 Speaker Sidekick

**Speaker Sidekick** is a WIQD-powered Microsoft 365 Copilot plugin that helps technical speakers turn rough ideas into conference-ready sessions.

Instead of immediately generating a title and abstract, Speaker Sidekick challenges the session idea first:

- Is this genuinely a 100, 200, or 300-level session?
- Is there a compelling story, or only a product walkthrough?
- Does the live demo prove something useful?
- Can the planned content realistically fit within the session duration?
- What knowledge should attendees already have?
- What supporting resources should be prepared?
- Where would GitHub resources or QR codes genuinely add value?

The goal is simple: help technical speakers design stronger, more focused, and more practical conference sessions.

---

## ✨ Capabilities

Speaker Sidekick can help with:

- Technical-session positioning
- 100, 200, or 300-level assessment
- CFP-ready abstracts
- Conference-session titles
- Target-audience definition
- Attendee prerequisites
- Measurable learning outcomes
- Session story arcs
- Session timing
- Live-demo design
- Demo fallback planning
- Attendee resources
- GitHub resource planning
- QR-code strategy
- Speaker preparation checklists

Speaker Sidekick is intentionally opinionated.

If a proposed 300-level session is really a product walkthrough, Speaker Sidekick should say so.

---

## 🧠 Architecture

The project is a WIQD plugin composed of a declarative agent and a reusable skill.

### Declarative agent

File:

```text
appPackage/declarativeAgent.json
```

The declarative-agent definition configures:

- Agent name
- Agent description
- Agent instructions
- Conversation starters

### Agent instructions

File:

```text
appPackage/instruction.txt
```

The instructions define Speaker Sidekick's persona and overall behaviour.

Speaker Sidekick is designed to be:

- Constructive
- Direct
- Technically credible
- Willing to challenge weak ideas
- Practical rather than flattering
- Conscious of audience, duration, and technical depth

### Design Conference Session skill

File:

```text
appPackage/skills/design-conference-session/SKILL.md
```

The skill contains the reusable methodology used to design and evaluate conference sessions.

The methodology covers:

1. Understanding the session idea
2. Challenging the premise
3. Defining the session promise
4. Determining the appropriate technical level
5. Developing session titles
6. Creating the CFP-ready abstract
7. Defining learning outcomes
8. Designing the session story and timing
9. Designing the demo and fallback
10. Planning attendee resources and engagement
11. Creating the speaker preparation checklist

This separation keeps the agent's personality distinct from the reusable conference-design expertise.

---

## 💬 Example prompt

```text
I want to deliver a 45-minute 300-level conference session about building AI-powered data experiences with Microsoft Fabric Data Agent.

The audience is experienced data engineers, analytics engineers, and Power BI developers.

I want to include a live demo and publish the supporting assets to GitHub.

Challenge whether this genuinely qualifies as a 300-level session and design the complete session for me.
```

Speaker Sidekick should challenge the premise before designing the session.

A complete response should include:

- Session verdict
- Recommended title
- Two alternative titles
- Recommended technical level
- Target audience and prerequisites
- CFP-ready abstract
- Three measurable learning outcomes
- Timed session story
- Demo design and fallback
- Attendee resources
- QR-code plan
- Speaker checklist
- One recommended improvement

---

## 🚀 WIQD lifecycle

One goal of this project was to explore the WIQD development lifecycle through a practical build.

```text
Create
  ↓
Configure
  ↓
Validate
  ↓
Provision
  ↓
Package
  ↓
Share
  ↓
Publish
```

### Validate

Validate the plugin structure before deployment:

```powershell
wiqd plugin validate
```

### Provision

Provision the plugin into the local environment:

```powershell
wiqd plugin provision --env local
```

Provision the plugin into the development environment:

```powershell
wiqd plugin provision --env dev
```

Provisioning creates or updates the agent in the selected Microsoft 365 environment.

### Package

Create a deployable Microsoft 365 app package:

```powershell
wiqd plugin package --env dev
```

The generated package is written under:

```text
appPackage/build/
```

### Share

Share the provisioned plugin with selected users:

```powershell
wiqd plugin share `
  --env dev `
  --scope users `
  --email user@contoso.com
```

Share the plugin with the entire tenant:

```powershell
wiqd plugin share `
  --env dev `
  --scope tenant
```

### Publish

Submit the plugin to the organisation's admin catalogue:

```powershell
wiqd plugin publish --env dev
```

Publishing is a separate distribution stage from provisioning and sharing.

---

## 🌍 Environment-specific naming

The project supports environment-specific naming through `APP_NAME_SUFFIX`.

The declarative agent uses:

```json
"name": "Speaker Sidekick ${{APP_NAME_SUFFIX}}"
```

Example resolved names:

```text
Local → Speaker Sidekick - [Local]
Dev   → Speaker Sidekick - [Dev]
```

A production environment can use an empty suffix:

```text
Speaker Sidekick
```

Environment-specific values should remain outside source control.

---

## ⚠️ Environment-variable precedence

One useful lesson from this build involved environment-variable precedence.

A PowerShell process-level value can override the corresponding value in an environment file.

For example, this value:

```powershell
$env:APP_NAME_SUFFIX = "local"
```

can cause a Dev package to resolve with the Local name if the value remains active in the terminal session.

Before provisioning or packaging Dev, verify the current value:

```powershell
$env:APP_NAME_SUFFIX
```

Set the correct Dev value:

```powershell
$env:APP_NAME_SUFFIX = "- [Dev]"
```

Then package the Dev environment:

```powershell
wiqd plugin package --env dev
```

To remove the PowerShell process-level override:

```powershell
Remove-Item Env:APP_NAME_SUFFIX -ErrorAction SilentlyContinue
```

---

## 🔍 Inspecting the generated package

When diagnosing environment resolution, inspect the actual packaged ZIP rather than only checking the source files.

Extract the Dev package:

```powershell
Remove-Item `
  .\dev-package-check `
  -Recurse `
  -Force `
  -ErrorAction SilentlyContinue

Expand-Archive `
  .\appPackage\build\appPackage.dev.zip `
  .\dev-package-check `
  -Force
```

Check the resolved agent name:

```powershell
Get-Content `
  .\dev-package-check\declarativeAgent.json |
  Select-String '"name"'
```

Expected result:

```json
"name": "Speaker Sidekick - [Dev]"
```

The source file can still contain the environment-variable expression. The extracted ZIP shows the value that was actually resolved during packaging.

---

## 🔐 Repository safety

Provisioned environment files and generated packages are excluded from source control.

The `.gitignore` should include:

```gitignore
# TeamsFx / WIQD environment files
env/.env.*
.localConfigs

# Generated packages
appPackage/build/
dev-package-check/

# Dependencies
node_modules/

# Miscellaneous
.env
.deployment
.DS_Store
Thumbs.db
```

Do not commit:

- Tenant IDs
- Teams application IDs
- Microsoft 365 application IDs
- Microsoft 365 Title IDs
- Share links
- Generated deployment metadata
- Packaged ZIP files

---

## 📁 Project structure

```text
speaker-sidekick-wiqd/
│
├── appPackage/
│   ├── declarativeAgent.json
│   ├── instruction.txt
│   ├── manifest.json
│   ├── color.png
│   ├── outline.png
│   │
│   └── skills/
│       └── design-conference-session/
│           └── SKILL.md
│
├── .vscode/
├── .gitignore
├── m365agents.local.yml
├── m365agents.yml
├── wiqd.plugin.json
└── README.md
```

---

## 🧪 Sample use cases

### Challenge a session idea

```text
I want to create a 45-minute session showing all the major features of Microsoft Copilot Studio.

I want it to be 300-level.

Challenge the idea and redesign it if the content does not justify that level.
```

### Turn a demo into a conference session

```text
I already have a working AI-agent demo.

Help me turn it into a conference session rather than a product walkthrough.
```

### Evaluate the technical level

```text
Review my proposed session and tell me whether it genuinely belongs at the 100, 200, or 300 level.
```

### Prepare a CFP

```text
Help me create a CFP-ready title, abstract, target audience, prerequisites, and three measurable learning outcomes.
```

### Design attendee resources

```text
Review my session plan and recommend the GitHub assets, supporting content, and QR-code strategy I should prepare for attendees.
```

---

## 💡 Why this project exists

Speaker Sidekick began with a conversation about starting a public-speaking journey.

The experiment became a useful way to explore a broader question:

> Can the methodology behind doing something well become reusable agent expertise?

Rather than placing the complete conference-design methodology inside the agent persona, the project separates two concerns.

### Agent behaviour

Defined in:

```text
appPackage/instruction.txt
```

### Reusable expertise

Defined in:

```text
appPackage/skills/design-conference-session/SKILL.md
```

This allows the agent persona to remain concise while the detailed conference-design methodology remains structured and reusable.

---

## 🛠️ Prerequisites

To work with this project, you need:

- PowerShell 7 or later
- WIQD CLI
- Microsoft 365 sign-in
- Access to a Microsoft 365 tenant that supports the required agent experiences
- Git, if contributing through source control
- Visual Studio Code, recommended but not required

Verify PowerShell:

```powershell
$PSVersionTable.PSVersion
$PSVersionTable.PSEdition
```

Expected:

```text
Major: 7 or later
PSEdition: Core
```

Verify WIQD:

```powershell
wiqd --version
wiqd doctor
```

Accept the Work IQ EULA when required:

```powershell
wiqd eula accept workiq
```

Authenticate interactively:

```powershell
wiqd auth login --interactive
```

---

## ▶️ Getting started

Clone the repository:

```powershell
git clone <YOUR-REPOSITORY-URL>
```

Open the project:

```powershell
cd speaker-sidekick-wiqd
code .
```

Validate the plugin:

```powershell
wiqd plugin validate
```

Provision a local development instance:

```powershell
wiqd plugin provision --env local
```

Provision a Dev instance:

```powershell
$env:APP_NAME_SUFFIX = "- [Dev]"
wiqd plugin provision --env dev
```

Package the Dev instance:

```powershell
wiqd plugin package --env dev
```

---

## 🚧 Project status

This is an experimental learning project built using preview developer tooling.

The repository is intended as:

- A WIQD learning sample
- A reusable agent-skill example
- A reference for separating agent persona from procedural expertise
- A practical conference-session design assistant

It is not represented as a production-ready application.

---

## 📚 Acknowledgements and resources

This project was inspired by:

- Microsoft's Work IQ Developer Tools preview announcement
- Microsoft 365 Agents Toolkit documentation
- Community learning content covering WIQD and Microsoft 365 extensibility

Relevant resources and the accompanying implementation article can be added here after publication.

---

## 👤 Author

**Richa Pandit**

Building and sharing practical experiments around:

- AI agents
- Microsoft 365 Copilot
- Copilot Studio
- Power Platform
- Agentic solution architecture
- Responsible and reusable AI patterns

---

## ⭐ Contributing

Ideas, issues, experiments, and adaptations are welcome.

If Speaker Sidekick gives you ideas for your own reusable agent skills, feel free to:

- Star the repository
- Fork the project
- Adapt the skill
- Submit an issue
- Share what you build