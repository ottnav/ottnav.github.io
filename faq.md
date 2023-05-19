{:toc}

# OTT Navigator FAQ
## What is OTT Navigator?
OTT Navigator is a video player dedicated to work with streamed and vod content, usually provided by `OTT/IPTV` providers

## Which IPTV service should I use, or which is used by the app?
The app is just a player and neither has any content, nor can provide you any. In order to use it, you need having an IPTV provider and configuring it within the app.

## How can I contribute to the app development?
- Help other users by responding to their questions in our Telegram channel.
- Translate to your language or improve current translations
  - Translations are being available online at [github](http://github.com/ottnav/ott-nav-locale/) (source language supported by developer is English, you can take it as a base).
  - Then you choose either:
    - (Github way for tech-ready guys): fork the repository, make your changes and submit a pull request
    - (Easy way for normal people): just download the corresponding xml file (or create a new one taking strings.xml as a base contents), make changes that are required and send it to us via email
- Provide high-quality detailed description on the issues you are experiencing, and suggestions you feel will perfectly fit the app.
- Suggest common questions and solutions for the FAQ
- Spread the word and help the app to grow and get new users

----

# Installation

## How to install
- Install from supported app store
- Sideload non-store (standalone) build of the app (check the link at the bottom of the FAQ)

## How to install on my Windows PC/Mac
There is no special version dedicated to be used on Windows PC or Mac, however, there is a solution to use the app with negligible side effects.
- Windows 11 has a decent Android apps support, so it's recommended to use builtin solution for running apps.
  - Step 1: Install `Windows Subsystem for Android` following one of these 2 instructions:
    - with Amazon Store: https://www.windowscentral.com/how-get-started-android-apps-windows-11
    - without it: https://www.androidpolice.com/set-up-wsa-windows-11-android-apps/
  - Step 2: Install `standalone OTT Navigator` app (check bottom of the FAQ)
- Install NoxPlayer app on your PC - it allows running Android apps and is highly optimized and recommended. Just use it like it was a native app.Some users are running the app on different emulators, like BlueStacks emulator and report that it also works quite well, and supports later Android versions. 

Please note, that hardware acceleration might not be available when using emulator on some devices, so you might need selecting software codecs to watch your content.

## Will the app work on my TV? Why not WebOS/Tizen?
The app only works on Android, so if your TV is running Android TV / Google TV then it will run perfectly.
We have investigated the tech and even did some proof-of-concept, but WebOS/Tizen are simply not powerful enough to make a really good app. It's suitable for simple web pages that pretend to be apps, but lack real power to do complex under-the-hood tasks.
So if you choose an LG/Samsung TV (the only 2 major vendors that do not use Android these days) - then it's highly recommended to purchase an Android / AndroidTV / GoogleTV / Chromecast(2021+ model) / FireTV / etc box or stick to be attached.

----

# Provider (playlist) configuration

## Which provider template should I choose?
- If your playlist contains something like `.../get.php?username=...&password=...&type=m3u_plus&output=...` most probably your choice is Xtream Codes template
- If the url contains something like `/stalker_portal/c/` then you should select either MAC or Stalker portal
- If you have a m3u file downloaded from provider, you should either upload it and setup as a Playlist (recommended), or configure as a Playlist File
- In other cases configuring as Playlist is generally preferable

## What playlist formats are supported
- Preffered format is [M3U/M3U8](https://en.wikipedia.org/wiki/M3U)
- However, the app also supports lots of more exotic formats (the support might be limited though), including `WebOS webtv`, `Tizen nStream`, `.xspf`, `.tv`, `SAT .txt`, etc

## Playlist setup
Your options are one of the following (it’s always preferred to use links over files):
- Use a specialized service like [m3u4u](https://m3u4u.com/) or [m3u.in](https://app.m3u.in/) to upload your playlist and configure a link to it
- Use any cloud storage service you prefer. For example, if using Dropbox:
  - Copy a playlist file to your personal Dropbox cloud storage
  - In a context menu select `Dropbox -> Copy Link`
  - Open a text editor and paste a link there; replace `dl=0` to `dl=1` in the link (since by default it copies a link to the web page rather than to the file itself)
- (Not recommended) copy file to Downloads directory, so the app will see it. However, file access is being limited in Android from version-to-version, and especially on Android TV devices, so better use any of the cloud storage.
- (For admins) make a web server in the local network that is bind to host “iptv.local” and ensure that your playlist is available by HTTP request to `iptv.local/playlist.m3u` and the app will auto-detect the playlist
- Also you can setup the player on your phone (not using files, links only!) and then use the backup/restore feature of the app to transfer configuration to your TV/box device!

## Streams not playing (401, 403 or other 4xx and 5xx errors)
These errors are returned from your provider (check [manual](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses)), so in general you should refer to your provider for more details.

Sometimes it may mean that your provider requires some extra headers (like `User-Agent` or `Referrer`) in the requests that you should configure via playlist or via the app, sometimes it might mean that your provider sources are configured incorrectly or even your subscription to your provider's services has been expired. Since it's provider-specific, there cannot be generic solution for this, contact your provider for help.

## Getting IP blocked by provider (or 403 error)
These issues might be caused by different provider paranoid flood settings/connection restrictions that can affect access to service. Here are some recommendations if you experience such a problem:
- Check amount of connections your provider offers and configure provider parameters to match this value in order to limit picture-in-picture and other advanced modes
- Setting stream technology to MPEG-TS (`settings - extended`; HLS support on xtream codes servers is quite poor)
- Disabling video preview (`settings - lists - description`) and in general limit usage of picture-in-picture and studio mode
- Disable video preview for Android TV home screen (if you enabled it) (`settings - extended - android tv`)
- Disable integration with android mediasession and notification (`settings - extended - system`)
- Contact your provider

## EPG setup
You can check whatever EPG is provided and alive from your IPTV provider by navigating to `Settings - EPG - Reload`, and watching the status of reload process (looking for the number of sources processed, each sources processing result).  

If your provider has an EPG source but for some reason does not specify it in playlist, then it’s recommended to configure it in `Settings - Provider - (your provider) - Parameters - EPG`.
This way the channels mapping will be searched by both channel names and tvg-id fields.
If you configure EPG source in `Settings - EPG - User-provided` then matching by name is only used.

## Want easier way to input characters on my Android TV device (from Phone)
Some of the control apps recommended to serve as a secondary output to your TV/box:
- (Android) [Android TV Remote Control](https://play.google.com/store/apps/details?id=com.google.android.tv.remote)
- (iOS) [Android TV](https://apps.apple.com/ru/app/android-tv/id1078761166)

## Fail to connect to the portal, however it works well in the other app
- First, please check all the data you input for misprints, correct url, etc - usually it just means that your provider requires some additional fields to be passed, like `device_id` or using some exact `user-agent`.
- If all the data seems correct but you cannot still connect via the app then please record a network dump working with your provider using the different app (stbemu highly preferred):
  - Install network capture software (or proxy) like `Wireshark`, start recording
  - Launch an app that works against your provider well (like `stbemu`)
  - Login to your provider, do some actions like list channels or videos
  - Stop recording and send the resulting capture file (`cap`) to the support email of the app, providing details on your provider and connection. It will help investigating the specifics of your provider and will help adding support for it in the future.

----

# General issues

## Part of the screen is being cut by my TV (fighting against overscan)
Some TVs are coming with overscan enabled in their configuration (especially for HDMI ports). Possible solutions (better to worse sorted):
- Disable overscan on your TV
- Configure HDMI port on your TV to be of type PC (this also disables overscan)
- Open display settings on your device, and setup it to match your screen (usually named position and size)
- In OTT Nav app go to `settings - visual style - margins`, and set up a margin that matches your TV output.

## Want to stream video from phone to my TV, how to do it?
App supports 2 ways of sending a stream to a TV (when both are located in the same WiFi network). Both are not very reliable and cannot be used if your provider requires some DRM tags or specific attributes being passed in addition to the stream url. The options are:
- If your TV supports working as WiFi TV (and is acting as UPnP device), while playing video open the menu -> parameters -> send to TV -> select your device. If successful (and the stream supported by your TV) it will start playing on TV and you should stop playing it on your phone not to take extra network connection. Note, that TVs supports only limited set of stream types and might not support the one your provider is offering.
- If you are using an old Chromecast device (2020 and older) and have Chromecast devices available in the network there will be a button on HUD to send the stream. This does not apply to newer Chromecast that are actually a Google TV device with Android, so you can just install the app and use it via remote, instead of just casting the stream.

Please note that due to limitations of your TV/Chromecast devices some streams cannot be sent - this includes streams that are encoded in `mpeg-ts`, or when your provider requires passing extra `http` tags to the stream (like `user-agent`, `referrer`, extra headers, etc). In this way it's recommended to use external player like `VLC` that can transcode `mpeg-ts` streams to `hls` that are usually playable on TV/Chromecast.

## Having multiple providers, how to manage channels?
The app has many options on how to manage channels from multiple providers.  
One the best that suits most use cases (when you need max channels from all providers and do not want to mess on them is):
- Remove/Hide categories you are not interested in
- Group channels (move) them so all channels of the same category (like sports) from all providers are located in the same category
- Enable duplicates folding. This way all channels with same or close names (like HD variants will be folded into a single record)

If a playback issue will occur the app will automatically switch to the next source (eg folded channel). You can alternatively manually switch between sources.
Note, that unless you manually switch the source of the exact channel, the default channel to be used will be the first one in the list if duplicate folding is disabled.  

Note, that the app sorts providers alphabetically and applies a list of channels from these providers in the order, providers are. So if you have sorting mode by provider being set, naming a provider alphabetically before others will cause their channels be higher in the list.  

Also quite popular is the quick provider switch option that adds a button on the main screen to enable/disable filters by a single/multiple provider you are currently interested in.  

Other, less popular, but still valuable options are to disable category merging between different providers, so “Sports” from provider A will not be merged with “Sports” from provider B, creating different categories instead. Also you can enable showing provider name in the channel name (either as a prefix or as a suffix of a channel)

## My list of channels messed up when I added a new provider
Providers are sorted and applied alphabetically. So if you had a provider named `BBB` in the app and made modifications to the groups, channels, etc, and then added a provider named `AAA` then some of the modifications will apply to the new provider `AAA`, since the provider list (as being sorted alphabetically) is now `AAA`, `BBB`.  
To preserve your metadata, ensure that new providers are AFTER the current ones. For example, you can add a prefix to the provider name like `1 BBB`, and `2 AAA` so alphabetically they will be `1 BBB`, `2 AAA` and channels/categories from the second provider will not be used for modifications made for the first one.

## Time is shown incorrectly on EPG, how to fix that?
Almost always when you see incorrect time it’s incorrect device setting (selected incorrect timezone), so go to the device settings and setup the time and time zone that correctly matches your region.  

If this does not help, here are some options available to you to make a virtual time shift:
- `Settings - Extended - System - Time shift (visual)`
- `Settings - Extended - System - Time shift (system)`
- (if the issue applies only to the some channels) open problematic `channel properties - EPG - time shift`
- (if using portal) open `provider properties - time shift`
  
After any of these changes you need to do manual EPG reload (`settings - epg - reload`) in order to apply the changes.

## Want to use Studio mode (up to 9 videos at the same time) or Picture-in-Picture, but cannot find how to enable them
Studio and PiP mode requires you either having multiple providers, or having a provider that allows more than a single connection at the same time. App tries to detect number of connections via provider API, but sometimes might not be able to detect it correctly. To set a number of connections your provider allows manually:
- `Settings - Provider - (..your provider..) - Properties - Connections`

After changing, your will have studio mode option available on the main screen, as well as PiP menu option available from a playback menu screen if these modules are not been disabled. To enable if you previously disabled (they are disabled by default on phones):
- Long tap any `icon on home screen - Modules` and ensure that Studio and PiP modules are enabled
- While in playback, `long tap any player menu icon` to check if the corresponding menu item has been enabled.

## I want to use my own background wallpaper image
You can use any image service you like, here is a quick sample to get idea how to get link to the image:
- Go to `https://imgur.com/upload` and upload your image
- You will be redirected to page like `https://imgur.com/a/SomeID`
- Press `hamburger icon -> Get share links`
- Copy the one that is named `Share Link` (will be something like `https://imgur.com/SomeID`)
- Paste the url in the app

## How long does backup in a cloud available?
The exact time may vary (depending on the load auto-cleanup may be done more or less frequently), but in any case it will be available 7 days at least. General service target range lies between 1 and 5 weeks.
You can also store backup on your own server - check FAQ about it

## Auto-start on device reboot
You can enable the app to auto-start on non-phone device boot via `Settings > Extended > Start on boot`.
However, the newer Android version is, the lower is the chance that this feature will work (though you should try, since it depends on your device firmware), since apps are limited when launching any visual screens from background by default.
However, you can enable `allow background activity starts` checkbox in `Developer Settings` (unlock them by going into your device settings, `About > Build Number` and tap this option 7 times).

## Cannot use local files for playlist, backup or other features
It is highly recommended not to work with local files. Recent Android versions greatly limited the app to work with files NOT created by the app, meaning that loading playlist from network and saving as a file, or using a backup after app reinstall is not available directly. While it is not problem when using a phone, since Android on phones has built-in file manager that allows browsing for file and getting access to it, it is still a problem on Android TV devices, since the firmware does NOT come with file browsing API, so there is no way besides rooting the device to access user-created files.

For the app we prefer features that works perfectly, that means that adding feature like backup to local file that will work in some cases (when clearing app data) but will not work in other cases (when reinstalling the app) - it is unsafe, since user is expecting the feature to work. So we prefer to hide such an option on devices that has limited access to files (like Android TV devices) instead of providing only a half-working feature.

So you should use different options - use cloud storage or services like `m3u4u` for playlists, and cloud backup options, etc.


----

# Playback

## Buffering way too much
There might be multiple reasons for buffering - starting from poor Internet connection to some firmware specifics. Here comes a list of actions that usually helps if the cause is hardware/firmware, rather than the network issues, try one-by-one:
- Set buffer size to minimal (`settings - player - network - buffer`)
- Change hardware codecs quality to compatibility (`settings - player - codec - hardware quality`)
- Disable AmLogic fix (`settings - player - codec - amlogic`)
- Change device resolution from 4K to Full HD on your device if not watching 4K usually
- Use a different codec for the given channel (since some codecs might not work well on your device/firmware)
- Set buffer size to maximum (assuming that your network connectivity have packet loss)

If the solutions above did not resolve your issue, then it's definitely a connectivity issue to your IPTV provider. You should contact him to fix the issue.

## Problems with video/audio playback
Since the streams of your provider can be different, your hardware used for playback has different capabilities and your device firmware has bugs, there is no best configuration. App comes with hardware decoders, software decoders, and support for external player, defaulting to software codecs in most cases as being less dependent on firmware bugs.  

Please try using these settings in the suggested order and test which works best for you:
- Hardware codecs (compatibility mode) - most channels should work, especially if casted via HLS/DASH technology
- Hardware codecs (best match mode) - can help supporting original 4k satellite streams
- Software codecs (should support almost anything, but will work slower)
- External player

App remembers which codec was previously selected for channel and will reuse it in the future (unless disable this in settings)

## Horizontal scrolling text is unreadable
When app is using hardware codecs it has no control whatever deinterlacing will happen or not - it’s fully dependant on your device firmware. In order to insist on deinterlacing you should switch the channel to use software codecs that uses one of 3 different deinterlacing algorithms depending on what software codecs quality is selected.

## Audio track selection / Subtitles enabling
Sometimes hardware codecs are unable to detect different audio tracks availability (especially in some incorrect HLS streams) and may not support subtitles. In this scenario you can use player menu to switch to software codecs, so you will be able to select a different audio and subtitles track.

## Trying PiP / Studio Mode, but app says that connections limit reached
App tries to detect the number of connections your provider allows to protect you against ban by your provider. Some providers do not allow the detector to work so app defaults to a single connection in that case. You can override auto-detected connections limit yourself.  
Go to `Settings - Provider - (select your provider) - Parameters - Number of connections`.
Bear in mind, that you still can use multiple screens (PiP / Studio) using 1-connection providers, if you have a couple of them, since each provider is counted separately.

## Hostname … not verified / Chain validation failed / SSL error when trying to playback
This error means that your provider is using invalid SSL certificates (either self-signed or without a trusted root). Your solution might be:
- Check date and time on your device (if it differs too much from the real time the secure connection to your provider will fail)
- Ask provider to either fix the SSL issues or to provide a link to plain http-only configuration
- Disable certificate validation within the app:
  - `Settings -> difficulty -> expert`
  - `Settings -> extended -> system -> ignore invalid SSL`
  - Restart the app

## The app does not see all audio tracks
This usually means that your provider incorrectly encodes the stream (quite common when the provider is using HLS but actually sending all tracks in the same file while they should be split to different ones).  

Best option would be to ask the provider to give instructions how to setup one of the following:
- get a link that either runs mpeg-ts directly
- or ask for multi-hls setup

When it’s not possible, you can also try one of the following:
- Use system video codec (it might support multiple tracks when hardware codecs fails to find any)
- Use software VLC codecs (it uses more processing power but should in theory support almost any stream, just like external VLC player does)

## Playing DRM content and it’s not playing
In order to play DRM-protected contents you need to pass the correct DRM keys and extra data in the playlist. Check the M3U playlist structure on clues how to setup it.  
Please note, that DRM playback is only supported using hardware codecs - so using software VLC, system or external player has no way to pass these license data.

## Experiencing ENOENT (FileNotFoundException) while trying to play a channel
It is a provider issue meaning that master playlist for the stream contains a link for one of the tracks in invalid format - instead of providing full url to the file with the domain, path, etc, it just only gives the path that is considered a local (like `/videos/12345/segment12345.mpg`) - of course, there is no such file on your current device.

## Cannot change volume on some channels
Some channels are using audio tracks that might not be supported by your TV box (like 5.1, 7.1). In this case the app passes the audio stream directly to your TV, since TVs usually supports such tracks. But as a side effect the volume can be only controlled using a TV remote. Possible solutions are:
- enable software audio decoder globally in the app codecs, or on this exact channel (this way the audio stream will be processed on your box, so the full volume control will be available)
- or enable manual audio volume fine-tune within the app

----

# Premium
## How many devices does Premium allow
- for `Play Store/AppGallery` version you can install the app on as many devices as you want (as long as they use same account), but it's a violation to use more than 5 devices at the same time (`Fair Use Policy` is insisted) for a purchase.
- for `Standalone` version you can use as many devices as you have purchased via `OttNav Companion` app.

## Purchase premium on a Firestick (or other device without play market)
- install `OttNav Companion` app (check the link in the bottom of the FAQ)
- launch it, create a new account, and press add more max devices button
- purchase device slots, to have some free slots on your account
- install a `standalone` version of `OTT Navigator` app (check the link at the bottom of the FAQ) (you might need enable installing from unknown sources)
- launch the app, go to settings - premium, log in with the same account you have created in `OttNav Companion`
- ensure that the current device is added to the list of active devices (4-word phrase represents an unique installation id), use `Add Device` button if it was not automatically added
- congrads, you can repeat last 3 steps on your other devices!

## I already have active purchase/subscription on Play Store and want to activate on non-Play Store device
- install a `standalone` version of the app (check the link at the bottom of the FAQ) (you might need enable installing from unknown sources)
- launch the app, go to `settings - premium`, create a new account
- press `claim purchase` button and enter your purchase number, ensure that number of available slots has been increased
- ensure that the current device is added to the list of active devices (4-word phrase represents an unique installation id), use `Add Device` button if it was not automatically added

Notes:
- If you recently made a purchase it might take several hours for system get it loaded, so please try later
- If you cannot find your purchase number in email from Google, then go to `pay.google.com` and find the transaction there
- Single purchase can be claimed only once
- Keep in mind that it's against `Fair Use Policy` to actively use more than 5 devices at the same time for a single purchase

## Purchased a premium on Play Store but it’s not active
Sometimes it takes a while for Play Store to sync purchases (due to long caching). Steps to guarantee that sync will happen instantly:
- Go to `settings - premium - restore purchases`. If the process will report that restoration occurred - it means that all is ok, and reactivation has happened. Usually this is the only step required!
- Clear data and cache of Play Store app
- Clear cache of OTT Navigator app (usually not required)
- Reboot your device (might not be needed, but usually triggers cache update for Play Market), and relogin to Play Store
- Relaunch OTT Navigator
- (if does not help) Reinstall the app
  - Backup the configuration (settings - extended - backup - backup)
  - Write down the backup code
  - Delete the app
  - Install the app, restore the backup
  - Launch the app
- In case it does not help - contact our support (specifying google account used for purchase, or purchase number GPA…)

## Unable to process purchase (Error DF-PDP-3)
Recently Play Market stopped processing purchases when the app was not installed from it. Install application from play market and payment should work.

## Premium and multiple accounts on a single device on Play Store
When the device has several Google accounts, then it might switch between accounts by Google services itself, meaning that in-app purchases / subscriptions might be taken from one or other account with almost no user control. Best way to reactivate all purchases to correct account:
- Uninstall the app (backup is suggested via settings - extended - backup)
- Open browser on your desktop PC
- Open play market page [in your browser](https://play.google.com/store/apps/details?id=studio.scillarium.ottnavigator)
- Log in to the web interface of Google Play with the account you used to purchase
- Install the app from the browser selecting the device to push the app to

Or switch to using standalone version of the app that is not linked to the active google account

## Will the premium purchase work for Family Library?
No, family library only apply to paid apps. Free apps with in-app purchases are not eligible for this. You can still use the app on several devices that share the same account.

## Currently subscribed to premium, willing to purchase via single payment forever
## How to change subscription period
If you wish to change your subscription, like switching from 3 months to annual, you need:
- Cancel auto-renewal of your subscription (this is done in a store app)
- The subscription will last until the end of the payed period (we do not allow purchasing a different subscription at the same time to protect users from accidental purchase of several subscriptions at once)
- After the premium period will expire you will have options to subscribe to a different period or purchase using one-time payment.

----

# Managing activations for multiple users (Partnership / Reseller)

## I want to purchase a lot of premium access and provide them to some users (clients), acting like a dealer
You can purchase more slots for device when you need and can give some of the slots to different users. In order to do this:
- Install `OttNav Companion app` (check bottom of the FAQ), register an account (if do not have ottnav account yet)
- Purchase as many premium device slots as you need (the larger pack you are purchasing, the cheaper it will cost per-device)
- Create a subaccount configuring a number of slots you wish to share with a different user/client
  - The app will generate a new login and password that you will share with this user
  - The user will need to install a `standalone version` of the app (check bottom of the FAQ) and log in using generated credentials
  - The user will be allowed to use the number of slots (devices activated) you have allowed
- You will be able to manage subaccounts using `OttNav Companion` app, adding new subaccounts, deleting them, or changing the number of slots (devices) allowed for this client to use. Alternatively you can use `API` to manage subaccounts

## API to manage client subaccounts
In addition to manual processing of client user accounts via `OttNav Companion` you are also able to achieve the same actions via the `API` making network requests to the server `api.ott-nav.com:8080/account/` to these endpoints:
- Authorize: `login` (`POST`)
  - Arguments: `login`, `pass`
  - Returns: a bean representing your account including `session` id and subaccounts
- Create subaccount: `addsub` (`GET`)
  - Arguments: `session`, `name` (some meaningfull title for the subaccount), `slots` (number of slots to give to this subaccount)
  - Returns: `{"<login>": "<password>"}` with the data of newly created subaccount
- Delete subaccount: `rmsubacc` (`GET`)
  - Arguments: `session`, `login`
  - Returns: a bean representing your account including `session` id and subaccounts
- Change subaccount properties: `editsubacc` (`GET`)
  - Arguments: `session`, `login`
  - Optional arguments (depending on what you wish to change): `name`, `pwd`, `slots`
  - Returns: a bean representing your account including `session` id and subaccounts

## Backup directly to your server for you and/or your clients
Since `v1.6.7.3` the app supports specifying custom url for backup service. This endpoint is called with `POST` data sent to it, so you can create script that stores backups for you or your clients on your hosting with your control. A very basic acceptor script in `PHP` that saves backup to `backup.nav` file would look like this:
```
<?php
$data = file_get_contents("php://input"); // get data from POST
$fp = fopen('backup.nav', 'w'); // creates a backup.nav file in the current directory storying the backup
fwrite($fp, $data);
fclose($fp);
?>
```

----

# Re-branding / white-label app

## Branded app with customizations
If interested in whitelabel package (custom logo, background, etc), then contact us via email `ottnav.partners@gmail.com` or reach us on Telegram (contact `@FlavusV`)

----

# Restricting functionality for users of the app

## How to protect some content from other users (parental control)
There are multiple ways to achive this
- Child mode (`settings - extended - child mode`) allows to specify which exact channels are available and hides all the other contect (PIN-protected)
- Restricted mode (`settings - extended - restrict`) allows you to setup a PIN code and protect settings, provider info, or categories/channels, etc to be available
- Using multiple user profiles

## Sharing same device between muktiple users
You can setup different user profiles, and some user-specific history, settings and suggestions will be saved on a user base, like custom favorites, etc.
You can also protect some of the user profiles via PIN code.

## Preparing devices for other users and wish to hide provider details
You can configure the app and then hide provider details.
- Go to the `settings - extended`, and long press the status line.
- You will be asked for a service code (if set) or receive access to service panel, that allows you changing the service code and/or disable provider settings details availability.

----

# Technical staff (playlist edit)

----

## M3U Playlist file sample (brief info on supported tags)

### `#EXTM3U`
Playlist header, marks playlist start  
Supported attributes:
- `url-epg="http://path/to/epg/api/"` : prefix for getting channel epg for exact channel (not recommended)
- `url-tvg="http://path/to/epg.xml.gz"` : path to EPG teleguide for the whole playlist (`XmlTv` format that is either `xml` or `xml.gz`)
- `url-logo="http://path/to/icons/root/"` : root for all channel icons (used if channel has icon specified without scheme://domain part)
- `catchup=".."` : alias for `catchup-type`
- `catchup-type=".."` : specifies that there are archives for channels. Supported types:
  - `default` - only replace variables
  - `flussonic`, `flussonic-hls` - flussonic (HLS)
  - `flussonic-ts`, `fs` - flussonic (MPEG-TS)
  - `flussonic-dash` - flussonic (MPEG-DASH)
  - `shift` - `?utc=startUnix&lutc=nowUnix`
  - `archive` - `?archive=startUnix&archive_end=toUnix`
  - `xc` - xtream codes
  - `append` - appending value specified in catchup-source attribute to the base channel url
  - `timeshift` - `timeshift=startUnix&timenow=nowUnix`
- `catchup-time="10800"` : duration for archives being available (in seconds) (not recommended)
- `catchup-days="3"` : duration for archives being available (in days)
- `catchup-source="..."` : allows override path for archive playback (or append to the end of the url if catchup-type="append" is set). Supported variables:
  - `{key}`, `${token}` - user-configured token
  - `${start}`, `{utc}` - show start (unix time)
  - `${timestamp}`, `{current_utc}` - current time (unix time)
  - `${end}` - show end (unix time)
  - `${login}`, `${password}` - user-configured login and password
  - `${duration}` - show duration (seconds)
  - `${durmin}` - show duration (minutes)
  - `${offset}` - delta from current time to show start (seconds)
  - `${start-year},${start-mon},${start-day},${start-hour},${start-min},${start-sec}` - show start date/time variables (`v1.6.6.5+`)
  - `${end-year},${end-mon},${end-day},${end-hour},${end-min},${end-sec}` - show end date/time variables (`v1.6.6.5+`)
- `max-conn="1"` : if your provider allows user opening more connections at the same time (like watching picture-in-picture) set number of connections here
- `billed-till="timestamp"` : unix time when user account will expire (will be displayed for user)
- `billed-msg="some text"` : custom message regarding user account (might be balance or any other info to be shown)
- `refresh="N"` : period of time when the playlist should be reloaded (`v1.6.6.1+`), in hours (if below 24), in minutes (if < 300), or in seconds if a large value, for example: refresh=”3” means refreshing each 3 hours)

### `#EXTINF:0 tag1="value1" tag2="value2"...,Channel name`
Channel declaration. Supported attributes:
- `ch-number="27"` : default shortcut for channel when using remote keys switching channel
- `group-title="Movies"` : category this channel belongs to
- `group-logo="http://url/to/image.png"` : category icon (`v1.6.6.7+`)
- `parent-code="0000"` : if set, marks a channel as restricted that should be hidden by default unless code entered (like adult)
- `ch-id=".."` : channel id. used only with combination when url-epg or url-logo are set in playlist header (appended to the end of the base url)
- `tvg-id="abc.yz"` : channel id in epg teleguide that was linked in the playlist header (or the one user has configured in the current provider properties)
- `tvg-name="Original"` : original channel name (channel name as declared in epg teleguide), if differs from channel name specified in playlist
- `tvg-logo="http://path/to/logo.jpg"` : link to channel logo (or file name that should be appended to root url set in url-logo in playlist header)
- `tvg-rec="1"` : marker that channel contains archives (0 - off, 1 - on). not needed if catchup* attribute is present (values more than 1 are parsed like aliases for catchup-days=”n”)
- `catchup*` : all catchup settings that are explained in header can be overridden here on channel level
- `type="playlist"`, `content-type="playlist"` : allows to merge another playlist inside the current one. Url specified for this 'channel' is treated as include
- `type="movie"`, `type="series"` : use any of these 2 markers to mark that the channel listed is not a channel, but actually a movie or a series, and should be treated as such, and should be placed to media library
- `adult="1"` : marker that channel is adult (however it’s highly recommended to place all channels in single adult category for simpler user manage)
- `tvg-shift="-2"` : marker specifying that epg data should be shifted by several hours
- `audio-track="2"` : try to autoselect 2nd audio track

### `#EXTGRP: Category Name`
Alias for `group-title` tag

### `#EXTHTTP:{..http tags..}`
Simple way for passing extra http attrs (`v1.6.6.9+`):
- `#EXTHTTP:{"User-Agent":"Chrome","SomeOtherTag":"SomeValue"}`

### `#EXTVLCOPT:parameter="value"`
Allows setting some custom parameters for the current channel (`VLC` compatibility tags):
- `http-user-agent` (User-Agent)
- `http-referrer` (HTTP referrer)

### `#KODIPROP:parameter=value`
Allows setting some custom parameters for the current channel (`KODI` compatibility tags). Supported `parameter` are:
- `inputstream.adaptive.license_type` (DRM type, can be one of the following):
  - com.widevine.alpha (Widevine)
  - clearkey (ClearKey)
  - com.microsoft.playready (PlayReady)
- `inputstream.adaptive.license_key` (License key or URL depending on the DRM type; URLs should start from `http://` or `https://`, otherwise it’s a non-url key) and is considered being static
  - license url for playready/widevine content
  - static key (or keys) for clearkey content. Example (1 key): `abc:def`, Example (multi keys): `{"abc":"def","klm":"opq"}`
- `inputstream.adaptive.stream_headers` (extra headers, if required. For example `param1=value1&param2=value2&param3=value3`) (`v1.6.4.1+`)
Syntax is generally compatible with KODI inputStream.Adaptive plugin declared at [xbmc](https://github.com/xbmc/inputstream.adaptive)

The app also accepts extra stream headers configured after `|` character in license_key (`v1.6.4.1+`)

### `#EXTATTRFROMURL:http://some/url/for/data.m3u`
`v1.6.9.2+`
If you wish to hide some sensitive tags from the playlist itself, or wish some of these tags to be generated upon request (like DRM keys to match the content), then you can specify this attribute targeting to your server service. App will make a request to this url when user going to play this channel/vod entry.

Sample response from your service should look something like this:
```
#EXTINF:-1, Demo channel
#KODIPROP:inputstream.adaptive.license_key=...
#KODIPROP:inputstream.adaptive.license_type=...
http://example.com/channel/02
```
Please note, that the app will also use the url to the content that is returned from your response rather the one you have in your playlist.

### A basic M3U file format sample
```
#EXTM3U url-tvg="http://example.com/epg.xml.gz"
#EXTINF:-1 group-title="Music", Music 1
http://example.com/channel/01
#EXTINF:-1 group-title="Sports", Sports News
http://example.com/channel/02
```

## OTC playlist format
`1.6.9.3+`
As a good alternative to `m3u` format you can also use `otc` format encoded in `json`.

### OTC playlist format provider properties
- `"epg": "url/to/epg.xml.gz"` - url for `xmltv` teleguide
- `"archive_days": 3` - number of days of archived (`catchup`) records are available
- `"archive_type": "default"` - see `catchup-type` in `m3u` format description
- `"refresh_minutes": 30` - how often to reload this playlist
- `"max_connections": 2` - maximal amount of connections for the user that is allowed to watch at the same time
- `"billed_till": 214363576` - unix time when user account will expire (will be displayed for user)
- `"user_message": "HI"` - custom message regarding user account (might be balance or any other info to be shown)

### OTC playlist format category properties
- `"name": "Sample Category"` - name
- `"icon": "url/to/category/icon"` - icon of the category
- `"adult": 1` - set to `1` or `true` to mark this category as adult

### OTC playlist format provider properties
- `"category": "main"` - id of category declared earlier in this json
- `"name": "Sample Channel"` - name
- `"number": 123` - channel number
- `"epg_id": "ch27"` - channel id in `xmltv` teleguide that corresponds to the current channel
- `"epg_name": "Correct Channel Name"` - if you fail to specify exact `epg_id` you can also try to specify alias for the channel name to the one that you believe will have data in `xmltv` teleguide
- `"epg_shift": 2` - shift program from `xmltv` teleguide by this amount of hours
- `"icon": "url/to/icon` - channel icon
- `"archive_days": 3` - number of days while archived shows are available
- `"archive_source": "source/url/format"` - check `catchup-source` in `m3u` format description
- `"user_agent": "Chrome.."` - allows to set custom `HTTP User-Agent`
- `"referrer": "some/url"` - allows to set custom `HTTP Referrer`
- `"drm_type": "widevine"` - check `inputstream.adaptive.license_type` in `m3u` format description
- `"drm_key": "abc:xyz"` - check `inputstream.adaptive.license_key` in `m3u` format description
- `"drm_url": "url/for/drm/provider"` - check `inputstream.adaptive.license_key` in `m3u` format description
- `"headers": "..."` - check `EXTHTTP` or `inputstream.adaptive.stream_headers` in `m3u` format description
- `"runtime_attr_url": "custom/url/for/getting/tags/at/runtime"` - check `EXTATTRFROMURL` in `m3u` format description
- `"url": "url/for/stream"` - url to the stream that should be played

### Simple OTC playlist sample
Basic structure looks like:
```
{
  "provider": {
    "epg": "url/to/epg/xml.gz"
  },
  "categories": {
    "main": {
      "name": "General channels"
    }
  },
  "channels": [
    {
      "category": "main",
      "name": "Sample Channel 1",
      "url": "url/to/channel/stream"
    },
    {
      "category": "main",
      "name": "Sample Channel 2",
      "url": "url/to/channel/stream"
    }
  ]
}
```

----

## Media library file (json)
App supports multiple formats for media library, but preferred format is json:

### Inner structure of the item ("info" field of movie/series/season/episodes)
- on no data - can be not added
- rating - 0-10, might be decimal like 5.6
- added - date when added (unix timestamp)
- ttl - available till (unix timestamp) if will be removed at this time
- trailer - youtube trailer (link or the video ID part) `v1.6.6.9.5+`
- backdrop - larger image (usually a screenshot from a video) `v1.6.6.9.5+`
Sample:
```
"info": {
    "poster": "http://poster/image.jpg",
    "bg": "http://background/image.jpg",
    "plot": "Something happens...",
    "cast": [ "John Dow" , "Jane Dow" ],
    "director": [ "Mr. Smith" ],
    "country": [ "Zimbabve" ],
    "rating": "5.5",
    "year": 2019,
    "genre": [ "drama", "history" ],
    "added": 12354235,
    "duration": 3600,
    "adult": true,
    "trailer": "HGH34ghgAU",
    "backdrop": "http://video/image.jpg",
    "ttl": 12354235
}
```

### Outer structure of the json file
- if no data, do not add a field; "info" is also not obligated field anywhere
- category - not mandatory field (if specified, the item will be placed in the folder).. might be either a "MyCat" or a json like `{"name":"MyCat","icon":"http:/..jpg"}`
- field "video" means it's a movie, "season" means it's series
- for episode "duration" in seconds
- "name" is episode name (if applicable)
- episodes and season numbers are not mandatory if they are listed incrementally (1, 2, 3, ..)
- if the item contains the link to the video using `video` tag, you can also pass additional parameters (`v1.6.6.7+`) like you do using `m3u` format:
  - `"drm": "..."` to pass drm type (like clearkey, widevine, etc)
  - `"drmkey": "..."` to pass drm key (for clearkey) or drm license url (you can use `|` to pass additional headers to be only used for drm request)
  - `"headers": "header1=value1&header2=value2` to pass additional headers (will be passed both to drm request and video request) or JSON format `{"User-Agent": "Chrome", "SomeOtherAttr": "SomeValue"}` (`v1.6.6.9+`)
Sample:
```
[
{
    "name": "Test video",
    "category": "Action",
    "info": { ... },
    "video": "http://video/file.mp4",
},
{
    "name": "Test serial",
    "category": "Drama",
    "info": { ... },
    "seasons": [
        {
            "season": 1,
            "info": { ... },
            "episodes": [
                {
                    "episode": 1,
                    "name": "Intro",
                    "info": { ... },
                    "video": "http://episodes/file.mp4"
                }
            ]
        }
    ]
}
]
```

### full sample of json VOD libarary
```
[
{
    "name": "Test video",
    "category": "Action",
    "info": {
      "poster": "http://poster/image.jpg",
      "rating": "5.5",
      "genre": [ "drama", "history" ]
    },
    "video": "http://video/file.mp4",
},
{
    "name": "Test serial",
    "category": "Drama",
    "info": {
      "genre": [ "drama", "history" ],
    },
    "seasons": [
        {
            "season": 1,
            "info": {
              "genre": [ "drama", "history" ],
            },
            "episodes": [
                {
                    "episode": 1,
                    "name": "Intro",
                    "info": {
                      "plot": "Something happens...",
                      "cast": [ "John Dow" , "Jane Dow" ]
                    },
                    "video": "http://episodes/file.mp4"
                }
            ]
        }
    ]
}
]
```


----

## Default app user-agent
User-Agent used by the app by default is `OTT Navigator/VER (Linux;Android ANDVER; LOCALE; HASH) CODECINFO` where:
- `VER` is app version like `1.6.8.3`
- `ANDVER` is android version
- `LOCALE` (optional) is a language set in the app
- `HASH` (optional) is installation identifier, should be quite unique between devices (may not always be passed)
- `CODECINFO` (optional) is information about the currently used codec for the channel (if it is a stream request), may contain something related for the codec used, for example when using hardware codecs will be something like `ExoPlayerLib/2.15.1`

Please note that this attribute might be modified by user, provider attributes in playlist or provider API (portal uses different agents)

----

# More information

## Changelog
Changes are published on [Telegram](https://t.me/ottnav) or [on web](https://ottnav.github.io/changelog.html)

## `OTT Navigator` app Availability
### Standalone version of the app
- Not linked to any store
- Premium can be purchased and managed using `OttNav Companion` app
- [Direct download of OTT Navigator](https://app.ott-nav.com/dist/std/latest.apk) (you will need to allow installing apps from unknown sources on your device)
- Code for `Downloader` app is `982469`.
- Allows switching between `stable`, `beta` and `alpha` update channels

### Google Play
- [OTT Navigator at Google Play Store](http://bit.ly/2PQEAVf)
- Payments managed via the store
- Accessing `beta` update channels via [subscribing to Beta versions on Play Store](http://bit.ly/2PrwwcH)

### Huawei AppGallery
- [OTT Navigator at Huawei AppGallery](https://bit.ly/2WHhIvQ)
- Payments managed via the store

### Versions for old devices not longer supported
- for `Android 4.x` latest version is `1.6.4.4` [google](https://app.ott-nav.com/dist/std/latest4.apk).
- for `Android 5.x` latest version is `1.6.7.7` [standalone](https://app.ott-nav.com/dist/std/latest5.apk).

## `OttNav Companion` app for managing premium account, sub-accounts (for standalone builds)
- [OttNav Companion at Google Play Store](https://play.google.com/store/apps/details?id=studio.scillarium.ottnavigator.companion)
- [OttNav Companion at Aptoide](https://ottnav-companion.en.aptoide.com/app)

## Contacts
- [Support chat on Telegram](https://t.me/ottnav_global)
- Contact the developer directly at `scillarium.studio@gmail.com`
- White label / branding contact `ottnav.partners@gmail.com`
- [Reddit](https://www.reddit.com/r/)
- [Privacy Policy](http://ott-nav.com/privacy_policy.html)
