---
sidebar_position: 1

---

# Welcome

**First of all, thank you very much for purchasing this source code**.

Introducing the Hello Doctor application, a complete end-to-end solution for booking remote consultation sessions with doctors. Our user-friendly app enables users to easily find and book a session with their preferred doctor, and make secure payments directly to them. With our video call system, users can have their consultation sessions with their doctor from the comfort of their own homes, providing a convenient and accessible option for those who prefer remote healthcare. Experience hassle-free booking and consultation sessions with the Hello Doctor application.

## What It Is And How It Works

In the current situation, face-to-face consultation can be difficult and intimidating for some. Additionally, many people may be hesitant to consult with a doctor due to concerns about cost. However, with the advancement of technology, we can address these issues by using video call technology to facilitate remote consultation.

Introducing the Hello Doctor application, which offers consultation sessions with various doctors from different specialties. The application enables clients to easily find and select their desired doctor based on ratings, reviews, and session fees. Payment is made easy for clients, and once the doctor's timeslot is purchased, the doctor can set the duration of the session and start the session at the scheduled time. After the session is complete, clients can provide feedback via a review system.

As the service provider, we will take a commission from each transaction that occurs, and the doctor will receive their payment directly from the client. We believe this application will help to make healthcare more accessible and convenient for clients, as they can easily find a doctor from various specialties. Once you try the Hello Doctor application, we are confident that you will fully understand its functionality.

## Technology / Stack used in this app

- Flutter
- GETX State Management
- Firebase Backend
- VideoCall using Agora.io
- Stripe payment gateway

## App Feature

### Client

- Login (with Google Login, or username & password) / Register / Forgot Password

- Top Rated Doctor

show all top rated Doctor

- Search Doctor

you can search Doctor by their name

- Doctor Category / Specialist

show all Doctor category

- Doctor Detail

you can see Doctor detail, like hospital, price, review, rating, biography . etc

- Doctor Timeslot

you can see all Doctor timeslot that you can book, there is time, and price

- Purchase Timeslot with Stripe payment Gateway

you can purchase Doctor timeslot using stripe payment gateway

- Order Detail

you can see your order detail

- Video Call

start consultation using video call

- Review & Rating

after consultation session you ban give review to Doctor

- Problem

if something wrong, you can complain and payment to the Doctor will be witheld, until problem resolve

- Edit Profile

you ca edit your email, and password

### Doctor

- Login / Register / Forgot Password

- Doctor Detail

Doctor can add their detail such as Specialist, Hospital

- Calendar Timeslot

Doctor can add Timeslot, with price, duration, and date

- Consultation List

Doctor can see if there is consultation being purchase

- Video Call Consultation

Doctor can start consultation session and client will be notified

- Balance, Money

Doctor can see their balance add if consultation alredy ended

- Withdraw Money

Doctor can withdraw their money using payment method that their chose(currently only support PayPal)

### Web Admin

- Dashboard Data (User Number, Doctor Number, ext)

- List Data of User

- List Data of Doctor

- List, Add, Edit, Doctor Category

- List Transaction

- List Witdhraw Request

and more
