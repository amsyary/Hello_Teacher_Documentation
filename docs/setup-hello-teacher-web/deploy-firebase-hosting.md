---
sidebar_position: 5
sidebar_label: Deploy to Firebase Hosting
---

# Deploy to Firebase Hosting

After you have the Hello Teacher Web app running locally, you can deploy it to Firebase Hosting so it is available on the web. This page walks you through building the React app and publishing it to Firebase.

## Prerequisites

Before starting, you need:

- Firebase CLI installed and logged in. If you have not done this yet, run:

```bash
npm install -g firebase-tools
```

Then log in:

```bash
firebase login
```

- The Hello Teacher Web project set up with dependencies installed (`npm install` already run) and environment configured (`.env` with Firebase credentials).

## Step 1: Build the project

Open a terminal in the **root** of the Hello Teacher Web project and create a production build:

```bash
npm run build
```

The build output is usually written to a folder such as `dist` (Vite) or `build` (Create React App). Check your project’s `package.json` or build config to see which folder is used—you will need it for the next step.

:::info

If your project uses a different build command (e.g. `npm run build:prod`), run that instead. The important part is that you have a static output folder ready for hosting.

:::

## Step 2: Initialize Firebase Hosting

In the same project root, run:

```bash
firebase init
```

1. Use the arrow keys to select **Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub Action deploys**, then press Enter.
2. When asked to choose a Firebase project, select your existing **Hello Teacher** project.
3. When asked for the **public directory**, enter the folder where the build output was written:
   - If the build output is in `dist`, enter: `dist`
   - If the build output is in `build`, enter: `build`
4. When asked **Configure as a single-page app (rewrite all urls to /index.html)?**, choose **Yes** if your app is a client-side React app (recommended for most React setups).
5. If asked about overwriting files (e.g. `index.html`), choose **No** so your built app is not replaced.
6. Finish the prompts. Firebase will create (or update) `firebase.json` and `.firebaserc` in your project.

## Step 3: Deploy

Deploy the app to Firebase Hosting:

```bash
firebase deploy
```

When the deploy finishes, the terminal will show your **Hosting URL** (e.g. `https://your-project-id.web.app`). Open that URL in a browser to use the deployed Hello Teacher Web app.

## Next steps

- To redeploy after making changes, run `npm run build` again, then `firebase deploy`.
- You can set up a custom domain or GitHub Actions for automatic deploys from the [Firebase Console](https://console.firebase.google.com/) under your project’s Hosting settings.
