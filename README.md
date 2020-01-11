# Tallkb
Fork of Kiibohd/Controller that contains files for my custom keyboard "tallkb".

## Build Gallery:

| | | |
|:-------------------------:|:-------------------------:|:-------------------------:|
|<img width="1604" alt="" src="https://i.imgur.com/4RtHTI5.png">  pcb right after etching with a vinyl mask |  <img width="1604" alt="" src="https://i.imgur.com/O1lWTXO.png"> Cherry switch mounting holes drilled |<img width="1604" alt="" src="https://i.imgur.com/PuxBALf.png"> Diodes and bridge wires where I couldn't fit traces|
|<img width="1604" alt="" src="https://i.imgur.com/SPDhvUy.png"> Rows and columns wired to the teensy |  <img width="1604" alt="" src="https://i.imgur.com/RTlySr8.png"> Closeup of the teensy 3.2 |<img width="1604" alt="" src="https://i.imgur.com/SOzGef6.png">The three "lock" switches |
|<img width="1604" alt="" src="https://i.imgur.com/DK0tLSW.png"> Ebonized wood frame |  <img width="1604" alt="" src="https://i.imgur.com/jDHobNk.png"> Clear acrylic case|<img width="1604" alt="" src="https://i.imgur.com/3d9yEK9.png"> Countersunk bolts with countersunk nuts on other side|
|<img width="1604" alt="" src="https://i.imgur.com/sRBaTEh.png"> Reset pinhole for the teensy |  <img width="1604" alt="" src="https://i.imgur.com/P2uW32q.png">Angled shot of the traces|<img width="1604" alt="" src="https://i.imgur.com/BXmV55x.png">Caps lock key replaced with escape for use with vim|
|<img width="1604" alt="" src="https://i.imgur.com/0RdanjU.png"> Vinyl and relegendable keycaps |  <img width="1604" alt="" src="https://i.imgur.com/ae5uBUU.png">Aluminum feet|<img width="1604" alt="" src="https://i.imgur.com/P6pelYB.png"> No nav-cluster or numpad (fn key sets HJKL to arrow keys)|
|<img width="1604" alt="" src="https://i.imgur.com/Pppm5fY.png"> Overview |  <img width="1604" alt="" src="">|<img width="1604" alt="" src="">|

<br>
<br>
<br>

# Upstream README:

The Kiibohd Controller
======================

This is the main Kiibohd Firmware.
In general, this should be the **only** git repo you need to clone.
The [KLL](https://github.com/kiibohd/kll) compiler is automatically retrieved during the build process and will warn you if your KLL compiler is too old.

Please refer to the [KLL](https://github.com/kiibohd/kll) repo or [kiibohd.com](http://kiibohd.com) for details on the KLL (Keyboard Layout Language) Spec.

[![Travis Status](https://travis-ci.org/kiibohd/controller.svg?branch=master)](https://travis-ci.org/kiibohd/controller) [![Appveyor Status](https://ci.appveyor.com/api/projects/status/67yk8tiyt88xmd15?svg=true)](https://ci.appveyor.com/project/kiibohd/controller/branch/master)

[![Visit our IRC channel](https://kiwiirc.com/buttons/irc.freenode.net/input.club.png)](https://kiwiirc.com/client/irc.freenode.net/#input.club)

[Visit our Discord Channel](https://discord.gg/GACJa4f)

# --> [Wiki](https://kiibohd.github.io/wiki/#/Quickstart) <-- If you have questions start here



Official Keyboards
------------------

* Gemini [Dusk](https://kono.store/products/gemini-dusk) and [Dawn](https://kono.store/products/gemini-dawn)
* [Infinity 60%](https://input.club/devices/infinity-keyboard/)
* [Infinity 60% LED](https://input.club/devices/infinity-keyboard/)
* [Infinity Ergodox](https://input.club/devices/infinity-ergodox/)
* [K-Type](https://input.club/k-type/)
* [Kira](https://kono.store/products/kira-mechanical-keyboard)
* [WhiteFox](https://input.club/whitefox/)


The Kiibohd firmware supports a lot of other keyboards, but these are more obscure/custom/lesser known.



Compilation
-----------

Compilation is possible and tested on Windows/Linux/macOS.
However, the recommended method is using a [Dockerfile](Dockerfiles).

Then, once you have a docker environment, you can select a build script [here](Keyboards).

To compile natively for your platform, refer to the [wiki](../../wiki).



Supported Microcontrollers
--------------------------

* [atsam4s](https://www.microchip.com/design-centers/32-bit/sam-32-bit-mcus/sam-4s-mcus)
* [Teensy 2.0](https://www.pjrc.com/store/teensy.html) (Deprecated)
* [Teensy 2.0++](https://www.pjrc.com/store/teensypp.html) (Deprecated)
* [Teensy 3.0](https://www.pjrc.com/store/teensy3.html)
* Teensy [3.1](https://www.pjrc.com/store/teensy31.html)/[3.2](https://www.pjrc.com/store/teensy32.html)
* [mk20dx128vlf5](https://www.nxp.com/part/MK20DX128VLF5)
* [mk20dx256vlh7](https://www.nxp.com/part/MK20DX256VLH7)


Adding support for more microcontrollers is possible.
Some considerations for minimum specs:

* ~16 kB of SRAM
* ~64 kB of Flash

It's possible to port chips with lower specs, but will be more effort and have fewer features.



Modules
-------

```
           +------------------------------------------------+
           |     Lib                              Debug     |
           +------------------------------------------------+

           +-------------+  +-------------+  +--------------+
Input +---->    Scan     +--+    Macro    +--+    Output    +----> Output
Data       | +---------+ |  | +--------+  |  |              |      Data
           | | Devices +------+ Pixels |  |  |              |
           | +----+----+ |  | +--------+  |  |              |
           +------|------+  +-------------+  +--------------+
                  |
                  v

               Hardware
               Control

```

* [Debug Modules](Debug) - Debug support modules (e.g. cli)
* [Scan Modules](Scan) - Defines keyboard behaviour (e.g. K-Type)
* [Macro Modules](Macro) - KLL support modules
* [Output Modules](Output) - Defines what the keyboard talks over (e.g. USB)

General Code can be found in [Lib](Lib).



Bootloader
----------

A custom bootloader (based off of [McHCK](https://github.com/mchck/mchck)) is available.
This is only necessary when assembling a keyboard with a blank MCU or if you're attempting to re-flash your bootloader (requires external tools).

[Bootloader](Bootloader)



Contributions
-------------

Contributions welcome!

* Bug reports
* Documentation and Wiki editing
* Patches (including new features)



Licensing
---------

Licensing is done on a per-file basis.
Some of the source code is from [PJRC/Teensy](http://pjrc.com), other source code is from the [McHck Project](https://mchck.org).
Code written specifically for the Kiibohd Controller use the following licenses:

* MIT
* GPLv3
* Public Domain
