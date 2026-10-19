# Through her eyes — photo approximation

[Open the live simulator](https://carsonbetta11.github.io/Grandma-Laurel-Vision-Simulator/) in iPhone Safari.

Choose a photo, pinch to enlarge it, and drag to move around. **Original** and **Simulated** keep the same zoom and position. **Fit photo** resets the view. **Save Image** exports the entire blurred photo with a permanent caption, regardless of the current zoom or comparison view.

The blur is computed on the full supported image before zooming. Zoom and pan enlarge that cached result; they never recalculate the blur as though the camera had moved closer. Zoom is available from 100% to 1600%, with plus/minus buttons and keyboard controls as alternatives to gestures.

The live camera, calculator, chart and measurement/calibration flows have been removed. No ruler setup is required. A curated photo library is intentionally deferred.

## Settings and limits

- The known facts remain left-eye acuity 20/70 and no right-eye vision. No image area is masked for the blind eye.
- Default Gaussian sigma is 2.0 arcmin, adjustable from 1.5 to 2.4. The assumed horizontal photo angle defaults to 65°. Both are explicitly labeled engineering approximations. Without known capture geometry, this is a rough demonstration, not calibrated reproduction of her vision.
- Image processing is local, with no uploads, external resources, analytics or camera access. Only sigma is stored locally. Photos disappear on reload.
- The blur decodes sRGB to linear light, uses horizontal and vertical Gaussian passes through WebGL2 framebuffers, then re-encodes sRGB.
- Photos are limited to a maximum 4096-pixel side, or the device's smaller limit, to control memory use. Pixel scale is adjusted if resized. The UI discloses resizing, kernel truncation at 48 pixels, or an 8-bit linear intermediate fallback.
- The model doesn't represent unknown contrast, glare, field, or other visual problems. Magnification helps inspect the modeled detail loss; it doesn't validate its match to her actual perception.
- iPhone Safari touch behavior and photo-library/save-share behavior still need a hands-on check on the intended phone.

## Verification

- JavaScript syntax and HTML/privacy checks.
- Actual PNG file-selection flow, zoom buttons, panning and matched comparison exercised in the desktop app's browser at a phone-sized viewport.
- Safari rendered a synthetic image through the same photo-processing code. Its linear-light edge matched an independent Gaussian calculation within one 8-bit RGB level. Flat color and orientation checks passed.
- The cached blurred pixels were byte-for-byte identical after six-times zoom and switching Original/Simulated, with zero additional blur calculations.
- Full-photo PNG export was exercised while zoomed into Original; the exported result retained simulated blur, full framing and the permanent caption.
- Safari's automated native file picker did not complete during QA; its rendering/export tests used a synthetic fixture through the same image-loading code. No personal photos were used.

## Development and hosting

The app is a single **index.html** with inline CSS and vanilla JavaScript. No dependencies or build step. GitHub Pages serves the root of the **main** branch. Publishing changes means committing and pushing this file and the guide.

The repository uses an allowlist in `.gitignore`: only the app, guide, ignore file and `.nojekyll` marker are tracked. Personal photos and local QA files stay out of the repository.
