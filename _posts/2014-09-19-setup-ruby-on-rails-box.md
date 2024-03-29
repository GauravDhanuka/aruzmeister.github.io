---
layout: post
title: "From Zero to Hero : Setup Rails Environment"
description: ""
category: 
tags: []
---

Most people spend bit of time setting up their development work-space, there seems to be some uncertainty about setting up a lean and up-to-date local development environment. I’m no different, after a number of months tweaking and experimenting the following article details how I setup my environment for Ubuntu or Linux Mint. This tutorial will guide you through the steps of setting up an Ubuntu or Linux Mint local development machine for Ruby on Rails even if you are behind the proxy firewall (College or Company). 

In these tutorial i haven't mention and version specific installation, all those installation depends upon the current package update. So these article assumes that you have already installed the Ubuntu or Linux Mint on your machine.

### Overview

We will be setting up a Ruby on Rails development environment on Linux Mint 17 or Ubuntu 14.10. The reason we're going to be using Ubuntu based operation system like Linux Mint is because the majority of code you write will be easy, fast and runs on a Linux server. Ubuntu is one of the easiest & user friendly Linux distributions to cope with. You don't need to be enough geeky to play with it, most of thing are Graphical and as the time passes you will start using Linux Command "Which is best part!!!" .
If you haven't downloaded then please go through below link to get one of following distribution.

[Ubuntu](http://www.ubuntu.com/download/desktop)

[Linux Mint](http://www.linuxmint.com/download.php)

Before installing Rails i have mention list of following packages which are necessary for development. Please don't skip or if you have already installed, then you can move forward.

>Note:- For Proxy Firewall enabled user i would recommend to configure your proxy setting in 
>/etc/apt/apt.conf and ~/.bashrc before installing below packages.

## 1. Git

Git is a free and open-source distributed version control system, designed to handle everything from small to very large projects with speed and efficiency.” Git is the choice for version control among most Ruby on Rails developers. It will come in handy for the future.
Before setting up Git, i would request to user create account in [Github](https://github.com/)

```sudo apt-get install git```

After installation try configure Global Value for Git and SSH keys in Terminal.

```
git config --global user.name "Your Name" 
git config --global user.email "your-email@address.com"
ssh-keygen -t rsa -C "YOUR@EMAIL.com"
```

For Example:-

```
git config --global user.name "Aruz Parajuli"
git config --global user.email "arujparajuli@gmail.com"
ssh-keygen -t rsa -C "arujparajuli@gmail.com"
```

Just press Enter or Yes when system prompt. Next step is to take the newly generated SSH key and add it to your Github account. You want to copy and paste the output of the following below command and [paste it here](https://github.com/settings/ssh).

```cat ~/.ssh/id_rsa.pub```

You can also open the file and copy all text 
gedit ~/.ssh/id_rsa.pub 

>Note:- For those who have Proxy Firewall in there College or Organization follow the tricks because normally certain port are disabled. 

Since certain ports are blocked we will be using Corkscrew to tunnel through Port 443.

First of all, Install Corkscrew

```sudo apt-get install corkscrew```

If it doesn't work then [Click Here](http://wiki.kartbuilding.net/index.php/Corkscrew_-_ssh_over_https) for official documentation. After successful installation create or copy below code to ~/.ssh/config & Save it. 

{% gist d6bbe99bf50640fd2957 %} 


Also if you need authentication for your proxy server create a file ~/authfile and write your user name & password as given below.

```
username:password
```

For example:-

```
aruzparajuli:rubyrocks
```


>Note:- Remember ~ means Home Directory of your Linux Machine. 

Once you've done this, you can check and see if it worked:

```
ssh -T git@github.com
```

You should get a message like this:

Hi Aruz! You've successfully authenticated, but GitHub does not provide shell access.


## 2. Installing Ruby

Linux comes with Ruby installed, as we don’t want to be messing with core files we’re going to use the RVM to manage and install our Ruby versions for our development environment. First of all execute below command in terminal.

```sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties```

After installation copy and paste below command in serial order at Terminal.

{% gist af7d937b83a5b61cf6d3 %} 

The last step is to tell Rubygems not to install the documentation for each package locally.

```echo "gem: --no-ri --no-rdoc" > ~/.gemrc```


## 3. Installing Rails

Since Rails ships with so many dependencies these days, we're going to need to install a Javascript runtime like NodeJS which combines and minifies your javascript to provide a faster production environment. Execute given commands in your terminal.

```sudo apt-get install nodejs```

```gem install rails```

Now that you've installed Rails, you can run the rails -v command to check the rails version.

```rails -v```

## 4. Installing Sublime

As you have already setup your Ruby stack. Now it's time to get your hand dirty with code. Since Gedit or normal editor isn't sufficient to work with Sophistication of Rails. I would recommend you to [Install Sublime](http://www.sublimetext.com/) which isn't free but you can use as many times you like. For advance user i would recommend use VIM is much faster than Sublime.

If above process of installion doesn't work just execute below command 

```sudo apt-get install sublime-text```

## 5. Cloud Setup

If you wish to run your own servers in localhost than it's ok. However, if you think to make your app public, it is much easier to deploy your application with a free “platform as a service” provider such as [Heroku](https://www.heroku.com/) and [Shelly Cloud](https://shellycloud.com/). For installation you can go through documentation of designate website.
