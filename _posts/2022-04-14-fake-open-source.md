---
layout: post
title: "fake open source"
date:   2022-04-14 19:01:01 +0200
categories: open-source
---

![image of car](/assets/20220414191012_1.jpg)
*please don't go attack anyone, just sharing my views

I had found this pretty cool open source project called BeamMP - a multiplayer mod for Beamng Drive. I thought the idea was pretty cool. BeamNG drive is a singleplayer only game, so for modders to have ported over multiplayer functionality is impressive.

I was looking at the code, seeing if I could modify it and play around with it - and then I looked at the license.

```
Custom ISC License
Permission to use and modify (providing any work is committed upstream)
without fee is hereby granted, provided that the above copyright notice
and this permission notice appear in all copies.
```

Wtf?? Permission to use as long as the work is committed to the master branch? Maybe the authors want to protect their work, but I don't understand why one takes an aggressive stance when developing something like this.

The licences around this work seem to heavily restrict what anyone except for the repository maintainers can do with the code - regardless of who wrote it.

I also looked at the clients/servers, and they aren't released under a public license. You are able to view the source code, but you can't edit it.

This is what I'm talking about when I say "Fake Open Source" - projects are made Open source, but under an extremely restrictive license. At that point make it GPLv3 and save everyone the headache.

There also seems to be a monopoly as to who manages the servers. In order to start a server for this open source project, you need a key you can ONLY get from the maintainers. There is no way you can host an alternate server without the maintainers approval.

In my opinion open source software should be "do whatever you want" with the hope of making the world a better place - not something for control.
