# Sprout

Documentation repository for **Sprout** — an adaptive learning platform with a real-time multimodal conversational tutor (voice, text, webcam, and screen sharing). This repo contains the internship technical report and related materials describing the production AI subsystem (Gemini Proxy gateway, Firestore schema, TypeScript SDK, and operations).

Application source code lives in separate repositories; here you edit and build the LaTeX report only.

**Internship report:** *Sprout Conversational AI System* (English LaTeX)  
**Student:** Nguyen Thanh Minh Duc (2470734) · **Advisor:** Quản Thành Thơ · **Reviewer:** Trương Quang Khải

## Repository layout

```
sprout/
├── sprout.code-workspace      # VS Code / Cursor workspace (LaTeX Workshop)
├── docs/
│   ├── README.md              # Docs index and chapter overview
│   ├── report/
│   │   ├── source/            # LaTeX source (main.tex, sections/, Makefile)
│   │   └── exports/           # Published PDFs
│   ├── reviews/               # Reviewer feedback
│   └── reference/
│       └── thesis-templates/  # Formatting reference (not Sprout content)
└── README.md
```

## System overview (from the report)

The documented AI stack includes:

- **Gemini Proxy** — JWT-validated WebSocket gateway on Cloud Run, forwarding clients to Google Gemini Live API  
- **Data** — Firestore collections (`users`, `courses`, `lessons`, `conversations`, `messages`, `gemini_sessions`)  
- **Client** — `@abyxolv/gemini-proxy-sdk` (TypeScript) for WebSocket, JWT refresh, and audio framing  
- **Async work** — Knowledge-map generation via Cloud Tasks; lesson completion and feedback triggers  

See the [abstract](docs/report/source/sections/abstract.tex) and [introduction](docs/report/source/sections/ch01-introduction.tex) for full scope. Chapter list and `docs/` paths: [`docs/README.md`](docs/README.md).

## Getting started

### Open the workspace

```bash
cursor sprout.code-workspace
# or: code sprout.code-workspace
```

Recommended extensions (prompted by the workspace): **LaTeX Workshop**, **LTeX** (optional grammar).

### Build the report

**Requirements:** XeLaTeX + BibTeX (BasicTeX is sufficient), Times New Roman (system font).

On macOS, install BasicTeX once:

```bash
brew install --cask basictex
eval "$(/usr/libexec/path_helper)"
```

**First-time TeX packages** (after BasicTeX):

```bash
eval "$(/usr/libexec/path_helper)"
sudo tlmgr update --self
sudo tlmgr install biblatex logreq biber eso-pic pgf fancyhdr titlesec algorithms algorithmicx listings caption tools booktabs microtype multirow anyfontsize float
```

Without `sudo`, use user-mode install:

```bash
tlmgr init-usertree
tlmgr install --usermode biblatex logreq eso-pic pgf fancyhdr titlesec algorithms algorithmicx listings caption tools booktabs microtype multirow anyfontsize float
```

Bibliography uses **BibTeX** (not Biber), so a system `biber` binary is not required.

**Compile** (from repo root):

```bash
eval "$(/usr/libexec/path_helper)"
cd docs/report/source
make pdf
```

Output: `docs/report/source/main.pdf` (gitignored; regenerate locally). LaTeX Workshop uses the same recipe via `sprout.code-workspace`.

**Notes**

- Times New Roman is set via `fontspec` only (`tgtermes` is not used).
- Overfull hbox warnings on long `\texttt{...}` URLs are cosmetic and do not block the build.

### Read without building

- [`docs/report/exports/sprout-internship-final-report.pdf`](docs/report/exports/sprout-internship-final-report.pdf) — final exported report  
- [`docs/reviews/internship-report-review.pdf`](docs/reviews/internship-report-review.pdf) — reviewer feedback  

## License

Not specified in this repository. Add a `LICENSE` file if you intend to publish or share beyond academic submission.
