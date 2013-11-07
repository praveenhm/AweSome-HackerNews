Installing the media server and configuring,

XBMC:
- this is orginal media server with lot of hacks
- various installation available for windows, mac and jailbroken iDevice.
- I have installed it on Windows7,mac and iPhone.
- best way to configure the server is to install xbmc hub wizard. [hub wizard](http://www.xbmchub.com/blog/2013/05/26/how-to-instantly-configure-xbmc-with-the-xbmc-hub-wizard-beta-addon/)
- The hub wizard will configure most of the video addon required.
- The top hirearchy is Add-ons under setting.
- Each addon has a bunch of video addons, this should be installed and enabled.
- once this is done these video are available under videos.
- you can run xbmc on win or mac and remotely connect via remote app on iPhone, this can be mirrored on apple tv.



Plex:
- works as client/server model
- There is a bit o hack, apple tv DNS should be configured to the media server IP address.
- run the media sever on win or mac and use the iphone app to mirror on apple tv.


#### plex,

http://lifehacker.com/5991757/sho...theater-pc

For those still wondering about how/what/why Plex, here's a quick synopsis,
-  Plex is based on a client/server model, whereas something like XBMC does not separate those roles out. The benefit to this separation of roles is that you have a centralized library of your media that is synchronized across all clients, rather than separate libraries being maintained on each end point.
-  Plex will scrape meta info for your media automatically. It helps if you name your files according to conventions it understands. (This is where the post-processing features of SABNZBD/Sickbeard/Couch Potato come in handy.)
-  If you will NOT be transcoding your media for mobile devices, then your CPU requirements will be low. In that situation, all that PMS (Plex Media Server) needs to do is catalog your media and tell clients where those files are stored. Clients will then direct stream from the source.
-  Your media does not need to be stored on the same machine that PMS runs on.
-  You CAN have both PMS and the Plex client running on the same machine if you want.
-  If you WILL be streaming your content to mobile devices (tablets, phones, Roku), then you will need a more substantial CPU to do the transcoding. You will not have a good time running PMS on devices like the Pogoplug or lower-end Synology's if you're looking to transcode.
-  Your Plex library can be shared and accessed from anywhere using myPlex. You do not need to be at home / on the same network to access your content this way. There are no router configurations like port forwarding needed.
-  You can stream your media through a regular web browser via Plex/Web and myPlex, as well as through the Plex app on iOS/Android/Win8/etc.
-  For remote streaming, you'll want to have at least 2 Mbps for a decent experience. The higher your upload bandwidth, the better.
