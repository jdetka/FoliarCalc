# FoliarCalc

FoliarCalc is a lightweight, browser-based tool for estimating the **projected area** and visible condition of foliage—including broad leaves and conifer needles—from a calibrated close-up photograph. It runs entirely in the browser: images are not uploaded or stored by the application.

The first workflow is optimized for green foliage photographed against a plain, light background. It is especially useful for quick measurements of detached leaves, small foliage samples, and spread pine-needle fascicles.

## What it measures

The calculator identifies green and brown/rust-colored foliage pixels in a photo, converts their count to real-world area using a visible scale reference, and reports the measured area in square millimetres and square centimetres.

The result is **projected leaf area**: the two-dimensional area visible to the camera.

- For a flat leaf placed flat in the image plane, projected area is generally a good estimate of one-sided leaf area.
- For pine needles, the app can also estimate total lateral surface area when the user provides needle count, mean length, and mean diameter. It uses `count × π × diameter × length`; the tiny tip/end areas are excluded.
- Leaves should be spread with as little overlap as possible. Overlapping leaves cannot be separated from one overhead image.

### Foliage condition measurement

For foliage affected by needle cast, blights, or other browning symptoms, the calculator reports:

- green foliage area;
- brown/rust-colored foliage area; and
- brown area as a percentage of detected foliage area.

The orange class is a visible-color measurement, not a disease diagnosis. Brown bark, cones, buds, and shadows can resemble symptomatic needles; crop tightly around target needles and inspect the orange overlay before accepting a result.

## Use it

1. Open `pine-needle-area-calculator.html` in a modern web browser.
2. Photograph the foliage on a uniform, light-colored background with a ruler or another object of known length in the same plane.
3. Choose the photo in the app.
4. Click the two endpoints of a known-length ruler segment, enter its length in millimetres, and select **Use selected points for scale**.
5. Select **Exclude**, paint purple over bark, cones, buds, tags, or other non-foliage material, then select **Set scale** if you need to adjust calibration points. Use **Clear all exclusions** to start over.
6. To measure a subset, select **Draw polygon ROI**, click or tap around the branch, leaf cluster, fascicle, or other foliage group of interest, and select **Finish polygon**. Only pixels within the blue outline are included. Use **Clear ROI** to return to whole-image measurement.
7. Use **Fit image** to fit the entire photo inside the image window (especially helpful for tall photos on a phone), or increase **Zoom** and scroll to inspect a small area. Adjust the green and brown controls until the green overlay covers healthy foliage and the orange overlay covers brown/rust foliage while excluding the background. Toggle **Show mask** off at any time to compare the original image directly with your classification; ROI and exclusion annotations remain visible.
8. Select **Calculate foliage condition**.
9. For a pine fascicle, optionally enter the needle count, mean needle length, and mean needle diameter, then select **Estimate needle surface area**.
10. Download the annotated PNG and/or CSV measurement record if needed. Purple exclusions, the blue ROI boundary, and polygon vertex coordinates are retained in the export.

## Field and photo protocol

For more repeatable measurements:

- Use even, diffuse light; avoid strong shadows and glare.
- Keep the camera directly above the sample and parallel to the background.
- Place the scale reference beside—not over—the foliage.
- Use the same background, camera distance, and lighting setup for all samples in a study.
- Check the red overlay before accepting a measurement. Adjust the controls or retake the photo if background pixels are included.

## Current capabilities

- Local image upload and browser-only processing
- Manual image calibration from a known-length reference
- Adjustable green-pixel segmentation
- Adjustable brown/rust foliage classification for condition measurements
- Touch-friendly exclusion brush for bark, cones, buds, and other non-foliage material
- Click-defined polygon ROI for subset measurements of irregular foliage
- Fit/zoom viewer with scroll-to-pan inspection of small foliage features
- Classification-mask switch for direct comparison with the original image
- Green area, brown area, brown percentage, and total classified projected area in mm² and cm²
- Optional cylindrical lateral-surface-area estimate for pine-needle fascicles
- Downloadable annotated PNG and measurement CSV
- Responsive layout for phones and desktop browsers

## Limitations

This is an early, rule-based prototype. Its color classification will be less reliable for senescent or blue-green foliage, variable backgrounds, uneven lighting, shadows, brown bark, cones, and overlapping needles. The brown class measures visible brown/rust color and should not be treated as a disease diagnosis without validation against field or laboratory assessments. The optional needle surface-area calculation assumes cylindrical needles of uniform mean diameter and does not identify individual needles or apply perspective correction.

## Roadmap

- Add an eraser/undo control for exclusion strokes
- Add multiple named polygon ROIs and batch export for within-branch comparisons
- Add support for non-green or senescent foliage
- Add manual exclusion tools for bark, cones, and buds, plus sample-based color training
- Measure individual leaf or needle objects where separable
- Derive needle length and diameter from calibrated image measurements
- Add a custom app icon for installed phone versions

## Running, installing, and using offline

No installation or dependencies are required: the app is a single HTML file.

For an installable, offline-capable phone version, publish the entire repository with GitHub Pages (or another HTTPS static web host). The included web-app manifest and service worker cache the calculator after its first successful online visit.

### iPhone and iPad

1. While online, open the published calculator URL in **Safari**. Do not open the raw `.html` file from Files or Library.
2. Wait for the calculator to load completely once. This lets the browser save the app for offline use.
3. Select **Share** and choose **Add to Home Screen**.
4. Open the new **Leaf Area** icon from the Home Screen.
5. Thereafter, the calculator opens without cellular or Wi-Fi service. You can choose photos already saved on the device and export PNG or CSV results locally.

### Android phones and tablets

1. While online, open the published calculator URL in **Chrome**.
2. Let the page load completely once.
3. Open Chrome's three-dot menu and choose **Install app** or **Add to Home screen**.
4. Open **Leaf Area** from the new icon.
5. The calculator will then open offline and can analyze photos stored on the device.

### Important offline notes

- A first online visit is required so the app can be cached.
- The calculator itself works offline; no uploaded image leaves the device.
- Newly published updates require one online visit before the updated version is available offline.
- Browser storage can be cleared by the operating system or user. If the app no longer opens offline, visit its URL once while online again.

## License

Choose a license before public release. The [MIT License](https://opensource.org/license/mit) is a simple permissive option for an open project.
