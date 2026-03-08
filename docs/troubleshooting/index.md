---
sidebar_position: 1
---

# Troubleshooting

This section lists common issues when setting up and running **Hello Doctor** (Flutter + Firebase + payments + video call).

## Flutter / build issues

- **`flutter doctor` shows missing dependencies**
  - Re-check the prerequisite steps in the *Before Start* docs.
  - Ensure Android Studio + SDK are installed and an emulator/device is detected.

- **Android build fails after changing package name**
  - Re-run the Firebase setup steps to ensure the new Android package name matches your Firebase app.

## Firebase issues

- **App can’t connect to Firebase (Android/iOS)**
  - Confirm you downloaded the correct Firebase config files for each platform.
  - Verify that the Firebase project matches the app flavor/bundle you’re running.

- **Firestore/Authentication features not working**
  - Ensure the required Firebase products are enabled in the console (Auth, Firestore, Functions, etc.).

## Payment gateway issues

- **Stripe / Paystack / Razorpay / Flutterwave checkout fails**
  - Double-check you are using the correct keys (test vs live) and that they’re placed in the right config locations.
  - For webhook/server-side steps, confirm the endpoint URLs and secrets match exactly.

## Video call issues

- **Video call can’t join / token error**
  - Confirm the provider keys are configured (e.g., Agora/100ms depending on your setup).
  - Verify the provider dashboard settings (roles, templates, webhook/token rules).

## Web admin issues

- **Web admin dashboard shows empty data**
  - Confirm you deployed/connected the correct Firebase project.
  - Verify Firestore rules/permissions allow the admin user to read the required collections.

## Where to look next

- Firebase setup: see the docs under *Setup Firebase*.
- Payments: see the docs under *Payment Gateway*.
- Video call provider: see the docs under *Setup Video Call Provider*.

## Contact us

If you face any issue that is not covered here, contact us and we will help you.
