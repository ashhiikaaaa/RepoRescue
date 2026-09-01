# RepoRescue Dashboard Prototype

RepoRescue is an agentic repository investigation platform that connects evidence from source code, Git history, dependencies, tests, and contributor activity. This repository contains the interactive frontend prototype.

## Included interactions

- Open on a dedicated landing page instead of directly entering the dashboard.
- Choose between **Explore demo** and **GitHub URL** before initializing a workspace.
- Launch a seeded **Demo Workspace** without entering a repository or calling GitHub.
- Return to the landing page using **Back to home** in the workspace sidebar.
- Display the active repository URL as a read-only reference inside the workspace.
- Switch between the demo workspace and live public-repository scans.
- Run a live basic scan for public GitHub repositories using the GitHub API.
- Read real repository metadata, recursive file trees, languages, and the latest 30 commits.
- Detect source files, likely test files, dependency manifests, large source files, and recent-author patterns.
- Browse evidence-backed repository findings.
- Inspect the individual signals behind each finding.
- Explore file-level change-impact information.
- Preview the x402 payment flow through GoPlausible and Algorand LoRA Testnet.
- Review the agent's tool-selection and investigation activity.
- Use the responsive light/dark interface on desktop or mobile.

The Demo Workspace deliberately uses evidence lists and file-level views instead of a pie or donut chart.
The Demo Workspace can only be launched from the homepage; it is not duplicated inside the repository overview or sidebar.
Repository URLs can only be entered or changed from the homepage's **GitHub URL** option. The workspace never contains an editable repository field or another Basic Scan action.

## Run locally

### Quickest option

Open `index.html` in a browser.

### Development server

```bash
npm install
npm run dev
```

Vite will print the local URL, usually `http://localhost:5173`.

## Build for deployment

```bash
npm run build
```

The production files will be written to `dist/`. The project can also be deployed directly to GitHub Pages as a static site.

## Important integration status

The app initially opens on the landing page. **Explore demo** loads realistic seeded data, while **GitHub URL** performs a live Basic Scan before opening the dashboard.

Basic Scan intentionally remains lightweight:

- It inspects public GitHub metadata and file paths without cloning the repository.
- Test detection uses common directory and filename patterns; it does not execute tests or calculate coverage.
- Dependency detection identifies common manifests but does not inspect package versions or vulnerabilities.
- Recent activity uses only the latest 30 commits returned by GitHub.
- GitHub's unauthenticated API rate limit applies, normally 60 requests per hour per IP address.

The displayed x402 payment action is intentionally a **frontend simulation** and does not create a blockchain transaction.

Before using this as the final hackathon submission, replace the simulated handler with:

1. An x402-protected deep-investigation endpoint.
2. Genuine `@x402-avm` integration.
3. Payment through the GoPlausible Facilitator.
4. Transaction submission and verification on LoRA Algorand Testnet.
5. A backend repository-analysis pipeline that returns real findings.

Do not describe this prototype as a complete x402 integration until those backend steps are implemented and verified.

## Current project structure

```text
repo-rescue-dashboard/
├── index.html       # Complete interactive dashboard prototype
├── package.json     # Local development and build scripts
├── .gitignore
├── LICENSE
└── README.md
```

## Suggested GitHub setup

```bash
git init
git add .
git commit -m "feat: add RepoRescue dashboard prototype"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/repo-rescue.git
git push -u origin main
```

## License

MIT
