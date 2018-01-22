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

The other day, as an icebreaker, I was asked what my biggest obsession is right now. It was an easy question for me. The answer is Home Assistant. https://home-assistant.io/ is an open-source home automation platform that I run on a Raspberry Pi 3 in my home. Initially, I wanted to just monitor a few appliances in my home, maybe control a wifi switch, if for no other reason than to say I could.  This initial dive into Home Automation ended up becoming much more and is now a part of the daily life for my wife and me.
The start of this journey was a Raspberry Pi 3 kit my team bought me for Christmas in 2016. Initially, a new toy to play with, I loaded on Linux, dabbled with LCD display readouts, and made a basic robot. It was fun but then sat in a drawer for the Summer when my next 'shiny' came along.  It wasn't until later that a use case came to me. 
We live in an old home with a three season porch on the front and in the middle of the block, as a result, the street lights are dim when trying to get in the front door. I could have gotten motion activated porch lights, but we liked the fixture we had and I knew I could just buy a few Phillips Hue bulbs to control them from my phone! Amazon Prime is a dangerous thing, and a few days later I was installing new bulbs on our porch. I was ecstatic!
It worked great, but it didn't really pass the usability tests. I still had to access my phone everytime I wanted to control the lights and coming home with an arm full of groceries wasn't a great UX. Looking up options, I quickly discovered a Google Home could allow me to voice control the lights when my arms were full. Another Prime shipment and I was back in business!
This evolution had a much-improved experience. No more phone needed and it felt surprisingly natural to just ask my house to turn the lights on and off. However, I was still not satisfied. I had to shout to get the Home to hear us through a closed window on the porch.  No more extra devices, but I looked pretty silly.
This led to my current iteration. I discovered the magic that is Home Assistant. I dug out my Raspberry Pi and within an hour I had a custom Linux distro and Home Assistant installed, thanks to Hass.io. Three lines of code had my lights installed and synced:
```	
    light:
      - platform: hue
        host: !secret hue_ip_address
```
Energized by the quick wins from a few hours of work, I set myself on the next, albeit much larger task. Automating my lights based on my presence near my home. This would require a few things:
	1) Tell the Home Assistant where is Home
	2) Tell Home Assistant where I am
	3) Set up the automation for turning the lights on and off.
I'll cover how I set this up in part two!
