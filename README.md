![Home Assistant Logo](hass.png "Home Assistant Logo")

# Kareems home-assistant-config

Configuration for Kareem's [HomeAssistant](https://home-assistant.io).

Note that the "[kareem](https://github.com/KptnKMan/home-assistant-config/tree/kareem)" (Dev) branch is usually more updated.

## Introduction

This is the project of my Home Automation journey.

Be warned: This is definitely a perpetual work in progress, and is full of messy commented code.

This code is provided to help myself and others learn.
If you like anything you see, and/or have any questions, contact me and I can try to help/describe what was going through my ape brain.

## Why I did this

I wanted to automate my living space for some time, but I never had the chance or the right property.
When I decided to purchase a house, I decided that this was the perfect time.

Also, because I like automating things.

## My automation policy

A few things I try to keep my system in-line with, which helps me make decisions about what hardware to purchase etc.
I'll try to explain a few of those decisions here.

### Centralised automation first

My goal is to have a single interface for everything, and have all sub-systems managed through this single interface of truth.
I did a lot of research on the compatibility and capability of nearly all the systems out there, and I came to the conclusion that I would have to bespoke some of this relative to my needs, but also try to keep it as general as possible.

The home automation space is relatively new, and as such there is much incompatibility between this system and that system, meaning buying Hue bulbs and Ikea bulbs wont work together... And will need separate interfaces.

I experimented with a few centralised systems and eventually came down to a choice between OpenHab and Home-Assistant.
Home-Assistant won out in the end, and I haven't looked back.

### Automation that runs itself

I also wanted to have as much as the automation run itself as possible.
This meant thinking carefully about what I wanted to achieve and what my own lifestyle and workflow is, so that I could translate that into tasks and actions for my system to use.

I found that the key to this is understanding the triggers and actions throughout my life that I normally don't think about.

### Local cloud first

My system, my data.

When I set out on this journey, I knew I wanted very much to have a private system, where I would be in control.
This would of course mean that a lot of systems and processes would need to be setup, like secure remote access, among other problems.

All "core" services and hardware need to work offline, without cloud services requiring them to work.
In the automation space, this can be a real issue, as most suppliers of hardware (Eg: Hubs) and software are tied closely to outside services in the cloud, and will not function when these services become unavailable. This is unacceptable for me, for core automated systems.

This meant the pick of my core systems would need to operate under direct control and function without an internet connection.

### Keep costs low

I wanted to keep costs low and use as much commodity hardware as possible.
This would be so that once I'd found a good solution, I could scale this out easily.

### Pass the "wife test"

It's very important that when an automated system inevitably fails, that my house will still work like you would expect a normal house to work.
This is often been referred to online as the "wife test", to represent a suffering spouse, who will be understandably frustrated because the light switch does not turn on the light as expected (Probably because some gizmo has crashed). To People who are not as enthusiastic about home automation, this can be a major inconvenience to things we take for granted.

As such, all switches and hardware needs to have hardware switches (Lights need to be operable from the regular switch etc), and operate as normally as possible in the absence of the core system itself.

## Dashboard

My current Home Assistant Dashboard:
<br><img src="Dashboard.png" width="1000">

## Diagram

I produced a diagram to keep track of, and help explain my system to others.
This diagram is likely not 100% accurate, as sometimes changes are made to the system.
![Home Automation Diagram](Diagram.png)

## Components and Hardware

Here is a best-effort list (With links where to buy) of all the current hardware I use.
I try to keep this list updated, and it will likely be more recent than the diagram above.

- Google:
  - 3x Google Chromecast (Ultra 4k, 2nd Gen, 1st Gen)
  - 2x Google Chromecast Audio
  - 4x Google Home Mini

- Amazon/Ring:
  - Ring Doorbell Pro (WiFi)

- HomeWizard:
  - 2x Wi-Fi kWh meter 1-phase MID (1 for Mains, 1 for Solar Panels) (WiFi)
  - 6x Energy Socket EU (WiFi)

- Vera Plus (Z-Wave + Zigbee Hub):
  - 10x Neo Coolcam Smart Plug (EU)
  - 5x Neo Coolcam PIR Sensor
  - 2x Vision Door/Window Sensor
  - 5x Fibaro Switch
  - 2x Fibaro Dimmer
  - 2x Aeotec Multisensor 6
  - 1x POPP Door Strike
  - 1x Fibaro "The button" (Red)
  - 2x Z-Wave Key Remote

- IKEA TRADFRI (Zigbee Hub):
  - 1x LED Driver/Controller
  - 5x GU11 Spot lights
  - 1x LED RGB Bulb 800lm
  - 7x LED White Bulb 1000lm
  - 1x GL-C-007 Bulb
  - 2x FYRTUR Blinds

- Xiaomi:
  - Mii-Light LED Bridge (Mostly unused)
    - 2x Mii-Light LED RGBW Controller (Unused)
  - Xiaomi Gateway II Zigbee Hub
  - Xiaomi Gateway III Zigbee Hub (Mostly unused)
  - 3x Xiaomi "Yeelight Ceiling Light" (WiFi)
  - 2x Xiaomi "Yeelight Ceiling Light (Jiaoyue 480/650)" (WiFi)

Sonoff:
  - 4x Sonoff Basic (Running Tasmota)
  - 4x Sonoff POW2 (Running Tasmota)
  - Sonoff RF Hub (Running Tasmota)
    - 2x RF Key Remote
  - Sonoff Zigbee Hub (Running Tasmota)

- 2x Shelley RGBW2 (Running Tasmota)
- 2x LC Technology 5V 4 Channel Relay (Running Tasmota)

## Automation goals and projects

When enbarking on this, I made sure to make clear a set of taks that I wanted to perform (Or have automated for me).

- [x] notifications & alarms
  - The system to notify me of environmental changes
  - The system should notify me of intruders
    - I should be able to understand locations of the intruders
- [x] lights by motion
  - I should be able to walk through the house without activating lights myself
  - The lights should switch themselves off
- [x] heating presence detection
  - The house should be warm when I am home
  - The house should automatically adjust the heating down when nobody is home
  - Heating should adjust down when its night time
  - If a designated "friend group" is in the house, the heating should auto-adjust itself 1 or 2 degrees higher
    - And return to my own "normal" when I am alone
- [x] heating control
  - Fine-grained and simple control of heating at anytime
  - Heating will auto-adjust during the day/night, when a valid presence in the house
  - Temperatures will auto-set based on periods of day:
    - Daytime - 9am to 11pm
    - Morning - 6am to 9am
    - Night - 11pm to 6am
    - Away - anytime when nobody is home
- [x] secure keyless entry
  - I should be able to buzz my door when without using a key
- [x] security of entry
  - I should be able to see who is at the door
  - I should be able to remotely lock the door(s)
- [x] voice control
  - I want to be able to control, using my voice:
    - heating
    - lights
    - automations
- [x] Music and radio
  - I should be able to play music anywhere in the house
  - I should be able to play music throughout the entire house
  - I should be able to play music by source (Spotify/Internet Radio)
  - The volume levels will automatically adjust based on time of day/night
- [x] low battery notifications
  - I want to be able to be notified:
    - when batteries are low, at a configurable threshold
    - which devices have low batteries
    - what level are the low batteries
- [x] Power/Electricity/Solar monitoring
  - I want a summary of electricity usage
  - I want a breakdown of particular items/systems in the house
  - I want to see an approximate electricity cost calculation
  - I want to see Solar Panel yield
- [ ] plant watering
  - The plants should be watered automatically
    - based on schedule or moisture level
- [ ] vacuum robot
  - A robot shpuld vacuum the house when I'm not home
  - The robot should return when I'm home or returning home
