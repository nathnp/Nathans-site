+++
title = 'My Home Lab'
date = 2023-12-05T16:05:33-05:00
draft = false
tags = ['Networking', 'Home Lab']
+++

I've had a small home lab for a bit. Servers have come and gone, but a few core ones have remained. So let's talk about it, and my home network as well.

# Network

Let's start with the network, as that's the backbone of the everything.

I'm pretty much all in on UNiFi for networking. My main router is a [UNiFi Dream Router](https://ui.com/us/cloud-gateways/dream-router). The UDR is a home and small business router. With the usual built in switch (though two of the ports are POE), and wireless access point.

The UDR, also controls two dedicated access points. One being a U6-LITE, and the other being an older AC-PRO. This allows me to have one, seamless, multi AP WiFi network. That covers the whole house. Though all of my lab server are hooked up over gigabit ethernet.

# Home Lab

My home lab, is made up of four main servers. My NAS, DNS, Home Auto, and Virtualization.

### NAS

My NAS is a [Synology DS418](https://global.download.synology.com/download/Document/Hardware/DataSheet/DiskStation/18-year/DS418/enu/Synology_DS418_Data_Sheet_enu.pdf). Its an older four bay NAS. It's main use is as file storage (duh), movie serving, and as a backup target for my Mac.

A NAS is so simple, it can be kinda hard to explain. Think of it like a giant flash drive. That any computer on the network can access. Provided they have a login. A NAS can also protect your data. If the drive in your computer dies, any data you backup to the NAS, will be safe. And even if a drive in the NAS dies, no data will be lost (if you have RAID set up correctly).

A NAS can also do fancy stuff, liking being the storage for a separate VM server. The VMs may get executed on one server, but all their files live elsewhere on the network.

### DNS

My DNS server is a Raspberry Pi 4 running [Pi-Hole](https://pi-hole.net). Pi-Hole is a network wide ad blocking server. It's one of those server, where you just set and forget. The only main thing about the set up, is that a number of guides tell you to set the Pi-Hole's IP, as the DNS on each of you devices. This is quite simply, shit. And really screams "I don't know networking". What you really want to do. Is set the Pi-Hole's IP as you DNS server, on your DHCP server[^1] (usually that's part of your router). That way, every device on your network, will automatically use the Pi-Hole. 

The Pi my Pi-Hole is running on, also has a USB to M.2 SATA board as its boot drive. I've had a number of SD cards and USB stick killed from Pi-Hole's logging.

### Home Auto

My home automation server, is really more of a protocol translation server. I mainly use Apple HomeKit for everything. Automations, and manual setting of devices. The only issue is, I have a number of devices that won't natively connect to HomeKit. Enter, [Home Assistant](https://www.home-assistant.io). Home Assistant manages all of my Z-Wave devices, passing their state to HomeKit. That's really it.

I did use to use Home Assistant as my dedicated home auto server. But back then, Home Assistant wasn't all that stable. It would work just happily for years, until it would shit the bed. While HomeKit is far less powerful, it's also far more stable. That's a trade off I'm fine with making.

My Home Assistant server runs on a Raspberry Pi 3+. 

### Virtualization

My virtualization server, is an old ass Dell OpitPlex running [ProxMoX VE](https://www.proxmox.com/en/proxmox-virtual-environment/overview). The fact that it's old doesn't really bother me, as I only need one or two VMs running at a time.

The main perk of a VM server, is that it let's you offload running a VM from your local machine. This is great if you just don't want to tank your laptop battery. Or your main computer is an ARM system, like mine. In that case, you can't easy run an x86 VM. So having a VM server fixes that downside of daily driving an ARM computer. 

This is a my newest server. So I'm still building a core use for it. But it has come in handy for demoing different Linux tools students.

The VM server runs on a second gen Intel Core i7 4C/8T, with 16GB of ram.

---

Like any home lab, this thing is always changing. Servers have come and gone. One of the old ones I used to run was a Raspberry Pi based Minecraft Java server. Might do a post on that one. I wonder what my lab / network will look like in a few years.

[^1]: Make your you set it as your DHCP DNS address, and not the DNS that the router will try to use. Some ISPs won't give you an IP unless you have the router set to their DNS, looking at you Comcast. 