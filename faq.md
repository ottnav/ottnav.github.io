# Installation

## How to install on non-Play Market device
- If you are running Huawei device, then use Huawei AppGallery to install the app
- If you are using Amazon device then use Aptoide market to install the app
- Alternatively you can sideload the app

## How to install on my Windows PC/Mac
There is no special version dedicated to be used on Windows PC or Mac, however, there is a solution to use the app with negligible side effects.
Install NoxPlayer app on your PC - it allows running Android apps and is highly optimized and recommended.
Just use it like it was a native app.Some users are running the app on different emulators, like BlueStacks emulator and report that it also works quite well, and supports later Android versions.
Please note, that hardware acceleration might not be available when using emulator, so you might need selecting software codecs to watch your content.

## Will the app work on my TV? Why not WebOS/Tizen?
The app only works on Android, so if your TV is running Android TV / Google TV then it will run perfectly.
We have investigated the tech and even did some proof-of-concept, but WebOS/Tizen are simply not powerful enough to make a really good app. It's suitable for simple web pages that pretend to be apps, but lack real power to do complex under-the-hood tasks.
So if you choose an LG/Samsung TV (the only 2 major vendors that do not use Android these days) - then it's highly recommended to purchase an Android / AndroidTV / GoogleTV / Chromecast(2021+ model) / FireTV / etc box or stick to be attached, to make it really smart (not smart by name).

# Provider (playlist) configuration

## Playlist file setup
Your options are one of the following (it’s always preferred to use links over files):
- Use a specialized service like `https://m3u4u.com/` or `https://app.m3u.in/` to upload your playlist and configure a link to it
- Upload file contents to a `https://pastebin.com/` (always make paste exposure to unlisted) and use RAW link to the playlist
- Use any cloud storage service you prefer. For example, when using Dropbox:
  - Copy a playlist file to your personal Dropbox cloud storage
  - In a context menu select `Dropbox -> Copy Link`
  - Open a text editor and paste a link there; replace `dl=0` to `dl=1` in the link (since by default it copies a link to the web page rather than to the file itself)
  - (Not recommended) copy file to Downloads directory, so the app will see it. However, file access is being limited in Android from version-to-version, and especially on Android TV devices, so better use any of the cloud storage.
  - (For admins) make a web server in the local network that is bind to host “iptv.local” and ensure that your playlist is available by HTTP request to `iptv.local/playlist.m3u` and the app will auto-detect the playlist
  - Also you can setup the player on your phone (not using files, links only!) and then use the backup/restore feature of the app to transfer configuration to your TV/box device!

## Which provider template should I choose?
- If your playlist contains something like `.../get.php?username=...&` most probably your choice is Xtream Codes template
- If the url contains something like `/stalker_portal/c/` then you should select either MAC or Stalker portal
- If you have a m3u file downloaded from provider, you should either upload it and setup as a Playlist (recommended), or configure as a Playlist File
- In other cases configuring as Playlist is generally preferable

