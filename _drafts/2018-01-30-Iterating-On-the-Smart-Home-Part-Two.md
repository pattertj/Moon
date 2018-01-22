---
layout: post
title:  "Iterating on the Smart Home (Part 2)"
date:   2018-01-23
excerpt: "The other day, as an icebreaker, a facilitator asked me what my biggest obsession is right now. It was an easy question for me. The answer is Home Assistant."
tag:
- Home Assistant
- Smart Home
- Tech
comments: true
---

#1 was again an easy win with just a few lines of code:
zone:
  - name: Home
    latitude: !secret home_lat
    longitude: !secret home_long
    radius: !secret zone_radius
    icon: mdi:home
The Radius allows me to trigger my presence out to 100 meters accounting for variations in GPS accuracy and to trigger the lights as I pull up to the house instead of having to be inside.
Reporting my location was again an iterative process. Initially, I did so by trigger "Home" when I connected to the wifi. Again, an easy bit of code:
	device_tracker:
  	  - platform: ping
	    hosts:
 	     me: !secret phone_ip
However, I ended up with phantom lights as the wifi would connect and drop when my phone slept. Amusing, but not functional. :)
