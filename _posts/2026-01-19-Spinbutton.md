---
layout: post
title: Spinbutton - A Tiny UI Control for creating buttons
date: 2026-01-19
tags: [ui, web, javascript, component, open-source]
---


Spinbutton is a small, focused repo that delivers a highly customizable button for Home Assistant, with a spinner border that animates around the button. I built it to be simple, reusable, and easy to drop into small projects without pulling in a big UI framework.

<!--more-->

## Design

The solution is intentionally minimal: a single, clear interaction pattern, small surface area, and clean styling you can adapt to your own HA dashboard.

The spinner is implemented as layers with a base layer containing a spinning disc with color stops designed to give the border a "travelling look", a layer with cutouts to capture spillover, and a face layer.  

<img src="/assets/images/spinbutton.png" alt="Spinbutton UI" style="width: 60%; margin: 40px auto; display: block;">

Code here:

`https://github.com/cajo-dk/spinbutton`
