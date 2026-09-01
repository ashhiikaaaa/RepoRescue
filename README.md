<div align="center">

# 🛡️ RepoRescue

### Know the code before it moves.

**An agentic repository intelligence platform that connects code, tests, dependencies and Git history to help developers investigate a repository before making changes.**

![Status](https://img.shields.io/badge/status-interactive%20prototype-159570?style=for-the-badge)
![Basic Scan](https://img.shields.io/badge/basic%20scan-live-159570?style=for-the-badge)
![x402](https://img.shields.io/badge/x402-UI%20simulation-F2B832?style=for-the-badge)
![License](https://img.shields.io/badge/license-MIT-25332F?style=for-the-badge)

</div>

---

## What is RepoRescue?

Developers often enter an unfamiliar repository without knowing which files change frequently, which modules depend on one another, where tests exist or what could be affected by a modification.

RepoRescue brings these signals together in one investigation workspace.

Instead of producing a vague repository health score, RepoRescue presents **evidence-backed observations** and explains why an area may deserve attention.

> A frequently changed file is not automatically a problem. It becomes meaningful when combined with evidence such as high complexity, broad dependency reach, corrective commits or weak test protection.

---

## ✨ Current Prototype Features

### Dedicated homepage

The application begins with two clearly separated options:

- **Explore Demo** — opens a seeded repository investigation without making an API request.
- **GitHub URL** — performs a lightweight live scan of an accessible public GitHub repository.

The dashboard never opens directly, and repository URLs can only be entered from the homepage.

### Live Basic Scan

Basic Scan uses the public GitHub API to retrieve real repository information:

- Repository name, default branch and primary language
- Recursive repository file tree
- Source files across multiple programming languages
- Likely test files based on paths and naming conventions
- Common dependency manifests and lockfiles
- Large source-file observations
- Latest 30 commits and recent-author patterns

After scanning, the selected repository URL is shown inside the workspace as a **read-only reference**.

### Demo Workspace

The seeded Demo Workspace allows anyone to explore RepoRescue without supplying a repository. It includes:

- Connected repository findings
- Evidence Engine explanations
- Agent tool-selection plan
- File-level Change Impact Intelligence
- Test and dependency observations
- Recent investigation activity
- Simulated x402 payment experience

The demo intentionally avoids generic scores and pie/donut charts. Findings are communicated through readable evidence and file-level context.

### Evidence Engine

The Evidence Engine connects multiple signals before presenting a finding.

```text
Git history ───────┐
Static analysis ───┤
Dependency reach ──┼──> Connected finding ──> Suggested investigation
Test relationships ┤
Corrective commits ┘
```

Example:

```text
Checkout service is a change hotspot

Evidence:
• 23 edits in the recent history window
• Complexity concentrated in checkout processing
• 9 dependent modules
• 6 corrective or revert commits
```

### Change Impact Intelligence

Before editing a file, RepoRescue can surface:

- Direct dependents
- Related tests
- Historically coupled files
- Previous corrective patterns
- Areas worth reviewing together

Live Basic Scan currently provides lightweight file facts and name-matched tests. Deeper dependency and coupling analysis is represented through the seeded demo and remains part of the planned analysis backend.

---

## 🔄 Application Flow

```text
Homepage
   │
   ├── Explore Demo
   │      └── Seeded Demo Workspace
   │
   └── GitHub URL
          └── Live Basic Scan
                 └── Repository Workspace
                        ├── Overview
                        ├── Evidence Engine
                        ├── Change Impact
                        └── Agent Activity
```

Users can return to the homepage at any time using **Back to home** in the workspace sidebar.

---

## 🤖 Agentic Deep Investigation

The intended deep-analysis workflow is not a fixed pipeline that blindly runs every tool.

The RepoRescue agent first inspects the repository and selects only relevant analysis tools:

| Repository signal | Agent decision |
|---|---|
| Python source detected | Select Python static analysis |
| Rich commit history available | Select history and change-coupling analysis |
| Tests detected | Select test-impact mapping |
| Dependency manifests detected | Select dependency-graph analysis |
| No tests found | Skip test execution and report the limitation |

The results are then connected by the Evidence Engine.

---

## 💳 x402 and Algorand Vision

Deep Investigation is designed as an x402-protected computational service:

```text
Deep Investigation requested
          ↓
x402 payment requirement
          ↓
GoPlausible Facilitator
          ↓
Algorand LoRA Testnet transaction
          ↓
Payment verification
          ↓
Agentic repository investigation
```

### Current implementation status

The present prototype includes the payment **user-interface flow**, but it does not submit a real blockchain transaction.

The final integration still requires:

- An x402-protected backend endpoint
- Genuine `@x402-avm` integration
- GoPlausible Facilitator communication
- Wallet/payment authorization
- A verified LoRA Algorand Testnet transaction
- Backend authorization before Deep Investigation begins

---

## 🧰 Technology Used

| Area | Technology |
|---|---|
| Interface | HTML5, CSS3 and JavaScript |
| Development server | Vite |
| Repository data | GitHub REST API |
| Icons | Lucide |
| Deployment | Static hosting or GitHub Pages |
| Planned payment layer | x402, `@x402-avm`, GoPlausible and Algorand |

---

## 🚀 Run Locally

```bash
git clone https://github.com/YOUR_USERNAME/RepoRescue.git
cd RepoRescue
npm install
npm run dev
```

Open the local URL displayed by Vite, normally:

```text
http://localhost:5173
```

The prototype can also be opened directly through `index.html`.

---

## 📁 Project Structure

```text
repo-rescue-dashboard/
├── index.html       # Homepage, workspace, styles and interactions
├── package.json     # Vite scripts and project metadata
├── README.md        # Project documentation
├── .gitignore       # Ignored local and generated files
└── LICENSE          # MIT License
```

---

## 🌐 Using Live Basic Scan

1. Open RepoRescue.
2. Select **GitHub URL** on the homepage.
3. Paste an accessible public repository URL:

```text
https://github.com/owner/repository
```

4. Select **Analyze public repository**.
5. Wait for GitHub data to be retrieved.
6. Explore the generated observations and files.

### Basic Scan limitations

- Only accessible public repositories are supported.
- GitHub's unauthenticated API limit applies, normally 60 requests per hour per IP address.
- Very large repositories may return a truncated file tree.
- Test detection uses paths and filenames; tests are not executed.
- Dependency manifests are detected, but package versions and vulnerabilities are not analysed.
- Recent activity uses only the latest 30 commits returned by GitHub.
- Full complexity, dependency, ownership and historical-coupling analysis requires the planned backend.

---

## 🗺️ Roadmap

- [x] Dedicated homepage with Demo and GitHub URL modes
- [x] Seeded Demo Workspace
- [x] Live public GitHub Basic Scan
- [x] Multi-language source-file detection
- [x] Test-file and dependency-manifest detection
- [x] Evidence Engine interface
- [x] File-level Change Impact interface
- [x] Simulated x402 payment experience
- [ ] Backend repository cloning and isolated analysis
- [ ] Real static-analysis tool execution
- [ ] Dependency and circular-dependency graphs
- [ ] Git co-change and corrective-commit analysis
- [ ] Test execution and test-to-source mapping
- [ ] Agentic tool selection and orchestration
- [ ] Genuine x402 and `@x402-avm` integration
- [ ] GoPlausible Facilitator integration
- [ ] Verified Algorand LoRA Testnet transaction

---

## 🔐 Privacy and Safety

The current Basic Scan reads public repository metadata through GitHub's public API. It does not request GitHub credentials, modify repositories or push code.

Future backend analysis should clone repositories into isolated temporary environments and must not execute untrusted repository code without appropriate sandboxing.

---

## 📄 License

This project is available under the [MIT License](LICENSE).

---

<div align="center">

**RepoRescue — investigate first, change with evidence.**

</div>
