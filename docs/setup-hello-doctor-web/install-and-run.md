---
sidebar_position: 4
sidebar_label: Install and run
---

# Install and run

After you have created the Firebase web app and set up your `.env` file with the Firebase credentials, install the project dependencies and run the Hello Doctor Web app locally.

## Step 1: Install dependencies

Open a terminal in the **root** of the Hello Doctor Web project (where `package.json` is located) and run:

```bash
npm install
```

or the short form:

```bash
npm i
```

Wait until all packages are installed. If you see any errors, check that Node.js and npm are installed and that you are in the correct folder.

## Step 2: Run the app

Start the development server with one of these commands (depending on how the project is set up):

```bash
npm run dev
```

or:

```bash
npm start
```

The terminal will show a local URL (e.g. `http://localhost:3000` or similar). Open that URL in your browser to use the Hello Doctor Web app.

## Next steps

- Sign in with the same Firebase Authentication used by the mobile app—users and sessions are shared.
- If you have not yet configured Stripe, Agora, or other services, refer to the relevant setup sections in this documentation and add the required keys to your `.env` when needed.
