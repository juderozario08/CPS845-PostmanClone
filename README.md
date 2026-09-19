# cps845groupproject
CPS 845 Group Project
# Postman Clone (CPS 845 Group Project)

A desktop Postman clone built with Electron and TypeScript for CPS 845.

---

## Prerequisites

Ensure you have the following installed on your machine:
- **[Node.js](https://nodejs.org/)** (v18 or higher recommended; v20+ / v24 verified)
- **npm** (bundled with Node.js)
- **Git**

---

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/juderozario08/cps845groupproject.git
cd cps845groupproject
```

### 2. Check out the Appropriate Branch
Refer to [RULES.md](RULES.md) for team branching policies. To start new feature work, ensure `dev` is up to date and cut a dedicated feature branch:
```bash
git checkout dev
git pull origin dev
git checkout -b feat-<your_name>-<what_you_worked_on>
```

### 3. Install Dependencies
Install required dependencies (Electron, TypeScript, Node type definitions):
```bash
npm install
```

---

## Available Scripts

In the project root, you can run:

### `npm start`
Builds the TypeScript source files and launches the Electron application.

### `npm run build`
Compiles all TypeScript files in `src/` to JavaScript in the `dist/` directory according to `tsconfig.json`.

### `npm run watch`
Runs the TypeScript compiler in watch mode (`tsc -w`), automatically recompiling whenever files in `src/` change.

---

## Project Structure

```
cps845groupproject/
├── dist/                 # Compiled JavaScript output (git-ignored)
├── node_modules/         # Installed npm packages (git-ignored)
├── src/
│   ├── index.html        # Main window HTML layout
│   └── main.ts           # Electron main process (window management, lifecycle)
├── .gitignore            # Git ignore configuration
├── package.json          # Project manifest, scripts, and dependencies
├── package-lock.json     # Dependency lockfile
├── README.md             # Project documentation and setup guide
├── RULES.md              # Team branching policies and PR guidelines
└── tsconfig.json         # TypeScript compiler configuration
```

---

## Development Guidelines

Please review [RULES.md](RULES.md) before contributing:
- Work must branch from and PR into `dev`.
- Follow the branch naming convention: `<type>-<your_name>-<what_you_worked_on>`.
- Merges into `main` occur only from `dev`.
