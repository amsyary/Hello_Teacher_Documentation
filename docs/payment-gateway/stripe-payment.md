---
sidebar_position: 1
sidebar_label: Stripe
---

# Stripe Payment Gateway

A payment gateway is a merchant service that authorizes card or bank payments for an app. In **Hallo Teacher**, the payment gateway is used when a user places an order for a teacher’s timeslot.

This guide explains how to set up **Stripe payments** and the required **Stripe webhook**.

## Prerequisites

- A Stripe account: https://stripe.com/
- Firebase Cloud Functions already set up and deployed from `/Halo_Teacher_Cloud_Function_Firebase`

## 1) Get your Stripe API keys

1. Open the Stripe Dashboard (Test mode): https://dashboard.stripe.com/test/dashboard
2. Copy the **Publishable key** (`pk_test_...`) and the **Secret key** (`sk_test_...`).

![Flutter Teacher](./assets/stripe_key.png)

### Add Publishable key to the Flutter client

Paste your Stripe publishable key into the Flutter project `.env` file in `/Hallo_Teacher_Client_Firebase`:

```dotenv title="/.env"
# Stripe
STRIPE_PUBLISHABLE_KEY=pk_test_your_publishable_key_here
```

### Add Secret key to Firebase Cloud Functions

:::info
Stripe **Secret key** must be available in Firebase Cloud Functions so the server can create/verify payments.
:::

#### If your Hallo Teacher version is >= `1.1.1`

Add your Stripe secret key to the Cloud Functions `.env`:

```dotenv title="/Halo_Teacher_Cloud_Function_Firebase/.env"
# Stripe
STRIPE_SECRET_KEY=sk_test_your_secret_key_here
```

Deploy your functions after updating env:

```powershell
firebase deploy
```

#### If your Hallo Teacher version is <= `1.0.19`

Set the functions config value (replace with your secret key):

```powershell
firebase functions:config:set stripe.token="sk_test_your_secret_key_here"
```

Deploy:

```powershell
firebase deploy
```

## 2) Create a Stripe webhook endpoint

After your Cloud Functions are deployed, configure a Stripe webhook so Stripe can notify your Firebase server when a payment succeeds (so the app can update the order status to `success`).

### Get your webhook URL from Firebase

1. Open **Firebase Console** → your project → **Functions**
2. Copy the URL shown for the `stripeWebhook` function.

![Flutter Teacher](./assets/firebase.PNG)

### Add the endpoint in Stripe Dashboard

1. Open Stripe Dashboard: https://dashboard.stripe.com/
2. Go to **Developers** → **Webhooks**
3. Click **Add endpoint**
4. Paste the `stripeWebhook` URL into **Endpoint URL**

![Flutter Teacher](./assets/stripe.PNG)

5. Click **Select events**

![Flutter Teacher](./assets/stripe2.PNG)

6. Search and enable **`payment_intent.succeeded`**
7. Click **Add events** → **Add endpoint**

![Flutter Teacher](./assets/stripe3.PNG)

### Copy the webhook signing secret

Open the webhook you just created and copy the **Signing secret** (`whsec_...`).

![Flutter Teacher](./assets/stripe4.PNG)

## 3) Add Stripe webhook secret to Firebase Cloud Functions

#### If your Hallo Teacher version is >= `1.1.1`

Add your webhook secret to the Cloud Functions `.env`:

```dotenv title="/Halo_Teacher_Cloud_Function_Firebase/.env"
# Stripe
STRIPE_WEBHOOK_SECRET=whsec_your_webhook_signing_secret_here
```

Deploy:

```powershell
firebase deploy
```

#### If your Hallo Teacher version is <= `1.0.19`

Set the functions config value (replace with your webhook secret):

```powershell
firebase functions:config:set stripe.webhook_secret="whsec_your_webhook_signing_secret_here"
```

Deploy:

```powershell
firebase deploy
```

## Notes on using a different payment gateway

If you want to use a different payment gateway provider, the main integration point is:

- `lib/app/service/payment_service.dart`

You’ll also need a matching server-side implementation in `/Halo_Teacher_Cloud_Function_Firebase` to create/verify payments and to receive webhook notifications.
