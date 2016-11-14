Zcash for ARM
=============

Platform Compatibility
----------------------

This port of [Zcash](https://z.cash/) is for the arm64 (aka "aarch64")
architecture only with the ARMv8 level instruction set. It will NOT
run on a Raspberry Pi. It was ported, and the binaries built, on a Mustang
board with an X-Gene SoC from APM. It needs at least 4 gigs of RAM to
build from source, and was ported and compiled on Debian Jessie. It SHOULD
run on systems such as the Pine64 with as little as 1 gig of RAM (4 for
private, shielded transactions). It is NOT recommended for mining: with
4 cores at 2.4GHz on the Mustang, it only gets a bit over 1 solution/sec.

Binaries
--------

Links to download binaries, both .deb files for Debian Jessie and a distro
agnostic tarball, are on my website at:
https://zcash.mercerweiss.com

To download and install the .deb package for Jessie, run:
```
wget https://zcash.dl.mercerweiss.com/zcash-1.0.2-arm64.deb
sudo dpkg -i zcash-1.0.2-arm64.deb
```

To install from the binary tarball on a non-Debian system, run the following commands as root:
```
cd /
wget https://zcash.dl.mercerweiss.com/zcash-1.0.2-arm64.tar.gz
tar xzvf zcash-1.0.2-arm64.tar.gz
```

After installation, to fetch and install the zkSNARK proving keys, as the user who will
be running zcashd, run ```zcash-fetch-params```, and then follow the rest of the steps 
after building from source in the [User Guide](https://github.com/zcash/zcash/wiki/1.0-User-Guide).
After you have created zcash.conf as outlined int he User Guide, to start Zcash simply type
```zcashd```.

Building from source
--------------------

To build from source, you must first enter the following commands to symlink
some tools that GNU autoconf wants to use the wrong names for (this will not
be needed in a future release):

```
mkdir -p ~/bin
cd ~/bin
ln -s /usr/bin/ar aarch64-unknown-linux-gnu-ar 
ln -s /usr/bin/g++ aarch64-unknown-linux-gnu-g++ 
ln -s /usr/bin/gcc aarch64-unknown-linux-gnu-gcc 
ln -s /usr/bin/nm aarch64-unknown-linux-gnu-nm 
ln -s /usr/bin/ranlib aarch64-unknown-linux-gnu-ranlib 
ln -s /usr/bin/strip aarch64-unknown-linux-gnu-strip 
```


User Guide
----------

When building from source all the steps in the normal linux [User Guide](https://github.com/zcash/zcash/wiki/1.0-User-Guide) are the same, except the lines where you clone and checkout the source
code are replaced by the following 2 commands:

```
git clone https://github.com/radix42/zcash.git
git checkout v1.0.2-arm
```

This was a volunteer effort, it's open source code, I'm not an employee of ZcashCo,
so please donate to support our efforts to expand the Zcash developer ecosystem
by porting it to as many additional platforms as possible. 
Donations in BTC may be sent to: 1L33E8M1LdXmAtgWaSgAVr4TEyDrLWk69B

Additional donation methods (ZEC, Paypal, etc.) are on our website at:
https://zcash.mercerweiss.com

Thank you,

David Mercer

Tucson, AZ

radix42@gmail.com
