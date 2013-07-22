---
layout: post
title: Set static IP on Ubuntu
categories:
- Tech Notes
tags:
- ip
- network
- tech
- ubuntu
published: true
comments: true
---
<p>Edit:
<code>sudo vim /etc/network/interfaces</code></p>

<p>Then change the content, assuming you want to set your IP as "192.168.1.66"
<code># The primary network interface<br />
auto eth0<br />
iface eth0 inet static<br />
        address 192.168.1.66<br />
        netmask 255.255.255.0<br />
        network 192.168.1.0<br />
        broadcast 192.168.1.255<br />
        gateway 192.168.1.1
</code></p>

<p>Then to restart your network.
<code>sudo /etc/init.d/networking restart</code></p>
