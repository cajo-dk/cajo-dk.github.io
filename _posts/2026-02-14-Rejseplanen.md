---
layout: post
title: hass-rejseplanen — MQTT-Powered Rejseplanen Departures for Home Assistant
date: 2026-02-14
tags: [homeassistant, integration, open-source]
---

**hass-rejseplanen** is a lightweight Home Assistant add-on that fetches departure data from *Rejseplanen*, filters it, compacts it for dashboards, and publishes it to an MQTT broker for use in HA automations and UI panels.

## Why this exists

A wall-mounted Home Assistant dashboard by the front door is meant to streamline everyday routines — arming the alarm, switching lights, heading out the door. But if you still have to pull out your phone to check whether your train is on time, you’re adding friction right when time matters most.

<!--more-->

**hass-rejseplanen removes** that last step by acting as a dedicated Rejseplanen fetcher that:c

* Pulls public transport departures for a given stop ID
* Filters by transport category (e.g., regional trains)
* Outputs a compact, consistent JSON payload
* Publishes to MQTT with retain so HA can consume it easily

It’s designed for responsiveness, configurability, and simple integration with dashboards and scripts.

## How it works

Under the hood, the add-on runs a Python service that on a configurable interval:

1. Queries Rejseplanen for departures
2. Filters results using `catOut=Re`
3. Compacts the data into a minimal JSON array
4. Publishes to your MQTT broker with a consistent topic structure

Example run command:

```bash
python3 /app/app.py 8600626 --cat-out Re --compact-data --mqtt-on

## Grab a copy

If you want to try it out, go grab the code here: `https://github.com/cajo-dk/hass-rejseplanen` 
