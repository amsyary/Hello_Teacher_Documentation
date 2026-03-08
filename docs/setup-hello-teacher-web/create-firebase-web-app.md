---
sidebar_position: 2
sidebar_label: Create Firebase Web App
---

# Create Firebase Web App

After you have created a Firebase project (see **Setup Firebase**), you can add multiple apps to that project. Here we will create the Hello Teacher Web app so the web version can use the same Firebase backend as the mobile app.

## Add Hello Teacher Web app to your Firebase project

1. Open the [Firebase Console](https://console.firebase.google.com/) and select your existing Hello Teacher project.

2. On the project overview page, click the **Web** icon (the one with angle brackets) to add a new web app.

3. When prompted, enter the **App nickname**: `Hello Teacher Web` (or a name of your choice).

4. You can leave **Firebase Hosting** unchecked for now if you only need to run the app locally. Click **Register app**.

5. Firebase will show your **Firebase configuration** (a JavaScript object with `apiKey`, `authDomain`, `projectId`, `storageBucket`, `messagingSenderId`, `appId`). Copy this configuration—you will need it for the next step when setting up your `.env` file.

:::info

Keep your Firebase config (especially `apiKey`) in a `.env` file and do not commit it to version control. The next page explains how to set up the environment file.

:::

6. Click **Continue to console**. Your Hello Teacher Web app is now registered under the same Firebase project as your mobile app, so they share the same backend, authentication, and data.

Next, open the Hello Teacher Web project and configure the environment file with these credentials.
