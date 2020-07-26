# Chrome OS for almost native development

I have a lot of reasons to like Chrome OS, unfortunately try using it for programming can be a pain without a little of configurations, thanks to awesome tools like Chromebrew and Crouton we can achieve that.

The first achievement was to run Jupyter Lab natively in crosh (we don't need Crouton for that), that's not the focus of this document but I've summarized it in the end of the file. Maybe I will work in some scripts and more complete explanations for more people to be able to fast configure a natively Jupyter workspace.

The main focus of this is to show how we can run Spacemacs properly in Chrome OS, because trying to running Spacemacs natively doesn't seens to work verywell because the lack of some fonts or libs, so we can't run a GUI Spacemacs, but a simple CLI Spacemacs also works fine, you just need to run `crew install emacs` and Spacemacs it.

I will show you how to configure a almost natively Spacemacs GUI.

## Printscreen

For some reason the OS can't print Crouton window right, so I add a photograph also.

![Imgur Image](https://i.imgur.com/Z7XSCas.png)

![Imgur Image](https://i.imgur.com/Cpew9cl.jpg)

## Installing Spacemacs in Chromebook feeling almost natively

As you can see in those images, spacemacs is running in Chromium OS very well, after a lot of experimentation and frustration. But in fact you can do that very easily with Crouton using xiwi so you don't have to run and entire chroot distro.

You need to download Crouton release in https://github.com/dnschneid/crouton
and then you should install xfce,xiwi and cli-extra (cli-extra is optional).
I suggest that you use a *Debian Buster* environment or more recent (>= 26.1), 
as users have reported errors using older environments that ship older and problematic versions of emacs (< 26.x).
```
  sudo crouton -r buster -t xfce,xiwi,cli-extra
```
  
Now you can start the chroot for the basic configuration, that's why I have installed cli-extra, so I dont need to load entire xfce to do shell steps now and later on if needed.
```
  sudo startcli
```
  
Now you need to run in order:
```
  sudo apt-get install git
  [ -d /usr/share/fonts/opentype ] || sudo mkdir /usr/share/fonts/opentype
  sudo git clone --depth 1 --branch release https://github.com/adobe-fonts/source-code-pro.git /usr/share/fonts/opentype/scp
  sudo fc-cache -f -v
  sudo apt-get update
  sudo apt-get install fonts-nanum fonts-nanum-coding fonts-nanum-extra
  sudo apt-get install emacs
  git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
```
  
Now you need to open emacs for the first time spacemacs configuration
```
  emacs
```

After the first run, close emacs and you now can run just a Spacemacs window like a native aplication
```
  # You can pass -mm or -fs argument
  sudo startxiwi -b emacs -mm
```

Now you may want to write an application or something to make it easier to run Spacemacs, I have my own Secure Shell fork hacked inspired by Venryx @ https://github.com/Venryx/chrome-secure-shell, so I have a lot of buttons to run commands or applications, you can create an Spacemacs button and fast open it with a single click or you may create a symlink, anyway, I'm very satisfied with Chrome OS, and now I can natively run Jupyter (without Crouton), and almost natively run Spacemacs (with Crouton), so it's everything ok for development IMO.

If you're curious about native jupyter, all you need to do is install Chromebrew https://github.com/skycocker/chromebrew, then install Anaconda https://anaconda.org/ with the normal Anaconda installer script for Linux. Conda Julia if you want, and be happy.
