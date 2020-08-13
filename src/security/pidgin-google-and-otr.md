## Using Pidgin with a Google Account, and Setting Up OTR

Pidgin comes installed with Ubuntu 16.04. To add my existing Google Account, I followed the steps outlined in [this Stack Overflow answer](https://stackoverflow.com/questions/28681341/how-to-add-google-talk-hangouts-to-pidgin-chat-client/33898893#33898893).

To summarize: 

In Pidgin, add a new account. Set the Protocol to "Google Talk", username to your Google username, and the Domain to "gmail.com". 

For the password you'll need to create a dedicated app password. You can do that [in your Google accounts Security > App Passwords section](https://security.google.com/settings/security/apppasswords). When creating the new app password, set "app" to "other" and call it something like "linux pidgin"-- it doesn't matter what you call it. Optionally, if on a secure computer, tick the "Remember password" checkmark. (Warning: This will mean your new app password will be stored in plain text in `~/.purple/accounts.xml`.) Leave "Resource" and "Local Alias" blank.

### Installing and Enabling OTR

Once my Google account was successfully added, I installed the Pidgin-otr plugin by running `sudo apt-get install pidgin-otr` in terminal. To enable and setup OTR, I followed [this EFF guide](https://ssd.eff.org/en/module/how-use-otr-linux). That guide also describes how to install the otr plugin through the Ubuntu Software manager if you're more into GUIs (see the early steps of that EFF guide).

### Further Pidgin Customizations

To display offline buddies, go to Buddies > Show > Offline Buddies. There are more preferences, like muting sounds, in Tools > Preferences.

Not sure how to disable the pop up notifications yet though.
