# OTT Navigator Changelog

# 1.6.6
## 1.6.6.1 (not yet released)
- vod dirs: mass hide action
- config: remote: disable 0-9 for channel switch
- config: show ip address on home screen
- new wallpapers
- allow folding categories under a different category, effectively grouping multiple items
- duplicates: option to merge by name within category, or merge by epg, in addition to the default global name match
- stalker: fixed epg loading for some providers
- long pressing right button in lists shows description of the item in a popup
- playlist: support header tag refresh=”N” for specifying channels auto-refresh timer
- category: more icon type variants
- channel browsing has extra layer for quick switching content
- duplicates: allow user to setup list of preferred suffixes for folding
- desc: option to remove most of the sections other than text description
- config: prefered audio/cc track language
- stalker: support and integrate vod search in global app search
- tvguide: unified touch and non-touch versions
- config: launcher mode: do not exit by pressing back from the app (and use double-back to exit from player)
- config: allow disabling left and bottom bars on home screen
- sort: fixed sort by number with huge lists
- chromecast: fixed button not appearing on some devices
- studio: more maximized sizing options
- category: move multiple channels to a different category
- xc: allow overriding stream tech in provider props
- config: disable recently added channels category

# 1.6.5
## 1.6.5.5 (2021-03-15)
- config: disable recently added channels category
- preview: setting on how fast preview should start
- rc: allow binding ch+/ch- buttons
- live: allow marking any channel to auto-start on app launch
- vod: user can manually add a stream link that will be added to the library (until app restart)
- lists: show category name larger now has 3rd value - do not show at all
- home: can mark any category to be shown on main screen
- phone: setting to toggle nav bar
- side-by-side: left button on category from player switches providers
- provider prop: disable video preview
- lists: config split to style and columns, allowing more control
- new themes: 10 theme (each 3 variants)

## 1.6.5.4 (2021-03-08)
- search optimized for huge lists
- dropped android 4.x support, it gives too much problems for a long time already and limits way too much
- new themes: 9 themes (each has 3 variants: solid, glass, transparent) plus an option to setup random, and added accent colors to all themes to highlight some data
- phone: better defaults for player (and +1 menu type)
- remote key configurable: menu (long)
- player action: open categories

## 1.6.5.3 (2021-03-04)
- new list view type: side-by-side
- provider: optimized applying channels for huge lists or many providers
- home: moved studio button to bottom of the launcher window and added access to search/settings from it
- player action: last channel should switch to recent as well
- quick provider switch: available from the categories, and can be configured to retain favorite channels even if belongs to filtered provider

## 1.6.5.2 (2021-02-27)
- brightness should apply to whole interface in addition to the playback screen
- remote control: media next/prev buttons to switch archived shows
- search: filter vod by provider
- fold duplicates: improved switching sources while playing archives
- player: on/off track tunneling (on global and channel level
- player action: switch duplicated source (and switching source should not mark previous as last channel)
- use case-insensitive sorting in channel/categories manage
- child mode: exit button asks for code and if correct -- exits the child mode. if the code matches restrict code, it also unlocks restricted mode
- player menu: narrow cards option

## 1.6.5.1 (2021-02-19)
- epg: take data from duplicates if the current source lacks one
- vod: recently added filter (14d) for providers that allows indexing and provides timestamps
- config: keep hud displayed while menu is on
- config: player hud menu position on top and bottom edges (also moves hud if overlaps it)
- playlist: support for http basic auth in playlist url
- new player hud type at bottom edge
- studio: up shortcut to switch channel, long back to switch exit
- pip: more position and size options
- channel sort: support country prefix removal
- player bindable action: show current broadcast info (defaults to long ok, or double tap in center)

# 1.6.4
## 1.6.4.4 (2021-02-09)
- epg: fixed a case when first-day shows might get duplicated. Also show epg loading status on main screen
- ftp support for epg sources
- provider props: can add up to 3 epg sources and disable builtin sources by provider
- setting to prefer highest/lowest track quality by default
- category mass action: set codec for all channels
- remote: can change back button behavior in player
- vod screen: setting to switch between global search and local (letter-by-letter)
- sorting: can set custom sort mode in each category
- afr: option to set to fixed resolution other than default
- fold duplicates: improved list positioning after source change
- studio: extended memory slots to 9 (and show channels in slot)
- stalker: improved retries in pip and studio for
- lists: fixed sort order by provider being broken after adding new provider
- wallpaper: fixed timed rotation if random
- search: save recent successful search queries
- zoom: allow to set custom aspect ratio on channel (scale by X coordinate)
- player bindable actions: sleep timer, exit playback, reload channels
- list type: compact (1+1)
- archive: support next/prev touch buttons even when no epg is available

## 1.6.4.3 (2021-01-27)
- tracks: added support for switching audio tracks for some providers
- afr: probably fixed low-fps channels switching
- video preview: allow changing codec (and show quality info if configured to show as numbers)
- provider props: drop all channels to single category
- vod: can toggle item description, select list type from list, cards, small 
- stalker: fixed archive detection for some portals
- search revamped, improving access to item properties, live customization, filtering by provider, grouping by type, and searching by vod directories
- quick channel switch: more delay options
- player: add some stream details to non-default codecs (system and vlc), and to vod player
- more backgrounds added

## 1.6.4.2 (2021-01-15)
- epg: switch to single threaded mode (slower but less impact)
- epg: cleanup data button
- list: extra narrow cards
- fixed most cases with time jumping backwards when watching archives on some providers
- drm: support for multikey clearkey streams
- stalker: fixed vod names when using locale unsupported on portal
- xc: support is_adult tags for video and live

## 1.6.4.1 (2021-01-07)
- usability: simplified hiding of multiple channels/categories at once
- stalker: support more portals when getting sub expire date
- drm: improved clearkey support
- codec: allow setting system by default
- playlist: support adult tag for filtering channels
- playlist: support inputstream.adaptive.stream_headers for DRM requests
- restrict: assume adult channels restricted by default
- restrict: can lock access to settings
- list: compact (narrow) style
- xc: split series episodes by seasons
- stalker: separate series and movies in vods (and adult filtering improved)
- config: bindable action to change codec
- config: ask when leaving archive video playback
- config: use channel position in a category as channel number (so multiple channels from different categories might have share number)
- launcher: prefer phone icons over tv banners for external apps
- phones: improved support for screen cutouts

# 1.6.3
## 1.6.3.8 (2020-12-18)
- Item description: show some previous show info as well if channel has archives
- cache: fixed app some metadata not resolved when restoring channels
- vod: support DRM media library items playback

## 1.6.3.7 (2020-12-05)
- player: added support for DVB image subtitles
- search: prioritize whole word matches in archive results
- config: setting to select and use fixed resolution/fps within the app (disables afr)
- stalker: improve epg update
- manage: setting to restrict changing channel/category properties
- wallpaper: do not cache user-configured background if it has query params (like ?..) to allow refreshing image remotely
- playlist: support billed-msg header tag for custom account-related message from provider
- reopen last channel now can reopen last archived show as well
- playlist: fixed useragent/referer apply for vod items in channels playlist
- config: allow editing of custom epg/vod sources

## 1.6.3.6 (2020-11-24)
- codec: updated vlc to 3.3.2, should improve its performance
- player: show HUD when tv-show is changed
- player: night mode setting with decreasing blue color filter
- config: delay before retrying channel
- playlist: more cleanup of bad characters in channel names

## 1.6.3.5 (2020-11-11)
- epg: optimize load speed with multiple channels matched
- vod: defer provider load until channels are being read not from the cache
- epg: restrict max data request for xc providers to 7d
- vod: fixed attributes parsing in some common user-provided sources
- playlist: file fix for older android versions

## 1.6.3.4 (2020-11-01)
- stalker: allow disabling genres in media library (and use everything) in provider properties
- stalker: for providers with batch epg support, also load archived shows records
- player: do not remove restricted channels from quick switch
- epg: more filtering on invalid incoming data from sources

## 1.6.3.3 (2020-10-26)
- stalker: extended support for some portals giving no handshake
- provider enable/disable should only patch the current provider, not reloading the whole list
- goodgame: more frequent channels refresh
- wifi: added option to send to tv for vod player
- config: how long restrict should be unlocked
- config: N of previous shows to display in desc
- config: do not show poster in desc
- dnla: some tvs support expanded
- vpn: several fixes when working under limited connection (and added config to limit duration for network become online)
- epg: added sanity checks for invalid incoming epg data

## 1.6.3.2 (2020-10-17)
- backup: supports local store/load (note that it is not guaranteed to load backup file that is 1y old)
- brightness change via menu should work on any device
- fixed restricted channels unlock without a code
- epg: further epg performance tuning (in addition to the work done in 1.6.3.1

## 1.6.3.1 (2020-10-13)
- epg: add virtual records when channel only has partial epg data for archived records
- epg: loading heavily redone. might take a bit longer while applying but should make much less impact on the device while loading in progress, and intermediate - - results while in loading can work even while loading. should resolve multiple loading issues.
- android tv: use smaller desktop icons, and use fallback icons if top favorite channels do not have one
- stalker: allow user to override useragent (via provider parameters)
- config: lists toggle whatever to use spacing between elements
- config: option to disable mediasession integration (since some devices with firmware issues are popping out notification while in playback)
- provider cache: try to reuse list of channels from the cache (on launch) while still loading the current list from providers. should greatly speed up initial access, but might not work with some providers well (can be turned off)
- player action: change screen brightness (also available in playback params)
- playlist: parsing speed improvements
- future epg: option to auto-switch to the channel when show will be live
- player action: start studio mode
- dnla: improved support for windows upnp server
- vod: support user-agent/referrer for user-provided m3u playlist

# 1.6.2
## 1.6.2.8 (2020-09-11)
- premium: added restore purchase action trying to fix play store cache issues with activation (settings-premium-restore)
- dnla: better support for windows dnla server
- provider attr: do not show expire info
- config: lists: always use 1 click to open (air mouse)
- channel duplicates: obey quick switch disabling a provider
- stalker: better support for external channel icons
- backup: can choose what to restore (provider, settings, metadata, or everything)
- long home live icon tap action to reload list of channels
- preview: more correct aspect ratio
- lists: fixed clear manual position not being applied to categories

## 1.6.2.7 (2020-08-21)
- vod: allow marking favorites to any folders (search subfolders supported as well)
- vod: refreshed ui, moved description to additional screen (configurable)
- stalker: support for portals with tv-series
- player hud: show number of tracks by type
- vod: support for search folder/action provided by some user-configured xml/json sources
- background: allow user-specified image (url)
- lists: 2 and 3-column mode
- enabled channel numbers to 10000
- search: extended limit for max results (was too restrictive)
- config: disable subtitles
- volume: process key down if system has non-default volume levels
- playlist: support for some playlists that has series/vods bundled with the list of channels
- fixed timetable skipping current show for channels without archives

## 1.6.2.5 (2020-08-10)
- category props: allowing to hide/restrict multiple channels at once
- stalker: better support for some vod providers
- list: tiny cards

## 1.6.2.4 (2020-08-01)
- studio: support playing archives
- preview: support most stalker/mac portals
- androidTv: support mediasession to report stream info to the system
- player: menu: quick open similar shows from archives (if any found)
- player: fixed zoom when using system view
- config: switch between slower (compatible) and fast rewind methods for catchup (default to fast seek for this beta)
- stalker: more support for some custom protocol vod items
- search: global search does not stop after launching an episode to preserve state
- config: list view as large/small cards
- config: can select a wallpaper (defaults to random for this beta)
- config: turn animations on/off
- config: use r/l arrow buttons as pgup/pgdown (instead of long press)
- epg: support some more odd time formats
- allow quick day switch in timetable view
- fixed loader screen not stopped sometimes

## 1.6.2.3 (2020-07-19)
- many ui lists redone for better navigation (multi-column mode is not yet supported!)
- vod: sometimes failed to seek to last known position on start
- translation: Serbian
- chromecast: multiple playback state and connectivity fixes
- playlist: added more support for #KODIPROP tags
- config: split settings to simple/normal/expert for easier navigation

## 1.6.2.2 (2020-06-26)
- player: better support for some incorrect HLS manifests with missing tracks info (enabled for compat hardware codecs quality)
- player: support smoothstreaming (ism)
- vod: fixed supports for some json sources
- player: allow holding volume buttons when using manual volume control

## 1.6.2.1 (2020-06-19)
- vod: save and restore watch position
- backup: fixed failing on some playlists
- epg: support some sources with uncommon date format used
- provider params: setting to replace provider order by alphabetical
- player: do not sort player menu items too often (freeze during a launch)
- some fixes to decrease chance that provider changing api/playlist internals causing losing some channel-related settings (like favorite/order/etc)
- archive: better save and restore playback position
- archive: fixed navigating through some virtual directories
- seek: fixed progress jumping on seek (also sometimes leaded to switching tv-show)
- stalker: fixed vod by cmd with a proxy link (on some portals)

# 1.6.1
## 1.6.1.6 (2020-06-07)
- search: improved search within the app, combining all search sources together
- stalker: support providers with vods with genres declared but not assigned
- stalker: optimized indexing and data loading
- vod: start indexing faster upon launch
- config: disable modules if not using them (archive/vod/studio)

## 1.6.1.4 (2020-06-01)
- icon: dynamic app shortcuts now obeys favorites order
- stalker: extended support for some MAC portals
- stalker: extended support for several vod series configuration

## 1.6.1.3 (2020-05-30)
- category properties: mass add to category action should retain focus while operating
- category properties: mass action to set numbers for all channels in a group (sequently)
- dealer panel: make it easier to access (long tap on status line in settings-extended)
- playlist: support missorted modifiers to work still
- playlist: pass provider user-agent when downloading a playlist, not channels only
- config: allow setting long desc scroll speed (default to 70%)
- player: try to auto switch to the audio/subtitle track corresponding to current language

## 1.6.1.2 (2020-05-21)
- list: auto scroll long description
- remote: bindable action to toggle favorite status of current channel
- stalker: allow changing device_id2 via provider props
- epg: fixed channels with shift (+N) sometimes had gaps in timetable
- drm: support #KODIPROP playlist params

## 1.6.1.1 (2020-05-18)
- category: can change category type with icon
- player: bindable action: open previous category
- drm: improved widevine support
- xtream codes: better support for https lines
- vod player: zooming support
- xtream codes: easier switch from v2 api and v1 api
- chromecast: now supported
- stalker: allow setting sn/device_id for your connection
- player: on channel error try to open previous channel rather than first in group
- player: bindable action to block screen controls
- vod player: recommend external player on playback error
- config: whatever favorite channels should be listed first
- lists: remember user-selected preferred channel if duplicates folding enabled
- stalker: better report of error occurred during auth
- player: auto-keep brightness level set in the same app session between screens
- config: disable offering to seek to last known position

# 1.6.0
## 1.6.0.3 (2020-04-20)
- vod player: menu option to auto start next episode on finish
- epg reload: support connecting to current updating epg session when trying to reload while loading
- config: ignore ssl errors
- list: removing sd channels when hd also applies to non-suffix channels
- player: when player error occurs in archive, try to retry from the same time
- config: disable provider epg sources
- remote: long left/right buttons acts as pgup/down in generic lists
- provider: allow setting referrer for provider (not supported in vlc codecs), and support for #EXTVLCOPTS:http-referrer tag in playlist

## 1.6.0.2 (2020-03-25)
- support for internet providers with playlist on iptv.local
- use more natural sort order for lists
- config: player rewind speed (remote)
- vod: allow hiding content (via properties)
- fixed live progress not visible on some themes
- codec: allow setting default codec to use system video view (might be buggy)
- duplicates merge: improved combined favorite status, weight and sorting
- stalker: speed up media library load on app start
- vod: remove duplicates entries in search

## 1.6.0.1 (2020-03-19)
- vod: internal player available and used by default (configurable)
- lists: desc: change transparency for description view setting
- lists: fixed categories not sorted alphabetically
- tvguide: auto unfold current element info setting

# 1.5.9
## 1.5.9.5 (2020-03-15)
- config: lists: sort archives by date
- vod: support for user source in some json formats (and support load on opening for large collections)
- about: show installation number as qr code
- androidtv: protect against duplicate channels

## 1.5.9.3 (2020-03-09)
- tvguide: better support for huge categories
- tvguide: remote version redone for better focus control and scrolling (also allows scrolling horizontally)
- pip: reopen last: will also try reopening last pip channel
- retry: when channel errors reached limit, switch to first channel in group instead of stopping
- fold duplicates: share same favorite status, weight and number
- autostart: try to start the app on device unlock in some cases (if enabled)
- search: optimized in-player search indexing on find action for huge lists
- androidtv: home channel for favorite/suggested vods
- epg: auto-retry on empty epg now limited to 1/8 of the configured epg reload rate
- config: player: assume long buffering as channel error

## 1.5.9.1 (2020-02-26)
- vod: reload each 24h (configurable) and manual reload action
- stalker: better support for MAC portals (use dedicated provider template for them)
- stalker: try to filter out empty vod categories
- vod: support custom source in xml format (will scan whole tree so will take a while to index)

# 1.5.8
## 1.5.8.6 (2020-02-18)
- cfg: list: fold similar channels to a single element
- cfg: bind action to change audio/video/subtitle track
- epg: allow to configure unlimited records
- stalker: properties allow setting epg shift

## 1.5.8.4 (2020-02-12)
- androidtv: config: split different content type to different rows
- archive: group shows by series in channels list
- config: action to drop custom channel ordering
- player: config: show black screen on channel switch
- vod: allow user to setup unlimited amount of vod sources
- preview: disable on restricted channels
- hud: config: show marker if currently playing archived video
- logo: use different colors for channel icons if not set
- epg: improved support for cases when matching by tvg-id leads to one channel and by name - to other

## 1.5.8.3 (2020-02-02)
- vod: config: show folders separately from videos
- config: time warp mode (view list of live channels like it was several hours ago)
- vod: long press option to select different player for playback
- vod: can mark video as favorite to have quick access to it via favorites section
- manage: add multiple channels to category at once
- vod: all category with every movie/series (might not work with some providers that requires loading data dir-by-dir)
- epg: show latest successful epg load info
- about: option to disable stats collection
- hud: updated playback hud info layout

## 1.5.8.2 (2020-01-22)
- player: zoom option to enlarge/shrink video
- provider: added xtream codes v1 middleware template (live/archive/vod)
- provider: quick menu option to reload list of channels
- manage: option to specify custom timezone for a channel
- player: allow setting sleep timer via playback parameters while watching
- player: fixed channel reminder while playing another channel
- player: fixed configured pause remote button not working in menu
- config: remote: allow configuring play/pause media button
- config: mark default values for remote and touch settings

# 1.5.7
## 1.5.7.2 (2020-01-12)
- live: when in no categories mode, auto open live stream selection on start
- ive: fix for returning from playback to adult category
- android tv: configurable options on launcher screen (on what content to publish)
- manage: renaming category to already existing name will move all channels to the new category
- manage: filtered channels should be sorted by name

## 1.5.7.1 (2020-01-06)
- lists: some cases fixed when categories are disabled
- picture-in-picture: ask when opening in channel in pip mode whatever to open on main or pip screen
- picture-in-picture: configurable buttons to enter/exit pip, and open last channel by default
- android tv: automatically add recent shows and channels to home screen
- android tv: show preview directly on home screen (if supported by provider)
- archive: support for dash playback, and catchup-type="flussonic-dash" tag
- tvguide: fix for skipping some data opening by binded key
- archive: support unpause for some providers requiring frequent reauth
