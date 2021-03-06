---

layout: post
title: How to connect to Google Starbucks wifi using i3 and Arch Linux
date: 2017-10-20
comments: true

---

If you are new to i3 and find yourself having trouble connecting to wifi networks in new places, you have come to the right article. 

I was recently at a Starbucks and couldn't connect to the open `Google Wifi` network. Coming from Gnome Desktop, I have been having to learn how to do things the i3 way. Simple things like connecting to new wifi networks require new approaches. 

If you install the `dialog` package, you can use `wifi-menu` to view available networks and select which network you want to join. This didn't work when I recently tried to join a Google Startbucks wifi network. There is a a simple CLI tool for `NetworkManager` called `nmcli` that you can use to join networks. 

Here is how to scan networks with `nmcli`: 

```terminal
[brian@archthinkpad ~]$ nmcli d wifi list
*  SSID                  MODE   CHAN  RATE       SIGNAL  BARS  SECURITY    
   --                    Infra  11    54 Mbit/s  94      ▂▄▆█  WPA2 802.1X 
   Google Starbucks      Infra  11    54 Mbit/s  89      ▂▄▆█  --          
   Google Starbucks      Infra  48    54 Mbit/s  87      ▂▄▆█  --          
   --                    Infra  48    54 Mbit/s  87      ▂▄▆█  WPA2 802.1X 
   --                    Infra  1     54 Mbit/s  75      ▂▄▆_  --          
   Einstein Bros Bagels  Infra  1     54 Mbit/s  75      ▂▄▆_  --          
   --                    Infra  1     54 Mbit/s  75      ▂▄▆_  WPA1 WPA2   
   --                    Infra  1     54 Mbit/s  72      ▂▄▆_  WPA2        
   Einstein Bros Bagels  Infra  161   54 Mbit/s  60      ▂▄▆_  --          
   --                    Infra  161   54 Mbit/s  59      ▂▄▆_  WPA1 WPA2   
   xfinitywifi           Infra  153   54 Mbit/s  40      ▂▄__  --          
   XFINITY               Infra  153   54 Mbit/s  40      ▂▄__  WPA2 802.1X 
   CoxWiFi               Infra  153   54 Mbit/s  39      ▂▄__  --          
   CableWiFi             Infra  153   54 Mbit/s  39      ▂▄__  --          
   XFINITY               Infra  11    54 Mbit/s  27      ▂___  WPA2 802.1X 
   ZM7JQ                 Infra  6     54 Mbit/s  24      ▂___  WPA2      
```
And here is how to connect to the `Google Starbucks` network. 

```terminal
[brian@archthinkpad ~]$ nmcli dev wifi connect Google\ Starbucks
Device 'wlp3s0' successfully activated with 'da3af242-4707-42f0-81c8-6f8b9dc1a0f7'.
```

You can read more about `nmcli` on the [Arch Wiki Network Manager article](https://wiki.archlinux.org/index.php/NetworkManager). 


