---
sidebar_position: 3
sidebar_label: Setup environment (.env)
---

# Setup environment (.env)

The Hello Teacher Web project uses a `.env` file to store Firebase credentials and other secrets. You need to create this file from the example and fill it with the Firebase config you obtained in the previous step.

## Step 1: Open the Hello Teacher Web project

- Open your code editor (e.g. Visual Studio Code).
- Use **File → Open Folder** and select the **Hello Teacher Web** project folder (the one that contains `package.json` and the React app source).

## Step 2: Create the .env file

- In the **root** of the Hello Teacher Web project (same level as `package.json`), create a new file named `.env`.
- Open the existing `.env_example` file in the same folder and copy its entire contents into the new `.env` file.

:::info

If `.env` already exists (e.g. from a previous setup), open it and add or update the values as described below. Do not commit `.env` to version control—it should remain local and secret.

:::

## Step 3: Fill in Firebase credentials

In your `.env` file, fill in the placeholders with the Firebase configuration you received when you registered the web app:

- `apiKey`
- `authDomain`
- `projectId`
- `storageBucket`
- `messagingSenderId`
- `appId`

The exact variable names may match what is in `.env_example` (e.g. `VITE_FIREBASE_API_KEY`, `NEXT_PUBLIC_FIREBASE_API_KEY`, or similar, depending on the project). Use the same names as in `.env_example` and paste the corresponding values from the Firebase Console.

If `.env_example` includes other keys (e.g. Stripe, Agora), fill those in later when you configure those services.

Save the `.env` file. Next, install dependencies and run the app.
