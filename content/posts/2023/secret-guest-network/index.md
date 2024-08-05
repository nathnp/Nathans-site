+++
title = 'The Secret Guest Network'
date = 2023-10-22T22:52:29-05:00
draft = false
subtitle = 'They will never know'
tags = ['Networking']
+++

Imagine this, you have some people over, and they want the password to your WiFi. You trust them, but not “you can be on my network” trust them. So you give them the guest network login. They get mad and leave, and now you're down a couple friends. But what if you could have a hidden guest network, that looks just like your main one, maybe that would let you keep some friends.

Ubiquity has rolled out support for PPSK (Private Pre Shared Keys). That let's you have multiple networks, behind one SSID. This is handy, as having too many SSIDs can hurt performance. 

What PPKS does, is let you automatically put a host on a VLAN, depending on what password they use. For example, let's say we have a WiFi network called "BullsEyeWiFi". We can set up PPSK so that anyone who uses the password "GoodPassw0rd1!", will be put on VLAN 1. And anyone who uses the password "Playground", will get put on VLAN 2. 

Now that's a pretty business example. A more home user example would be: Having a segregated guest network, on the same SSID as your main one. This way, you can put your house guests on a guest network, without them having any idea. And thus, keeping them as friends.

![](fig1.webP)

Here's a good video from Cameron Gray Going over PPSK on UNiFi. And its downside (It doesn't work on WPA3 networks (That includes 6GHz networks)).

https://www.youtube.com/watch?v=DvhU7roLviY&t=1228s