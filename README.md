# Ultimate Linux Experience on Dell Venue 8 Pro 5855

#### Why is this page a thing?
Dell Venue 8 Pro 5855 is a great tablet, however, it does not play very nice on a stock install of whatever distro you're throwing at it.

Performance and audio issues are a thing for starters. This guide will hopefully help you to get rid of them and give you a pleasant user experience.

This page aims to serve as a complete guide to get Linux fully working on the 5855 without getting a headache from mindless googling.  

#### Who is this guide for? 
If you're tired of Windows 10 and wants to give your tablet a greater experience, it's also pretty fly to have a fully fledged Linux operating system on a tablet.  

This is also just a reminder for me how I did it in case I get alzheimer's. 


# Preparation ⏳

### What you need. 📝
* Time, roughly an hour, depending how tech savvy you are.
* A USB stick with Ubuntu 19.04 or later, or whatever Linux distro that has Kernel 5.0>=.
* Dell Venue 8 Pro **5855**, this guide does not cover any other models of the Dell Venue 8 Pro. 

# Installation 🖥

In this guide I'll use Ubuntu 19.04, if you want to have a similar experience as me I would recommend using it too. 

I recommend selecting minimal installation when greeted with the option. 

You don't need to do anything special when installing the distro, just go on as you would with any other machine.

# Fixes 🛠

If you've followed the guide you're probably greeted with a stock Ubuntu experience. You will experience some major performance issues. Smooth as syrup. 

No such thing as audio either, your only output will be Dummy Output. That's no fun.

Let's fix this!


### Audio issues 🔈

Go to plbossarts' repository [UCM](https://github.com/plbossart/UCM), press on `Clone or download` and then `Download ZIP`.

Extract the folder `cht-bsw-rt5672` and place it somewhere. I'll place it in the Downloads folder. 

Crank up the terminal and type the following commands.

`$ cd Downloads/`

`$ sudo cp -rf cht-bsw-rt5672 /usr/share/alsa/ucm/`

`$ sudo rm -rf /home/user/.config/pulse/`

Reboot. 

You should now have a functional audio device called MonoDevice instead of Dummy Output. 


### Performance issues 🚤

#### Desktop Environment 
Ubuntus flavor of GNOME hogs way too much resources, I therefore recommend installing the vanilla version of it.

`$ sudo apt-get install vanilla-gnome-desktop vanilla-gnome-default-settings`

When it's finished installing, log out and select your user, click on the cogwheel next to the Sign In-button and select GNOME.

You're now greeted with classic GNOME. It's an eyesore but we'll make it look okay. 

First thing's first, let's remove Ubuntus GNOME environment. 

`$ sudo apt-get autoremove ubuntu-session snapd`

#### Appearance and performance tuning inside GNOME

##### Animations

Animations aren't necessary, they hog a lot of resources and can be disabled.
Open up GNOME Tweaks, select `General` and disable Animations.

##### GNOME Search

I can not stress this enough, this is easily the biggest resource hog. 

Go to `Settings → Search` and disable everything here. 

##### Fonts

Everything is much better, except that everything is tiny.  GNOME Tweaks should be installed by default. If not, install it by typing this into the terminal.

`$ sudo add-apt-repository universe`

`$ sudo apt install gnome-tweak-tool`

Crank up GNOME Tweaks, click on Fonts, and type in `1,30` into Scaling Factor. Everything should look okay now. 
If you're experiencing scaling issues, a quick logout and in should solve the problems. 


##### Scaling
It's a lot better than Ubuntu GNOME already, but the scaling might look too big, or too small.  
Fractional scaling is not enabled by default, crank up the terminal and type in the following:

`$ gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"`

The display might flicker for a second and rotate the screen into portrait mode. Fear not!

Go to `Settings → Devices → Displays`. You should now be able to see the option "Scale".

This is a personal opinion but I prefer 100%. 

I've also noticed a one-time bug that it might not scale properly the first time. Pick 125%, select Apply, and then pick 100% again. 

#### You should now have a fully functional Ubuntu Linux installation on your Dell Venue 8 Pro 5855.
