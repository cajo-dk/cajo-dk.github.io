---
layout: post
title: Running MyCousinVinyl as a Home Assistant Add-on to Save Energy
date: 2026-01-12
tags: [homeassistant, mycousinvinyl, mqtt, raspberrypi, homelab, energy]
---

I moved MyCousinVinyl into Home Assistant as an add-on to save energy and simplify my homelab. Instead of keeping a separate always-on server just for the collection app, I let the HA box do double duty.

The HA server is a Raspberry Pi 5 with 8GB RAM and a 128GB SSD. That is plenty for Home Assistant plus MyCousinVinyl, and it lets me consolidate into a single, low-power device.

<!--more-->

## What I installed

- Home Assistant OS on the Pi 5.
- MyCousinVinyl add-on from my repo.
- Mosquitto MQTT broker as a Home Assistant add-on.

## Why it saves energy

- One always-on device instead of two.
- The Pi 5 is efficient at idle and still has headroom for the app.
- Less heat, fewer fans, and a simpler setup to maintain.

## MQTT setup notes

MyCousinVinyl uses MQTT for events, so I pointed it at the Mosquitto add-on running inside Home Assistant. Keeping everything on the same host reduces network hops and keeps latency low.

If you want the add-on code, it is here:

`https://github.com/cajo-dk/mycousinvinyl-ha`
