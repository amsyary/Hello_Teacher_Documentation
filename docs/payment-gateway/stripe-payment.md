---
sidebar_position: 1
sidebar_label: Setup Stripe Payment Gateway
---

# Payment Gateway

A payment gateway is a merchant service provided by an e-commerce application service provider that authorizes credit card or direct payments processing for e-businesses,
here we will use a payment gateway to provide payment services for users, when they are about to place an order for a Teacher's timeslot

## Stripe Payment Gateway

here we will use Stripe payment gateway, because Stripe is one of the largest payment gateways, and is widely used, but if you want to use another payment gateway, modifying the app will be very easy, just change `lib\app\service\payment_service.dart`, but here we will use Stripe payment gateway

- goto Stripe official site and register new account https://stripe.com/
- when Stripe asks you to activate your account, you can **activate it later**
- for now we only need a `Publishable key` and a `Secret key` you can get it here https://dashboard.stripe.com/test/dashboard
<<<<<<< HEAD

![Flutter Doctor](./assets/stripe_key.png)

- Copy Stripe `Publishable key` and paste it in `.env` file at `STRIPE_PUBLISHABLE_KEY=` in your `/Hallo_Teacher_Client_Firebase` flutter project
=======
>>>>>>> parent of 7ad62a1 (Add documentation for rebranding Hello Teacher app and payment gateways; include troubleshooting section)

your `.env` file should look like this

<<<<<<< HEAD
=======
- Copy Stripe `Publishable key` and paste it in `.env` file at `STRIPE_PUBLISHABLE_KEY=` in your `/Hallo_Teacher_Client_Firebase` flutter project

your `.env` file should look like this

>>>>>>> parent of 7ad62a1 (Add documentation for rebranding Hello Teacher app and payment gateways; include troubleshooting section)
```jsx title="/.env"
#Stripe Environment
STRIPE_PUBLISHABLE_KEY=sk_test_51HuXoBEwKn2CFnwUTqweh1Si9L0vG4zSbAbKm1OIhYLZA1R3ypELDXDCntEPJ9Y2nw62kwsKBn
```

for the Secret Key in Stripe Dashboard, we have to add it to the Firebase Cloud Function that we previously setup in folder `/Halo_Teacher_Cloud_Function_Firebase`

:::info
Stripe Secret Key must be added to the Firebase cloud Function, for verify payment
:::

## Add Stripe Key To Firebase Cloud

:::info
if your Hallo Teacher version is greater than or equal to `1.1.1` you just need to copy `Stripe secret key` to `.env` file at STRIPE_SECRET_KEY=put_your_stripe_key_here
and skip the next step in this page
:::

if your Hallo Teacher version is lower than or equal to `1.0.19` add the stripe cloud function with this step: 

- back to Firebase Cloud function folder `/Halo_Teacher_Cloud_Function_Firebase`
- open it with `CMD`
- run the command below, but change the key to your Stripe Secret Key

```
firebase functions:config:set stripe.token="sk_test_51HuXoBEwKn2CFnwUTqw8kKeh1Si9L0vG4zSbAbKm1OWpRfIhYLZA1R3ypELDXDCntE28PJ9w62kwsKBnuzHkszK"
```

- now we can deploy it using this command

```
firebase deploy
```
<<<<<<< HEAD

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

- now we can deploy it using this command

```
firebase deploy
```

## Notes on using a different payment gateway

If you want to use a different payment gateway provider, the main integration point is:

- `lib/app/service/payment_service.dart`

You’ll also need a matching server-side implementation in `/Halo_Teacher_Cloud_Function_Firebase` to create/verify payments and to receive webhook notifications.
=======
>>>>>>> parent of 7ad62a1 (Add documentation for rebranding Hello Teacher app and payment gateways; include troubleshooting section)
