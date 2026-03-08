---
sidebar_position: 3
sidebar_label: Setup Apple Sign In
author: amsyari
---

# Setup Apple SignIn

Apple Sign in only work in IOS build, so the button will not showing in android build, to enable it :

## Enable Aple SignIn in Firebase 

1. Open Firebase -> Authentication -> Add new Provider ->

![Example banner](assets/enable%20apple%20sign%20in.png)


2. `Enable Apple Sign in` - > Save
![Apple Banner](assets/enable%20apple%20sign%20in2.png)

Done, now you the app should be able to register with apple account

:::info
with apple's new rules for uploading to AppStore
Apple Required you to enable Apple Sign in if you enable Google Sign in, 
except if it not implementing Google Sign is, it's okey to not Adding Apple Signin
like the Teacher App, it's not implementing Google & Apple Sign in
:::
