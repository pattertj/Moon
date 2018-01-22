---
layout: post
title:  "IoT @ Home with Home Assistant (Part 1)"
date:   2018-01-23
excerpt: "Home Automation (Part 1)"
tag:
- Home Assistant
- IoT
- Smart Home
comments: true
---

The other day, as an icebreaker, a facilitator asked me what my biggest obsession is right now. It was an easy question for me. The answer is [Home Assistant](https://home-assistant.io/). Home Assistant is an open-source home automation platform that I run on a Raspberry Pi 3 in my home. At first, I wanted to track a few appliances in my home and control a wifi switch, if for no other reason than to say I could.  This initial dive into Home Automation ended up becoming much more and is now a part of the daily life for my wife and me.

The start of this journey was a Raspberry Pi 3 kit my team bought me for Christmas in 2016. Having a new toy to play with, I loaded on Linux, dabbled with LCD display readouts, and made a basic robot. It was fun but then sat in a drawer for the Summer when my next 'shiny' came along.  It wasn't until later that a use case came to me. 

We live in an old home with a covered porch on the front and in the middle of the block, as a result, the street lights are dim. When trying to get in the front door it can be hard to find your keys. I could have gotten motion activated porch lights, but we liked the fixture we had. I knew there had to be another way, I could buy a few Phillips Hue bulbs to control them from my phone! Amazon Prime is a dangerous thing, and a few days later I was installing new bulbs on our porch. I was ecstatic!

It worked great, but it didn't pass basic usability tests. I still had to access my phone every time I wanted to control the lights. Coming home with an arm full of groceries and digging out my phone wasn't great UX. Looking up options, I discovered a Google Home could allow me to voice control the lights when my arms were full. Another Prime shipment and I was back in business!

This evolution had a much-improved experience. No more phone needed and it felt surprisingly natural to ask my house to turn the lights on and off. But, I was still not satisfied. I had to shout to get the Home to hear us through a closed window on the porch.  There was no need for a device in-hand, but I looked pretty silly.

This led to my current version. I discovered the magic that is Home Assistant. I dug out my Raspberry Pi and within an hour I had a custom Linux distro and Home Assistant installed, thanks to Hass.io. Three lines of code had my lights installed and synced:
```	
    light:
      - platform: hue
        host: !secret hue_ip_address
```

![Home Assistant tile for my lights](https://github.com/pattertj/pattertj.github.io/blob/master/assets/img/HASS-PorchLights.PNG)

Energized by the quick wins from a few hours of work, I set myself on the next, albeit much larger task. Automating my lights based on my presence near my home. This would require a few things:

1. Tell the Home Assistant where is Home
2. Tell Home Assistant where I am
3. Set up the automation for turning the lights on when I get Home
    
So far my journey has been an iterative one. Starting with the easiest "Buy" answer, to extending it with add-on's, and finally tackling a "Build" option to solve my problem. In Part two I'll cover how I set up my full automation and continued to build from a skateboard, to a bike, to a car!

![The Agile Bicycle](https://cdn-images-1.medium.com/max/1600/1*qINsG4WH_BDN-viMJUH6Ng.png)
_Image Credit to Henrik Kniberg and [The Agile Bicycle](https://m.dotdev.co/the-agile-bicycle-829a83b18e7)_
