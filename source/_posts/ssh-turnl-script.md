title: SSH tunnel script
link: http://blog.wangyaodi.com/2009/11/03/ssh-turnl-script/
creator: yorzi
description: 
post_id: 13
post_date: 2009-11-03 18:24:13
post_date_gmt: 2009-11-03 10:24:13
comment_status: open
post_name: ssh-turnl-script
status: publish
post_type: post

# SSH tunnel script

Why SSH tunneling? Obviously, if you live in Chxna or some other place where you are restricted to access free network, and if you luckily own a ssh accessible account on a server that is hosted in a free country, congratulations, you can use ssh tunnel to fuck the wall. Seriously, you just need to install ssh tool on your PC, (it will be much easier to setup a ssh tunnel if you are using a *nix OS), putty is a good choose if you are on Windows. I will show the script to explain what you should do on Ubuntu 9.04. 
    
    
       ssh -qTfnN -D LocalPort remotehost(dreamhost)
    

` All the added options are for a ssh session that’s used for tunneling. -q :- be very quite, we are acting only as a tunnel. -T :- Do not allocate a pseudo tty, we are only acting a tunnel. -f :- move the ssh process to background, as we don’t want to interact with this ssh session directly. -N :- Do not execute remote command. -n :- redirect standard input to /dev/null. In addition on a slow line you can gain performance by enabling compression with the -C option. ` Enjoy it.