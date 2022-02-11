---
layout: post
title:  "xxx"
date:   2023-12-07 23:49:52 +0100
categories: posts/hosting
author: Marvin Borisch
description: Have you ever wondered how to get your Jekyll blog on "the cloud"? This article will show you how to host Jekyll on Debian 11, set-up your domain using Nginx and secure it with SSL.
---
**Tech-knowledge needed:** Webdev basics

*This little stub is focussing on webdevs that have worked with SFTP and traditional webservers. I will explain how I got my website (the one you are currently reading) running on Debian 11. We are going step by step and will use: **Debian 11**, **Nginx**, **Lets Encrypt**. If you use any other Linux Distribution, this process might be diffrent than the one I am elaborating on here.*

## Step 0: Prerequisites
At first you will need to install your Debian 11. I host my website on Vultr. This tutorial is made to work on Vultr's Debian 11 Cloud Computing service. Feel free to google Vultr or use my referral code by clicking the banner. You probably can use any hoster, tho I recommend Vultr as it has a usage based payment modell and is one of the cheapest around.

<a href="https://www.vultr.com/?ref=9000947"><img src="https://www.vultr.com/media/banners/banner_468x60.png" width="468" height="60"></a>

You are also going to need a SSH client, a FTP Client with SFTP support and a code editor (or use the  cmd/ssh client and power up yourself with some VIM knowledge). This tutorial will use a FTP Client and a code editor as it is aimed for webdevs that are switching from classic GUI based to CMD step-by-step. I **might** make a alternative tutorial only using the SSH client using cmd input and VIM usage.

Once you've started your Debian 11 server and logged into via SSH and FTP, let's check some things:
You will start in the /root folder as you can see in your terminal `root@hostname:~#` or in your ftp in the server location `/root`. First thing we are doing for **safety reasons** is to add a new user, the one we are going to use doing all this.

Now it is time to create our working user.
```bash
sudo adduser username
```
Follow the steps the process is asking you. Set your password, re-enter it and maybe add a full name. You can leave the values empty tho. After that, we will need to add the user to the `sudo` usergroup in order to have full rights to install, rename, delete, change, ... stuff.
```bash
sudo usermod -a -G sudo username
```
Now your user should have all the rights needed. To check if that's true, we will now switch to the user and use a sudo command to check if that worked out.
```bash
su username
```
To change your user, and then use this sudo command as example to test your new powers.
```bash
sudo apt update
```
It should ask you for your password and when the update is finished you should get a 
```bash
All packages are up to date
```
Now let's dive in into the fun!

**NOTE:** *If you ever run in any permission problems, make sure to give the directory the 774 (or 664) persmission.*
```bash
sudo chmod -R 664 foldername
```

## Step 1: making Jekyll ready for hosting

First of all, for comfort reasons and to prevent accidental overriding of important files, we will add this line into your `_config.yml` of Jekyll. I always put it below the `url: "https://yourdomain.com"` but you can probably put it anywhere in the block.

```yml add this line
destination: "../html/"
```
```yml my example
...
# in the templates via {{ site.myvariable }}.

title: coppnic
email: xxiv-vii@e.email
description: < the personal Zen Garden of a 24/7 busy brain >
baseurl: ""
url: "https://coppnic.cc"
destination: "../html/"
twitter_username: coppnic
github_username:  marvinpoo
markdown: kramdown

# Build settings
...
```

## Step 2: Install prerequisites
**NOTE:** Make sure you are logged in as the user you've just set-up. Do not use the root user for safety reasons!

First we need to install the prerequisites needed for Jekyll. 
```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt-get install ruby-full build-essential
```

And because we are using our own user and do not have rights for the root-user's dir/folder, we will need to make our current user's `GEM_HOME` like this:
```bash
mkdir ~/.ruby
```
and update our shell to use this directory for our GEM installations:
```bash
echo 'export GEM_HOME=~/.ruby/' >> ~/.bashrc
echo 'export PATH="$PATH:~/.ruby/bin"' >> ~/.bashrc
source ~/.bashrc
```

And then we are going to install the prerequisites for Nginx:
```bash
sudo apt update -y
sudo apt upgrade -y
sudo apt install curl gnupg2 ca-certificates lsb-release
```
This should give you the final message of `Processing triggers for man-db (X.X.X-X) ...` or similar. Then you can finally install Nginx.
```bash
sudo apt install nginx -y
```
which should finish with something like `Processing triggers for libc-bin (X.XX-XX)`. To check that your installation has worked, you can test by `sudo nginx -v`, which would give you the version installed on your Debian 11. With `sudo nginx -t` you can check for any errors, but it should work totally fine.

Now we need Nginx to start on boot so you can totaly ignore it once we've set it up.
```bash
sudo systemctl enable nginx
```
and open the ports 80 (http) and 443 (https). Luckyly Nginx installation prepared that for us, so all we have to do is run the following command in order to prepare the ports to receive successfull requests for unsecured (http) and SSL secured connections (https).
```bash
sudo ufw allow 'Nginx Full'
```
Use `sudo ufw status` to check if everything worked out fine. Nginx Full should be listed on there. If you've done everything as told so far, you could now open your browser and enter `http://your-server-ip` and get a blank page with Nginx welcoming you.

## Step 3: Setting up your domain
(Skip this, if you just want to use your IP for now ... or forever.)
For this example I will use my domain, please make sure you will edit it to yours, otherwise your website might not work. At the very first you will need to alter the DNS of your domain to point onto your server. Put the IP in the A-record, set the NS to your host's Nameserver (in the Vultr example, it will be `ns1.vultr.com` and `ns2.vultr.com`) and set the CNAME * to your domain (without protocolls such as http, https or dat).

We need to tell Nginx now, how it should handle the domain. We do that by adding a configuration file, a so called virtual host configuration. In your FTP tool, go to `/etc/nginx/sites-available` and add a file. Before we can add a file, we need to set the following folders in `/etc/nginx/` to 664 (only works if you have password prompt activated inside your FTP client, otherwise, use SSH to make it fool proof). You can easily do that in your FTP client **or** use SSH, navigate with `cd` to the folder and then enter
```bash
sudo chmod -R 664 foldername
```

Folders to 664:
- conf.d/
- sites-available/
- sites-enabled/

This is how it would look over the ssh terminal if you are inside `/etc/nginx/`
```bash
sudo chmod -R 664 conf.d/
sudo chmod -R 664 sites-available/
sudo chmod -R 664 sites-enabled/
```

Once you've set the rights, we will add our configuration file. We will call it `coppniccc.conf` in this tutorial, but you should call it something like `www.example.com.conf` for overview reasons, if you want to handle multiple domains or want to experiment with multiple configurations later on.

To prepare the domain for Jekyll, which uses html files, and to add some security and logging, we will add this text into the `.conf` file. I am showing you how to do it with the SSH terminal and VIM. If you want to use FTP and your editor of choice, you know how to create and edit a file.

```bash
sudo nano copniccc.conf
```

Now, your nano VIM has opened. Add and edit the following to the file:
```
server {
	server_name coppnic.cc www.coppnic.cc;
	root /var/www/coppniccc/html;

	index index.php index.html;

	access_log /var/www/coppniccc/logs/access.log;
	error_log /var/www/coppniccc/logs/error.log;

	# Prevent access to hidden files
	location ~* /\.(?!well-known\/) {
		deny all;
	}

	# Prevent access to certain file extensions
	location ~\.(ini|log|conf)$ {
		deny all;
	}
}
```
**NOTE:** *As I prefer "privacy by design", I do **not** add the line that adds the access.log: `access_log /var/www/coppniccc/logs/access.log;`, I will show you in some other tutorial how to disable that function completely. Not adding this line will not stop nginx from logging, it will just stop splitting the access log into a designated file but instead add it to the main log.*

To make all this work, we will now add the respective dir/folders to the server with the following SSH commands:
```bash
sudo mkdir -p /var/www/coppniccc/html/
sudo mkdir -p /var/www/coppniccc/logs/
```

and then, again, verify the configuration with `sudo nginx -t`, which should throw out this:
```bash
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

Then we need to restart Nginx with `sudo systemctl reload nginx`. This should make us good to go, check it by going to your domain with your browser. You should now see a 403 error by Nginx. Don't panic, that's correct because we haven't added any files yet.

## Step 4: Install a SLL (via LetsEncrypt)
In this example, we will use LetsEncrypt for your SSL as it is free and secure enough. You surely can use any other provider/issuer, but you are on your own on this, if you are looking to waste your money. 

To make it as easy as possible, we will use the Certbot as a snap package for the LetsEncrypt generation and installation. This is how we install snapd and the certbot:

1. Install snapd
```bash
sudo apt update
sudo apt install snapd -y
```
2. Update snapd
```bash
sudo snap install core && sudo snap refresh core
```
3. Install Certbot
```bash
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```
4. Generate & Install your LetsEncrypt Certificate
```bash
sudo certbot --nginx
```
Simply enter your E-Mail (should be vaild!), register with the server by agreeing to the terms and then decide if you want to get free Newsletters by the EFF. Once you are done, the Certbot will ask you for which domains you want to register the certificate. If you have added the domain with and without `www.` as shown above, you would need to type `1,2` and hit enter. The Certbot will also take care of redirecting any `http://` requests to `https://`. No need to edit your Nginx domain configuration again, yay!

We are all done! Let's head over and play around with Jekyll finally!

## Step 5: Installing Jekyll

We've done it. We are finally working on whaat really matters: Your new website! Head over to `/var/www/yourwebsite/` (as in my example `/var/www/coppniccc/`). Make sure you are in the very root of the server first by using `cd ..` until you are in the root, or use `cd ../../../../..` just to make very sure!. Then we need to create your jekyll dir/folder and enter it, before we install jekyll.

```bash
cd /var/www/coppniccc/
```

Now, we are going to install Jekyll & bundler GEMs:
```bash
gem install jekyll bundler
```
And to install our first Jekyll, we will run
```bash
jekyll new dev
```
(You can name `dev` anything you want, we will use this to develop and run Jekyll)

Now, via FTP replace the `_config.yml` file or use nano VIM to edit the file as shown above.