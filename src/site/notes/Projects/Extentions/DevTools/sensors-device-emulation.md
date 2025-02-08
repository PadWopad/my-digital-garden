---
dg-publish: true
created: 2025-01-31T18:00:19 (UTC +03:00)
tags: []
source: https://developer.chrome.com/docs/devtools/sensors?hl=en
author: Kayce Basques
---

# Sensors: Device Sensors Emulation  |  Chrome DevTools  |  Chrome for Developers

The **Sensors** panel allows you to emulate states that can be reported by the [Compute Pressure API](https://developer.mozilla.org/docs/Web/API/Compute_Pressure_API).

To emulate CPU pressure on your website:

1. [Open the **Sensors** panel](https://developer.chrome.com/docs/devtools/sensors?hl=en#open-sensors).
2. At the bottom of the panel, find the **CPU Load** section and select one of the [human-readable load states](https://developer.mozilla.org/docs/Web/API/Compute_Pressure_API#pressure_states): **No override**, **Nominal**, **Fair**, **Serious**, or **Critical**.
3. Click **Refresh DevTools** in the command bar at the top of DevTools.

![Emulating "serious" CPU pressure.](https://developer.chrome.com/static/docs/devtools/sensors/image/emulate-cpu-pressure.png?hl=en) 