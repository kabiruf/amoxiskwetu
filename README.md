# AmoxiSkwetu — Local Development README

This README contains minimal setup and verification steps to get the project running locally on Windows (PowerShell). It assumes you have already copied `.env.example` to `.env.local` and filled in your Firebase values.

1) Install Node.js (required)
- Install Node.js LTS (recommended) from https://nodejs.org/ and ensure `npm` is on your PATH.
- If you prefer version management, use nvm for Windows (https://github.com/coreybutler/nvm-windows).

2) Copy env example
 - Copy `.env.example` to `.env.local` in the project root and fill in real Firebase values:

```powershell
cp .env.example .env.local
# then edit .env.local in an editor and paste your keys
```

3) Install dependencies
 - From the project root (PowerShell):

```powershell
npm install
```

4) Typecheck and lint (optional but recommended)

```powershell
npx tsc --noEmit
npx eslint . --ext .ts,.tsx
```

5) Start development server

```powershell
npm run dev
```

6) Verify core flows
- Open the app in your browser (default Next.js: `http://localhost:3000`).
- Verify: Sign up / Login (Google and email/password), Create a property (`/properties/submit`), Create notes (`/notes`), Trigger SOS and check Firestore `emergency_alerts`.
- Check the browser console and network tab for Firebase errors.

7) Claims and roles
- If server-side custom claims are modified, call `await refreshClaims()` from the `useAuth()` context (client) and reload the UI to see updated role checks. See `context/AuthContext`.

8) Helpful files
- Agent guidance: `.github/copilot-instructions.md`
- Firebase config helper: `lib/firebase.ts` (exports `auth`, `db`, `storage`)
- Env example: `.env.example`
- PR checklist: `.github/PULL_REQUEST_TEMPLATE.md`

9) Troubleshooting: `npm` not recognized
- If PowerShell reports `npm` is not recognized, Node.js was not installed or PATH is not updated. Reinstall Node or restart your shell after install.

10) Next actions you can ask me to do
- Add an `.github/ISSUE_TEMPLATE.md` or expand `copilot-instructions.md` with more code snippets.
- Prepare a PR branch with these changes.

If you want, I can also produce a small `package.json` scripts block template (dev/build/type-check/lint) to paste into your existing `package.json`.
