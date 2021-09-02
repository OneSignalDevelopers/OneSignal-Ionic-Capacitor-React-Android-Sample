# Push Notification Integration In Ionic + Capacitor (React) Android App

- **Part 1: Set Up Your OneSignal Account**
- Android Configuration
- **Part 2: Push Notification Setup For Android In Ionic + Capacitor (React)**
- Send Mobile (Android) Push Notifications

This tutorial requires some basic knowledge of React. I'm using the [Ionic CLI](https://ionicframework.com/docs/cli) to generate my project and **NodeJS version 14.16**.

Github Repository Resources: [Ionic + Capacitor (React) OneSignal Setup](https://github.com/OneSignalDevelopers/OneSignal-Ionic-Capacitor-React-Android-Sample)

## Part 1: Set Up Your OneSignal Account

To begin, log in to your [OneSignal account](https://onesignal.com/) or [create a free account](https://app.onesignal.com/signup). Then, click on the blue button entitled **New App/Website** to configure your OneSignal account to fit your app or website.

![OneSignal App](https://lh5.googleusercontent.com/Ebl1JmOEJM1HyO4yq_XHLlh9Db6XcOSLmu0BGhj5ja08nNxLYNjNHruf84bStnCCioe5qDcpUd-OkDtAgcqUQVdXxRHDTxzLriRlAiARZvn94BLokXSRlmip31XMahDBNFGIYjG3)

Insert the name of your app or website. Select **Google Android** as your platform.

![OneSignal Android setup](https://lh4.googleusercontent.com/SlEfsntRb7J0y0JgSdQ5rcEoVm1w19j5Od3p6EPI6sIC0r-lksC-A1mpmkmeYwPOmYwb62MhvFY2ep0vpR-Z7ASG59VYKh9_y2J_M1T_lNbtEi4rrRXXRDRvvYYE0muG5wl-8G_B)

Click on the blue button entitled, **Next: Configure Your Platform**.

**Google Android FCM Configuration**

It’s time to configure your Android app using a **Firebase Server key**. This key and the Server Id are required by all Android apps if you want to send push notifications. If you don’t have the Firebase Server Key, take a look at [this doc](https://documentation.onesignal.com/docs/generate-a-google-server-api-key) to learn how to get your key.

![OneSignal Firebase Server Key](https://lh4.googleusercontent.com/ik5SwHcH5x3nKswqxXDmvmr6cPnb0e_-IV9CZH1-Iu5xxzK9yF4S5V2I--Nfs5rJ5FTAI6AtweUFtPi9gb5hOx2YdiWXr8tF0nu9qzsLsgXTEwLgY3HnbEBN_RBTQvKk2-rodQl9)

Now select your target SDK. We'll take you through the steps to get your first user & send your first test notification.

![OneSignal Ionic Setup](https://lh3.googleusercontent.com/qfldf1uKZMGFkeDD2yZA4sjKqzFNgPOS9kM5MyNK0ki-hxJUjZsAE1AHlPmhPY7xb85XXy-LtWBeyMqWuh8Uoho1WNI2IG1KPf8P_1t58Fe61Cpa_ggatx-yRkkFidFpVT1ufhn4)

In the next screen, you will see your **App Id**, copy that app id because we will use it inside of our Ionic application. Make sure to **DO NOT** check for subscribed users nor clicking on done yet.

![OneSignal App Id](https://lh3.googleusercontent.com/dK7TxCGbAMSRxfMvl5ellSW_E-qgjLPXvvPMWS4LUo1cZVc7B0vAdVXiv-m5njZ7osETrAkjLiszeETY62B826NVVSYtYIV1q8Sv9ddxxFj4e-0pNROsDEYUwRduvRsWj-FHLb9X)

## Part 2: Push Notification Setup For Android In Ionic + Capacitor (React)

Now that you have gotten the necessary items to integrate Push notifications in your Android app, you will need to make your Ionic app aware of OneSignal to receive push notifications.

### Creating Your Ionic + Capacitor (React) App

Inside your terminal, you will have to run the following command to add the Ionic project globally in your machine to use Ionic in your command line.

```shell
npm install -g @ionic/cli
```

Inside of your terminal run the following command to create a new Ionic + Capacitor (React) project using the Ionic CLI. You will be asked to select a framework, select React.

```shell
ionic start
```

![OneSignal Ionic app](https://lh6.googleusercontent.com/esfBfrFeTz6IeXvYoHxxft1O2z8BdeLVWNvGBnPRfgxymZVHRIZqHsZ-K8KitvSyWa77do2Zgw9d8X3k_3Uwt0t1PmIUu3ImEO_g4a-Hp2F7n2qajQc3PvKmOMkvzZdVkmds1HiZ)

When asked to enter a project name, you can enter whatever name you want. In my case, I named my project ​​OneSignal-Ionic.

![OneSingal Ionic ](https://lh4.googleusercontent.com/q03rLlgD5WO4DN912G01alEYnjTMhsw5Z1Ow3FfNXyQAW5JjOGbgkI3-hbDp-j4XWmWlY9VrqQAsoy0X6dvDWI9YcnKUiBE7TWXSJPZlNByQLh-cgtEpGam_BlTlgOyx5RBzuIFu)

Later you will be asked to select a template, feel free to select the template that you want. In my case, I will be selecting **tabs**.

![OneSignal Ionic Tabs](https://lh4.googleusercontent.com/NGkzTmvU7YA-qNfDECwTVJx1OA3qMS8xLLITMaXj1XeZv1fk8gUmkR11bV9RBDn_1q2iuNXQH3xhH9BUivI2B9SAoLx2XseEhLjxO312NGqt8znG1kqQtg8nbWXV9KT9J4u2RSMl)

### Adding OneSignal To Your Ionic Application

This is a simple Ionic React Android app that illustrates how to integrate the OneSignal SDK.

Running on the Cordova npm package [onesignal-cordova-plugin](https://documentation.onesignal.com/docs/step-by-step-cordova-2x-to-300-upgrade-guide) release.

Add your desire platform to the project, for this app I chose Android by running: `ionic capacitor add android`

Now, Install OneSignal Cordova plugin inside project `npm install onesignal-cordova-plugin`

It’s time to build your Android app. This command will open the Android build in Android Studio `ionic capacitor build android`

After building your Ionic application into a new **Android app**, run the **cap sync** command (1 time only): `npx cap sync`

At the top of you **App.tsx** file, import the OneSignal npm package to your component.

`import OneSignal from 'onesignal-cordova-plugin';`

Add the following initialization code to the App.tsx file. **Make sure to add your app ID, which you previously copied during Google Android FCM Configuration.**

```javascript
// Call this function when your app starts
function OneSignalInit(): void {
  // NOTE: Update the setAppId value below with your OneSignal AppId.
  OneSignal.setAppId("YOUR_ONESIGNAL_APP_ID");
  OneSignal.setNotificationOpenedHandler(function(jsonData) {
      console.log('notificationOpenedCallback: ' + JSON.stringify(jsonData));
  });
}
```
After creating the `OneSignalInit()` function, you are going to call it when your app starts. In the **App.tsx** file, add the following line of code:

`OneSignalInit();`

Finally, build your app again by running `ionic capacitor build android` and open the project in Android Studio.

**Note: I recommend you run the application on an actual Android device to test the notifications. To run the app on your Android device you will need to connect your device and enable [developer mode](https://developer.android.com/studio/debug/dev-options).**

Once you have connected to the device and enabled developer mode, run the application on your device by selecting your device as the target device. In my case, I’m running the app in a **Google Pixel 5**.

![OneSignal Android Run](https://lh6.googleusercontent.com/JWbNLNK3Gt6SbI2RHBAms-o4_PVhXuEr6jsCzLYCtn4VRgnhAnHEmJIrMN1zPhOx8UpTkazZTjXDCIFLVxYqKkEnVlIgEQHsr_BXClvppvtK7l84whahm6XEcc5-FHSe6Mi0Jhsu)

Once you have opened the application on your device, the device will be automatically subscribed to the notification. Now, your device will be able to receive notifications sent by OneSignal.

Time to finish the setup. Go back to the OneSignal setup, click on the button **Check Subscribed Users** and a green message will appear like the one in the image below.

![OneSignal Android Setup](https://lh4.googleusercontent.com/sTOOxfHRrTPyis3ferWfRKPmBu8KgEEhgl_tph_gKdOvEVTXlbekWKfaoeaTuhTWDZXdFjot_CHJ8DkimzvSfDMqwwTazkoa3j3UVtTQxbJjxHrbaynuo_8SJH988gwV3LdQWcFp)

Click on the **Done** button.
