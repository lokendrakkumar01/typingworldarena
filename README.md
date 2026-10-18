# TYPEARENA PRO

A static React typing practice and local competition app. It runs entirely in the browser and is deployable as a Render Static Site.

## Features

- Typing tests with 15, 30, 60, or 120 second duration, four difficulty levels, and seven passage categories.
- Character level feedback, live timer, progress, gross/net WPM, accuracy, and errors.
- Four sequential local competition rounds with qualification thresholds.
- Practice race against simulated computer players.
- Dashboard, local analytics, local leaderboard with clearly marked sample entries, profile, settings, and achievements.
- Namespaced, versioned local storage; CSV and JSON export; history and all-data reset.
- Responsive dark/light layouts, reduced-motion support, and client-side routing.

## Technology

React, Vite, JavaScript, React Router, Framer Motion (available for animation extensions), Lucide React, and Recharts (available for chart extensions). No backend, API keys, database, authentication, or online multiplayer service is used.

## Local setup

Requires Node.js and npm.

```sh
npm install
npm run dev
```

Create a production bundle with `npm run build`; preview it locally with `npm run preview`.

## Deployment to GitHub and Render

1. Create a GitHub repository and push this project, including `package.json`, `public/`, `src/`, `index.html`, and `vite.config.js`.
2. In Render, create a **Static Site** and connect the repository.
3. Set the build command to `npm install && npm run build`.
4. Set the publish directory to `dist`.
5. Deploy. The `public/_redirects` file is copied to the published root and provides the SPA fallback (`/* /index.html 200`). Do not add a separate conflicting rewrite rule.

There is no server start command. The output in `dist/` is the complete deployable app. Vite serves the app from the site root; React Router handles unknown routes with the custom 404 screen after the host fallback serves `index.html`.

## Metrics

- Gross WPM = all typed characters ÷ 5 ÷ elapsed minutes.
- Net WPM = correctly matched typed characters ÷ 5 ÷ elapsed minutes.
- Accuracy = correctly matched typed characters ÷ all typed characters × 100; an empty test displays 100%.
- Errors = typed characters that do not match the corresponding passage character.
- The timer starts on the first keystroke. A minimum 1 ms denominator prevents division by zero. Results are submitted once per run.

## Known limitations

This is local browser play. Profile, settings, achievements, competition, and typing history are not synchronized to other users, browsers, or devices. Browser storage clearing can remove progress. Leaderboard example entries are sample data, not live participants. Practice race opponents are simulated; real online multiplayer requires a separate real-time service. The competition uses local qualification thresholds and is not an audited tournament.
