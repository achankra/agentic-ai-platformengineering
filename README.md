***** DO NOT USE THIS REPO. THIS WAS ONLY INTENDED FOR THE JANUARY 2026 COURSE *****

Please use the latest [repo](https://github.com/achankra/agentic-pe-oreilly)

# Agentic AI in Platform Engineering

Interactive demos showcasing how AI agents can solve platform engineering challenges using Claude API and Python used in the Agentic AI in Platform Engineering Course

## Overview

This course and repository focus specifically on **agentic patterns**—AI that reasons, plans, and acts. We intentionally skip some topics that are well-covered elsewhere or still too nascent:

### What Do We Cover?

- Diagnostic agents that investigate incidents
- Release readiness agents that assess risk and make recommendations
- Multi-agent coordination and conflict resolution
- Developer portal agents for personalized onboarding
- Progressive autonomy patterns and guardrail design
- Production-ready code you can deploy Monday morning


### Demos

This project demonstrates four AI agent patterns for platform engineering:

1. **Workflow Diagnostic Agent** - Automatically diagnoses failed CI/CD workflows and provides root cause analysis with suggested fixes
2. **Release Readiness Agent** - Evaluates quality gates to make intelligent release/rollback decisions with confidence scores
3. **Multi-Agent Orchestration** - Cost optimizer and incident responder agents coordinate to balance efficiency with reliability
4. **Developer Portal Agent** - AI-driven onboarding and self-service endpoint for intelligent developer guidance

### What's not covered?


| Topic | Why It's Not Included |
|-------|----------------------|
| **RAG (Retrieval-Augmented Generation)** | Table stakes at this point. Every vendor has it, documentation is abundant, and it's not where the interesting platform engineering problems are anymore. |
| **MCP Servers** | Promising protocol, but patterns aren't stable enough to teach as best practice yet. We'll revisit when the ecosystem matures. |
| **Fully Autonomous Operations** | We focus on *scaffolding*—the trust infrastructure, guardrails, and feedback mechanisms that make autonomy possible later. Organizations that skip straight to autonomous systems fail. Trust is earned incrementally. |
| **Replacing Platform Engineers** | Research consistently shows hybrid human-AI approaches outperform both fully manual and fully autonomous systems. Our demos emphasize AI that augments human judgment, not replaces it. |



##  Learning Resources

- [O'Reilly/Pearson Course Site](https://www.oreilly.com/live-events/agentic-ai-in-platform-engineering/0642572268862/)
- [Effective Platform Engineering Book](https://effectiveplatformengineering.com)
- [Online Demos](https://agentic-pe.platformetrics.com)
- [Alternate Python CLI versions](https://github.com/achankra/agentic-ai-platformengineering/tree/main/python)


## Tech Stack

- **Frontend**: React, TypeScript, Vite, Tailwind CSS
- **UI Components**: shadcn/ui
- **Backend Functions**: Supabase Edge Functions (Deno)
- **AI Integration**: Claude API (Anthropic)

## Getting Started

### Prerequisites

- Node.js 18+ and npm
- An Anthropic API key for Claude

### Installation

```sh
# Clone the repository
git clone <YOUR_GIT_URL>

# Navigate to the project directory
cd <YOUR_PROJECT_NAME>

# Install dependencies
npm install

# Start the development server
npm run dev
```

### Environment Variables

Create a `.env` file with:

```
ANTHROPIC_API_KEY=your_api_key_here
```


## Repository Directory Structure

```
agentic-ai-platformengineering/
├── public/                          # Frontend static assets (Vite)
├── src/                             # Frontend source (React/TS)
├── supabase/   
    ├── functions/                   # Edge functions for AI agents
        ├── workflow-diagnostic/
        ├── release-readiness/
        ├── multi-agent/
        └── developer-portal/
├── README.md
├── SETUP.md
├── components.json
├── eslint.config.js
├── index.html
├── package.json
├── tsconfig.app.json
└── python/                          # Course Python demos & exercises (Alternative to Vite/React/TS. Not mandatory)
    ├── ai_client.py
    ├── exercises/
    │   ├── ai_client.py
    │   ├── ex1_diagnostic_agent.py
    │   ├── ex2_quality_gates.py
    │   ├── ex3_multi_agent.py
    │   ├── ex4_developer_portal.py
    │   └── ex5_starter_kit.py
    ├── logs/
    │   └── sample.log
    ├── outputs/
    │   ├── diagnostics/
    │   │   └── diagnostic_20251114_205321.json
    │   └── quality-gates/
    │       └── decision_20251222_173144.json
    ├── README.md
    ├── requirements.txt
    └── setup.py
```

## Demo Features

- **Live Execution**: Run AI agents in real-time
- **Formatted Output**: Toggle between raw and formatted markdown output
- **Workflow Diagrams**: Visual representation of agent decision flows
- **Source Code**: View the Python implementation for each agent

## Deployment

The application can be deployed to any static hosting platform:


The build output will be in the `dist` directory.


### Deploy to GitHub Pages

*Start with deployment helper*

```
npm install --save-dev gh-pages

```

*Then update the package.json file*
```
{
  "homepage": "https://achankra.github.io/agentic-ai-platformengineering",
  "scripts": {
    "build": "vite build",
    "deploy": "gh-pages -d dist"
  }
}
```
*and update the vite.config.ts file*
```
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react-swc";
import path from "path";
import { componentTagger } from "lovable-tagger";

export default defineConfig(({ mode }) => ({
  base: "/agentic-ai-platformengineering/", 
  server: {
    host: "::",
    port: 8080,
  },
  plugins: [react(), mode === "development" && componentTagger()].filter(Boolean),
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
}));

```

*Deploy*

```
npm install
npm install -D gh-pages
npm run build # creates the dist/ folder
npm run deploy

```

*Look for the following URL (Obviously replace the subdomain with whatever appropriate)*
https://achankra.github.io/agentic-ai-platformengineering

## Tech Overview

This project demonstrates agentic AI patterns using a deliberately simple stack—no heavy frameworks, no complex orchestration layers. The goal is clarity: you should be able to read the code and understand exactly what's happening.

### Architecture
```
┌─────────────────────────────────────────────────────────────────┐
│                        Frontend (UI)                            │
│                 React + TypeScript + Vite│
│                  Hosted on GitHub Pages                         │
└─────────────────────────┬───────────────────────────────────────┘
                          │ HTTPS API calls
                          ▼
┌─────────────────────────────────────────────────────────────────┐
│                   Supabase Edge Functions                       │
│              (Deno runtime, TypeScript)                         │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌───────────┐  │
│  │ Diagnostic  │ │  Release    │ │ Multi-Agent │ │ Developer │  │
│  │   Agent     │ │  Readiness  │ │Coordination │ │  Portal   │  │
│  └──────┬──────┘ └──────┬──────┘ └──────┬──────┘ └─────┬─────┘  │
└─────────┼───────────────┼───────────────┼─────────────┼─────────┘
          │               │               │             │
          └───────────────┴───────┬───────┴─────────────┘
                                  ▼
                    ┌─────────────────────────┐
                    │      Claude API         │
                    │   (Anthropic Claude     │
                    │    Sonnet 4)            │
                    └─────────────────────────┘
```

### Component Breakdown

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Frontend** | [Lovable](https://lovable.dev) | AI-generated React UI with shadcn/ui components. Rapid prototyping without hand-coding every component. |
| **UI Framework** | React 18 + TypeScript | Type-safe frontend with modern hooks |
| **Styling** | Tailwind CSS + shadcn/ui | Utility-first CSS with accessible component primitives |
| **Build Tool** | Vite | Fast dev server and optimized production builds |
| **Backend Functions** | Supabase Edge Functions | Serverless Deno runtime for API endpoints. Handles auth, secrets, and CORS without infrastructure management. |
| **AI Provider** | Claude API (Anthropic) | Direct API calls to `claude-sonnet-4-20250514`. No LangChain, no abstraction layers—just prompts and responses. |
| **Alternative Runtime** | Python 3.11+ | Standalone CLI implementations of each agent for local execution and workshops |
| **Hosting** | GitHub Pages | Static site hosting for the frontend (free, simple, no server) |

### Why No Agent Framework?

You'll notice we're not using LangChain, LlamaIndex, CrewAI, or similar frameworks. This is intentional:

- **Transparency** — You can read the prompt, see the API call, understand the response parsing. No magic.
- **Fewer dependencies** — Less to break, fewer security surfaces, easier to audit.
- **Learning-focused** — Frameworks abstract away the patterns we're trying to teach.
- **Production-realistic** — Many production agent deployments use direct API calls for control and observability.

The tradeoff is more boilerplate. 

### Supabase Edge Functions

Each agent is a standalone Edge Function in the `supabase/functions/` directory:
```
supabase/functions/
├── workflow-diagnostic/index.ts    # Analyzes CI/CD failures
├── release-readiness/index.ts      # Evaluates quality gates
├── multi-agent/index.ts            # Cost optimizer + incident responder
└── developer-portal/index.ts       # Personalized onboarding
```

**Why Supabase?**
- Free tier handles traffic easily. Can be scaled to production effectively
- Secrets management (API keys never touch the frontend)
- 'Deno' runtime = TypeScript with no build step
- Deploys in seconds: `supabase functions deploy`

### Python Implementations

The `python/` directory contains equivalent implementations for each agent:
```
python/
├── ai_client.py                    # Multi-provider client (Claude, OpenAI, mock)
├── exercises/
│   ├── ex1_diagnostic_agent.py     # Workflow diagnostics
│   ├── ex2_quality_gates.py        # Release readiness
│   ├── ex3_multi_agent.py          # Multi-agent coordination
│   ├── ex4_developer_portal.py     # Developer onboarding
│   └── ex5_starter_kit.py          # Template generator
└── requirements.txt
```

**Why both TypeScript and Python?**
- TypeScript: Production-style deployment via Supabase
- Python: Workshop exercises, local experimentation, familiar to most platform engineers

Both implementations use the same prompts and patterns—just different runtimes.

### Lovable (Frontend Generation)

The React frontend was generated using [Lovable](https://lovable.dev), the popular AI-powered app builder. This enabled rapid iteration on the demo UI without hand-coding every component.

**What Lovable provided:**
- Initial React + Vite + Tailwind scaffold
- shadcn/ui component integration
- Responsive layout and dark mode
- Workflow visualization components

**What we customized:**
- Typescript / Python agents
- Supabase function integration
- Demo-specific flows and state management
- GitHub Pages deployment configuration

This approach mirrors real platform engineering: use AI to accelerate the undifferentiated work, focus human effort on the parts that matter.

### Local Development
```bash
# Frontend
npm install
npm run dev                    # Runs at localhost:8080

# Supabase Functions (local)
supabase start
supabase functions serve       # Local function emulator

# Python exercises
cd python
pip install -r requirements.txt
python exercises/ex1_diagnostic_agent.py
```

### Environment Variables

| Variable | Where | Purpose |
|----------|-------|---------|
| `ANTHROPIC_API_KEY` | Supabase secrets / local `.env` | Claude API authentication |
| `DEMO_ACCESS_PASSWORD` | Supabase secrets | Optional gate for live demos |
| `SUPABASE_URL` | Frontend `.env` | Edge function endpoint |
| `SUPABASE_ANON_KEY` | Frontend `.env` | Public API key for Supabase |

## License

MIT
