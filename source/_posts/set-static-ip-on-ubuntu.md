title: Set static IP on Ubuntu
link: http://blog.wangyaodi.com/2009/11/11/set-static-ip-on-ubuntu/
creator: yorzi
description: 
post_id: 62
post_date: 2009-11-11 11:03:40
post_date_gmt: 2009-11-11 03:03:40
comment_status: open
post_name: set-static-ip-on-ubuntu
status: publish
post_type: post

# Set static IP on Ubuntu

Edit: `sudo vim /etc/network/interfaces` Then change the content, assuming you want to set your IP as "192.168.1.66" `# The primary network interface auto eth0 iface eth0 inet static address 192.168.1.66 netmask 255.255.255.0 network 192.168.1.0 broadcast 192.168.1.255 gateway 192.168.1.1 ` Then to restart your network. `sudo /etc/init.d/networking restart`