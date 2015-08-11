# PushLogin
Notify Your Devices when Your Mac Logs In.

## How PushLogin Works
PushLogin is basically an Automator app that will send a push notification to your device through PushBullet. By adding it to the current user's Login Items, PushBullet will run when the user logs in and post a notification to your other devices.

Before it runs, PushBullet will try to ping pushbullet.com and will continue to ping every 10 seconds if an error occurs. This allows Pushbullet to wait until the WiFi or internet connects. If the ping was successful, it'll post the Notification.

## Installation
1. Go to [Pushbullet/Accounts](www.pushbullet.com/account) page and copy your Access Token.
1. Open the **SetupConfig.app** and paste in your copied Access Token after the *PB_API_KEY=*
1. Open **PushLogin.app** to test whether it works or not.
1. Copy the **PushLogin.app** to a folder you want to hide it in (eg. **~/Library**)
1. Open System Preferences > Users & Groups > Login Items > +
1. Find where you just hid *PushLogin.app* and select it
1. You're done!

## Push to Different Devices
By Default, PushLogin will push to all your connected devices.
If you would like to change it...
1. **cd** into the current directory in Terminal and type in
```bash
  pushbullet list
```
1. You'll see a list of devices connected to the PushBullet account.
1. Open the *PushLogin.app* in *Automator.app* and at the line where it shows
```AppleScript
do shell script ". " & resourcePath & "pushbullet push all note \"User Login Detected at `date +%H:%M`\""
```
1. Simply replace the word `all` with the device you want.
1. Open *PushLogin* again and see if you receive the notification.

## Credits
[pushbullet-bash](https://github.com/Red5d/pushbullet-bash) - Bash interface to the PushBullet API by [Red5d](https://github.com/Red5d)
