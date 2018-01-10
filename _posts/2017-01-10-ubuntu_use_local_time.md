---
layout: post
title: Solve the time conflict on Windows and Ubuntu dual-boot computer
---

We can solve the conflict by setting Ubuntu to use the local time:

// 1 means using local time, 0 means using UTC time <br />
$ timedatectl set-local-rtc 1

// writing the setting to the hardware clock to make it permanent <br />
$ hwclock --systohc --localtime

Tested on windows 10 and Ubuntu 16.04.
