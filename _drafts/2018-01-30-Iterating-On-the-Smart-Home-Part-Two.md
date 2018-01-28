---
layout: post
title:  "Iterating on the Smart Home (Part 2)"
date:   2018-01-23
excerpt: ""
tag:
- Home Assistant
- Smart Home
- Tech
comments: true
---

_In [Part 1](https://pattertj.github.io/Iterating-On-the-Smart-Home-Part-One/) I covered the begining of my smart home journey. In today's Part 2 I will walk through how how I iteratively built my proximity-based porch lights._ 

With my Raspberry Pi up and running with [Hass.io](https://home-assistant.io/) I had three tasks ahead of me to reach porch light nirvana, if such a place were to exist.

1. Tell the Home Assistant where is Home
2. Tell Home Assistant where I am
3. Set up the automation for turning the lights on when I get Home

#1 was again an easy win with just a few lines of code in my configuration.yaml file:

```	
    zone:
      - name: Home
        latitude: !secret home_lat
        longitude: !secret home_long
        radius: !secret zone_radius
        icon: mdi:home
```	

The Latitute and Longitude are the location of my home pulled from a quick address lookup on [Google Maps](https://www.google.com/maps). The Radius is in meters and allows me to account for variations in GPS accuracy on my phone. Additionally, it allows me to trigger the lights as I pull up to the house instead of having to be directly inside.

With that out of the way I was on to telling Home Assistant where I am. This was considerably more difficult than anything prior, however, there is great documention out there which I will link to throughout.

Initially, I triggered "Home" when I connected to the wifi. Again, an easy bit of code:

```	
	device_tracker:
  	  - platform: ping
	    hosts:
 	     me: !secret phone_ip
```	

However, I ended up with phantom lights as the wifi would connect and drop when my phone slept. Additionally the lights often didn't come on until I was in my porch for a minute or so, usually after I needed them to be on. I knew I needed something more robust and more accurate. Searching the forums led me to [OwnTracks](http://owntracks.org/).

OwnTracks is an [open-source](https://github.com/owntracks/owntracks) application that allows people to track their location on iOS or Android phones and publish it to a broker. It uses the open [MQTT](http://mqtt.org/) protocol for this communication which is very popular in the Home Assistant community and will the subject of future blog posts. To set up OwnTracks, I had a few new steps:

1. Tell the Home Assistant where is Home
2. Tell Home Assistant where I am
   1. Setup the MQTT Component in Home Assistant
   2. Setup an MQTT Broker
   3. Setup OwnTracks in Home Assistant
   4. Setup OwnTracks on my Phone
3. Set up the automation for turning the lights on when I get Home
