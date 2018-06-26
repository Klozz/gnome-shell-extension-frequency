 gnome-shell-extension-frequency
==============================

View the actual frequency and change CPU frequency governor from gnome shell.

There is a bit of work to make it work though.

cpufreq
-------
You need CPU Frequency scaling set up to use it.  

**Ubuntu 17.x**: sudo apt-get install cpufrequtils

Admin rights for changing the governor
--------------------------------------

When the extension sets a governor, it does it one by one, calling cpufreq-selector for every cpu.

The problem here is that it will raise a popup asking for your password for each cpu. Typing the password for 4 CPUs can become quite annoying.

To solve this, I use (in archlinux):

Create and edit the file: /var/lib/polkit-1/localauthority/50-local.d/org.gnome.cpufreqselector.pkla

with:

> [org.gnome.cpufreqselector]  
> Identity=unix-user:**USER**  
> Action=org.gnome.cpufreqselector  
> ResultAny=no  
> ResultInactive=no  
> ResultActive=yes  

replacing **USER** with your username.

Thanks
------
https://github.com/nodefourtytwo I based this on his work I'm gonna improve it in the future.
https://github.com/Farsx  
https://github.com/LeCoyote  
https://github.com/victornoel  
https://github.com/sonic414  
