# Grandma Laurel Vision Simulator

[Open the live page](https://carsonbetta11.github.io/Grandma-Laurel-Vision-Simulator/).

A self-contained Blender-rendered room with eight embedded panoramas, live laptop text, TV artwork and pharmacy-label artwork. No external assets, dependencies or build step.

## Use

- **Fullscreen** expands the simulation. **Done** or Escape returns. Phones use a screen-filling page view; Safari's own browser bars may remain. Wider screens also request native fullscreen when available.
- **Pinch** to magnify, then drag to pan. **Fit** returns to the full view. Desktop users can double-click or pinch a trackpad; with the scene focused, + / − zoom and 0 fits.
- At normal magnification, drag or use keyboard arrows to look around.
- Switch between **20/70 · left eye** and **Clear reference** at the same magnification and position.
- Text size and eye-to-laptop distance change the underlying scene. Reduced contrast and glare are optional and start off. **Reset** restores defaults.

Magnification applies a CSS transform outside the blur layer: the scene and its blur grow together. Pinching and panning while magnified do not rerun the room renderer, resize its canvas, alter the blur radius or move the virtual eye. Actual layout changes (fullscreen or device rotation) fit and render the scene for the new viewport; settings and looking around update it normally.

This is an illustrative approximation, not a clinical measurement of one person's vision. The page has a brief explanation under **About this view**.

## Hosting and source

GitHub Pages serves **index.html** from the root of **main**. Only the page, this guide, `.gitignore` and `.nojekyll` are tracked. All artwork stays embedded; source scenes and local QA files are not uploaded.

The original parallel-project HTML remains unchanged separately on the Mac. This checkout now contains the streamlined UI and fullscreen/magnification changes. Future parallel-project edits do not automatically synchronize here.

History: the photo-only app is recoverable at **294397d**; the unmodified room-page import is **6f481ed**.

## Verification

Syntax and gesture tests check pinch anchoring, pan handoff, bounds, Fit, and zero renderer calls during magnification. Browser checks cover desktop and phone-sized layouts, expanded view, comparison, unchanged filter/canvas/camera during zoom, and preserved embedded assets. Phone-sized browser checks are not a physical-iPhone multitouch test.
