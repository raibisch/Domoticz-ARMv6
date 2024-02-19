# Domoticz-ARMv6

## Update vor running under Debian 12 (bookworm)
the original (--> https://github.com/PE1DDA/Domoticz-ARMv6) Domoticz binary was compiled under bullseye (Debian 11), for running under bookworm (Debian/Rasbian 12) you need to compile under bookworm, because some libs have changed (e.g. libssl)

so if you run into
```
./domoticz: error while loading shared libraries:
libssl.so.1.1: cannot open shared object file: No such file ordirectory
```
(the reason is inscribed in this post: domoticz/domoticz#5233)

...there is no need to compile yourself:
## if you see this error after start take the version in the 'bookworm_10' folder

...for the rest follow the existing readme: 

## Howto Update for ARMv6 (e.b. pi zero w)
Like (many) others I got struck by updating Domoticz to the latest release at the beginning of january 2024, because I didn't read the update information
(I seldom did......... was used to just clicking that "green" button)
I'm sure that (many) others experienced the same.
Running Domoticz for many years on my Raspberry Pi zero W, after updating -> no go, so I tried a cmd-line update and an update beta with no luck.
Only after all that I read about the ceased support for ARMv6

Since I am still satisfied with my (old) RPI zero W, I started to search for solutions and the only one applicable seemed to start building from source....!
This has to be done on an ARMv6 device, so I started following the instructions from the Domoticz WiKi and compiled domoticz (13-01-2024) for ARMv6 boards from source.
This took almost 2 full days to complete on my RPI zero, also because Boost and GCC have to be installed, this all takes a lot of time to complete.

Now, here is my solution:

On a freshly installed bullseye light via the Raspberry Pi Imager (nice tool to be downloaded from RPI's site).

install Domoticz with:

sudo bash -c "$(curl -sSfL https://install.domoticz.com)" 


This will be the version for ARMv7, but just install it
After installation is complete, do not reboot, but go to your installation directory "domoticz" with for example FileZilla
Replace the file "domoticz" with the one above on this site/page
Now on your RPI do:

cd domoticz

sudo ./domoticz

Domoticz now will run
Go to your webinterface and login (user admin, pw domoticz)
Go to settings -> settings -> backup/restore
hit database restore and point to the domoticz.db you just downloaded from this repository or your own saved copy.
Wait untill the dashboard pops up and if all went well, you
should see the dashboard with some devices from Buienradar (Dutch weather site) and a Dummy.
Ofcourse those can be deleted, but try some of your favorite apps or plugins first to see if it is fully working.
Now you are good to go
Make sure to disable Software Updates because they will be for ARMv7 systems!
