# HardwareFix AI

A React + TypeScript + Vite application with Firebase Authentication and a Netlify serverless Gemini troubleshooting proxy.

## Requirements
- Node.js 20 or newer
- npm

## Run locally
1. Extract the ZIP.
2. Open a terminal in the project folder.
3. Run `npm install`.
4. Run `npm run dev`.
5. Open the local URL printed by Vite.

The application includes built-in fallback troubleshooting guidance when the Gemini function is not configured. To use live Gemini AI locally, run with Netlify Dev (`npx netlify dev`) after setting `GEMINI_API_KEY` in a local `.env` file. Do not commit `.env`.

## Deploy to Netlify
1. Push this folder to a GitHub repository.
2. Import the repository into Netlify.
3. Build command: `npm run build`.
4. Publish directory: `dist`.
5. Functions directory: `netlify/functions` (already set in `netlify.toml`).
6. In Netlify Site configuration > Environment variables, add `GEMINI_API_KEY` with your own Google AI Studio API key.
7. Deploy the site.

## Firebase Authentication
The original app's Firebase web configuration is retained in `src/App.tsx`. Firebase web config is intended to be public, but secure the project with Firebase Authentication authorized domains, appropriate provider settings, and security rules. The original project configuration may need to be replaced with your own Firebase project's web app configuration if you do not control that Firebase project.

## Important integration status
- Firebase Authentication: configured using the Firebase project settings present in the supplied source; verify ownership and authorized domains before production.
- Gemini: server-side proxy included; requires your own `GEMINI_API_KEY` environment variable.
- Payments, subscription checkout, persistent cloud database, and admin backend are not included as completed integrations in the supplied source. Do not advertise them as live until implemented and tested.
- Some device readings are browser-limited estimates or optional APIs; the website cannot inspect all physical hardware from a normal browser.

## Security note
The supplied source contained a hard-coded credential-like Gemini key. It has been removed from the browser code and is not included in this ZIP. If that credential was real or active, revoke/rotate it with its provider. Configure your replacement only as a server-side Netlify environment variable.
