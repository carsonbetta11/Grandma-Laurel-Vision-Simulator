# Through her eyes

The complete app is **index.html**. No libraries, installation, API keys, accounts, or build step.

## Put it on GitHub Pages

1. Create a public GitHub repository.
2. Upload **index.html** to its top level and commit it.
3. Open **Settings → Pages**. Choose **Deploy from a branch**, select your branch (usually **main**) and **/(root)**, then **Save**.
4. Open the HTTPS address GitHub provides in iPhone Safari. Tap **Start Camera** and allow camera access.

Only index.html needs uploading. Do not upload your personal photos. The preview image and this guide are optional and aren't app dependencies.

[GitHub's publishing instructions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

## Use it

- **Camera:** start the rear camera, hold the image for Original, release for Simulated. Flip, freeze/resume, or save a captioned PNG. Switching away from Camera stops the camera.
- **Photos:** choose or take a photo. For screenshots, enter the original screen width and her distance. For ordinary photos, enter horizontal FOV if known.
- **My measurements:** enter physical cap height and her distance, then tap the top and bottom of that same letter or digit in the photo. The source-pixel separation and angular cap height determine pixels per degree. This local scale is applied uniformly to the full photo; other depths and perspective remain approximations.
- **Calculator:** edit a preset or enter your own measurements. TV subtitles start unset. Numeric task edits and blur sigma are saved locally; photos aren't saved by the app.
- **Viewing setup:** enter the width of the visible image, excluding page margins, and your viewing distance. The default 15 cm assumes a landscape phone. Portrait and casting require different widths.
- **Chart:** optional, under Calculator. Adjust sigma if helpful; it updates every mode and persists. Hold the chart for Original. The chart is a visual check, not a certified test or validation of the patient's experience.
- **Snapshot:** tap Save Snapshot, then Download PNG. If Safari opens the PNG, use Share → Save Image. The caption is permanently part of the PNG.

## Fidelity checklist

- Only uniform Gaussian acuity blur is enabled by default.
- Contrast reduction is optional, off at each page load, and explicitly tagged as not established.
- No blind-eye image masks, field effects, vignette, glare, color shifts, noise, object removal, or simulated inattention.
- Blur decodes sRGB to linear light, runs separate horizontal and vertical Gaussian passes through WebGL2 framebuffers, then encodes back to sRGB.
- Pixels per degree are recalculated from the actual processing width and the entered geometry.
- Defaults and evidence tags accompany controls. Unknowns and limitations are in About.
- Scene blur is not amplified to compensate for a small phone display. The warning reports that limitation.
- Camera and photo content is never transmitted. A restrictive content policy blocks script network connections. No external resources are needed. Reference links navigate away only when tapped.
- Snapshot export always renders the simulation, including when the viewer is holding Original. Its caption records sigma and any enabled contrast, raster zoom, kernel truncation, or 8-bit fallback.

## Compromises and limits

1. **Acuity is not an optical prescription.** 20/70 does not uniquely identify a Gaussian blur or predict fluent reading. The 2× reading reserve is an approximation; actual critical print size can be larger. The requested category labels are retained with that qualification.
2. **Chart glyphs are hand-drawn Sloan-style vectors**, using the requested ten letters and a nominal 5:1 letter/stroke ratio. They aren't certified Sloan outlines. The chart's source is 100 px/degree; its physical angular scale at the viewer's eye also depends on screen size and distance. Its suggested legibility pattern is a check, not a guaranteed calibration outcome.
3. **Screenshot zoom is raster magnification**, centered on the screenshot. It cannot recreate browser reflow, new line breaks, or newly rendered text. Content is enlarged before filtering, so the blur scale remains fixed.
4. **Field anatomy is schematic.** The 200°/160° diagram describes typical fields, not her measured field. The caption makes the normal-left-field assumption explicit. FOVs above 120° receive different wording because a centered camera wedge can cross a typical left eye's nasal boundary. No field mask is rendered.
5. **Performance has explicit limits.** The Gaussian radius is capped at 48 pixels, and unusually large images are reduced to the GPU's texture limit. Slow live sessions can reduce processing resolution toward 1920 pixels wide; pixels per degree and sigma are recalculated. The UI reports reductions, truncation and low camera sampling. Half-float linear intermediate buffers are preferred, with a disclosed 8-bit linear fallback if unavailable. Thirty fps is a target.
6. **Compatibility needs device verification.** The implementation targets Safari 15.4+ and Android Chrome with WebGL2. Actual iPhone camera permission handling, camera flipping, orientation changes, long-run memory use, frame rate and iOS save/share behavior still need verification on the intended phone. They have not been claimed as tested.

## Verification performed

- JavaScript syntax checked.
- Rendered in the desktop app's browser; WebGL2 chart, photo processing, two-point photo scaling, calculator presets, screenshot zoom and captioned PNG export exercised.
- Phone-sized portrait layout inspected at 390 × 844; landscape layout checked separately.
- A synthetic 1200 × 800 edge-and-color image was blurred at 100 px/degree and sigma 2.0 arcmin. The exported edge matched an independent linear-light Gaussian calculation within one 8-bit sRGB level. Interior color patches retained their exact original RGB values. The exported image was visually checked for its caption and correct orientation.
- No personal photo was used for verification, and no publishing was performed.

Research context is linked in the app's About panel, including [Legge & Bigelow on reading and print size](https://pmc.ncbi.nlm.nih.gov/articles/PMC3428264/) and [Clinical Methods on typical fields](https://www.ncbi.nlm.nih.gov/books/NBK220/).
