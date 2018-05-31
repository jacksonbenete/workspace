[[https://github.com/jackson/workspace/blob/master/img/print.png]]
[[https://github.com/jackson/workspace/blob/master/img/photo.JPG]]

## Installing Spacemacs in Chromebook feeling almost natively

As you can see in this image, spacemacs is running in Chromium OS very well, after a lot of experimentation and frustration. But in fact you can do that very easily with Crouton using xiwi so you don't have to run and entire chroot distro.

You need to download Crouton release in https://github.com/dnschneid/crouton
and then you should install xfce,xiwi and cli-extra (cli-extra is optional)
```
  sudo sh ~/Downloads/crouton -t xfce,xiwi,cli-extra
```
  
Now you can start the chroot for the basic configuration, that's why I have installed cli-extra, so I dont need to load entire xfce to do shell steps now and or later.
```
  sudo startcli
  # or sudo startxfce4
```
  
Now you need to run in order:
```
  sudo apt-get install git
  [ -d /usr/share/fonts/opentype ] || sudo mkdir /usr/share/fonts/opentype
  sudo git clone --depth 1 --branch release https://github.com/adobe-fonts/source-code-pro.git /usr/share/fonts/opentype/scp
  sudo fc-cache -f -v
  sudo add-apt-repository "deb http://dev.naver.com/repos deb/"
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

If you're curious about native jupyter, all you need to do is install r/Chromebrew, then install r/Anaconda with the normal Anaconda installer script. Conda Julia if you want, and be happy.
