# Grandma Laurel Vision Simulator

[Open the live page](https://carsonbetta11.github.io/Grandma-Laurel-Vision-Simulator/).

Self-contained HTML with a Blender-rendered room, six supplied comparison photos and a local personal-photo tool. No libraries, build step or external assets.

## Room

Reported near vision is 20/70 in the left eye; the right eye has no vision. Prescription glasses are used, but test distance, correction during testing and distance acuity are unknown. The numerical angular-blur model is retained as a general illustration; it is not a measured prediction of acuity at every distance. Contrast and glare remain optional and off by default.

Drag at normal magnification to look around. Pinch, double-click or use + / − with the room focused to magnify; drag while magnified to pan. Fit (or 0) restores the frame. Clear reference and the illustrative near-vision mode stay aligned. Text size and eye-to-laptop distance change the underlying scene; Reset restores defaults.

The original 1400 × 1000 pill-label artwork is rendered independently on overlapping curved CSS-3D strips, at its original physical size and placement. This removes the forced square texture and room-canvas resolution bottleneck for label detail. The same parent filter covers room, laptop, TV and labels once. Magnification scales that filtered scene without changing its blur radius, focal length, canvas size or virtual eye.

## Photo Comparison

Manual swipe, arrows and keyboard navigation, in order:

1. Computer — Clear
2. Computer — Blurred
3. Pills — Clear
4. Pills — Blurred
5. Thermostat — Clear
6. Thermostat — Blurred

All six supplied PNGs are embedded byte-for-byte without extra filtering or cropping. They are supplied illustrations, not clinically calibrated 20/70 examples. Pinch/double-click magnifies the existing image; drag pans while magnified. Fit resets. Paired clear/blurred images retain the same zoom and pan; at normal magnification, a horizontal swipe changes slides. There is no autoplay.

## Add your own

The large green button opens the personal-photo workspace. Choose photo opens the device picker. Original / Blurred compare the same framing; Fit resets magnification. Fullscreen expands the workspace.

The earlier WebGL2 Gaussian-blur renderer is reused: the full supported photo is blurred once on import into a cached texture. Zoom, pan, mode switches, resize and fullscreen only present the existing texture. The illustrative default assumes a 64-degree photo frame and uses the same angular Gaussian parameter as the room, rather than inferring scene geometry or test distance. There is no calibration UI. Processing is limited to 3072 pixels on the longest side and 6 megapixels for phone memory use. Very large photos are downsampled once before processing.

Personal photos remain in device memory, are not stored or uploaded, and disappear on reload. The page has no outbound application requests; CSP blocks connections. The six public comparison images are part of the app and separate from personal photo selection.

## Fullscreen and hosting

Fullscreen / Done expands each viewer. Phones use a screen-filling page view; Safari browser bars may remain. Wider screens also request native fullscreen when available. Escape exits. Room viewport changes fit and render the room again; image viewers retain the cached image/blur.

GitHub Pages serves index.html from the root of main. Only index.html, this guide, .gitignore and .nojekyll are tracked. The parallel project's original HTML remains separate and unchanged on the Mac.

History: photo-only app at 294397d; unmodified room import at 6f481ed; streamlined room/fullscreen UI at 142b031.

## Verification

Static and gesture checks cover exact source-image preservation/order, pinch anchoring, pan handoff, swipe/cancellation, bounds, Fit, removed-control absence, unchanged room assets/blur parameter and a single photo-import blur call. Browser checks cover clear/simulated label detail, all six slides, swipe-style drag, paired magnification, local photo import/replacement, unchanged cached-blur build count during zoom/pan/comparison/fullscreen, and desktop/phone portrait/landscape layouts. Physical iPhone multitouch still requires a device check.
