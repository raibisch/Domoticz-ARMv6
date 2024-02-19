### Update vor running under Debian 12 (bookworm)
the original (--> https://github.com/PE1DDA/Domoticz-ARMv6) Domoticz binary was compiled under bullseye (Debian 11), for running under bookworm (Debian/Rasbian 12) you need to compile under bookworm, because some libs have changed (e.g. libssl)

so if you run into
```
./domoticz: error while loading shared libraries:
libssl.so.1.1: cannot open shared object file: No such file ordirectory
```

if you see this error after start take this version in the 'bookworm_10' folder
(is actual: domoticz 2024:

...for the rest follow the existing readme...
