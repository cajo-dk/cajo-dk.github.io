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

When running MCV on the local machine or from the NAS, each component runs in its own Docker container. In order to simplify the application when on the Pi, all components except the Postgresql and the MQTT broker run in the same container managed by the HASS server.

¤¤¤ Prerequisites

Before getting started, you need to ensure you have the following:

- Home Assistant OS on the Pi 5.
- MyCousinVinyl HA add-on from my repo.
- Mosquitto MQTT broker as a Home Assistant add-on.
- Postgres 17

If you want to implement additional features, you must develop them in the MCV main project and pull them into the HA module using the script in the main repo.

## Why it saves energy

- One always-on device instead of two.
- The Pi 5 is efficient at idle and still has headroom for the app.
- Less heat, fewer fans, and a simpler setup to maintain.

## MQTT setup notes

MyCousinVinyl uses MQTT for events, so I pointed it at the Mosquitto add-on running inside Home Assistant. Keeping everything on the same host reduces network hops and keeps latency low.

If you want the add-on code, it is here:

`https://github.com/cajo-dk/mycousinvinyl-ha`
