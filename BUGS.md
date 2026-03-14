BUGS
====

## Video playback is not working properly after a rendering.

* Report Details
  * Date: 14 March 2026
  * OS: Windows 11
  * CPU: x86_64

### Report

Cannot play video files after a rendering.
Playing a video at the very first frame seems okay.

### Analysis

StratoHAL reused the main HWND of Direct3D 12 rendering to Media
Foundation EVR playback. However, once Direct3D swapchain is created
for the HWND, it cannot be shared with EVR.

### Patch

Added a rendering child HWND and a video child HWND.

### Commits

* d0aaa9a748381fb6736154dcc432f867275201f5
* 820d539727b8b431ed55c79c44ee57969d67b10d

---

## Video aspect ratio is wrong if DirectShow is used

* Report Details
  * Date: 14 March 2026
  * OS: Windows 11
  * CPU: x86_64

### Report

If DirectShow is used for a video playback, the aspect ratio is wrong.

### Analysis

StratoHAL lacked the code for aspect ratio adjustment.

### Patch

Added a logic to StratoHAL.

### Commits

* 18b4a766e84791154870e7592863c49367d986cf
* be8e6b359f763614c7577cfa590e23972729e96f

---

## Video playback cannot be skipped

* Report Details
  * Date: 14 March 2026
  * OS: Windows 11
  * CPU: x86_64

### Report

Video playback cannot be skipped by a click.

### Analysis

In StratoHAL, the video HWND didn't receive mouse events.

### Patch

Added event handlers for the video HWND in StratoHAL.

### Commits

* 82f0e0e86e3349269bf95a809b0a061eebc5cf40

---
