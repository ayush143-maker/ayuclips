# ayuclips

A single-page video-clipping interface for selecting a source video and preparing shorter segments. The page is in `index.html`, and its interface lists MP4, MOV, and WEBM as supported input types. The root also contains `vercel.json`; inspect it to understand its role before changing deployment-related settings. The README does not establish the available processing or export behavior, so verify the implementation before relying on a completed clip or output format.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## Configuration and data handling

This is a static page, and its HTML and scripts are delivered to the browser. Any values placed in client-side code or configuration are visible to visitors; do not put passwords, private API keys, or other secrets there. No `.env.example` is listed among the root files. If you add a configuration template, use placeholders rather than real credentials, and keep any real secret out of tracked files.

The interface accepts a source video, but this README does not establish whether media stays in the browser, is uploaded, or how output is handled. Check the implementation before making privacy or data-retention claims. Use a sample video when reviewing the interface, and avoid including private media in tracked files. Review `vercel.json` before changing it, and do not add sensitive values to tracked configuration.

## Manual review checklist

Use these actions after editing the page; they are review steps, not verified results or performance measurements.

- [ ] Open `index.html` and review the source-selection and clipping interface.
- [ ] Try selecting a short sample in a listed format that the browser can decode. Observe the interface response and review the implementation before assuming a format is processed or exported successfully.
- [ ] Inspect image, audio, video, font, stylesheet, and script references in `index.html`. For each local reference, check that the path resolves to an existing file. Do not assume a resource is local just because it appears in the page.
- [ ] Review the page's external dependencies: FFmpeg and JSZip are loaded from CDN URLs, and Google Fonts are referenced. Confirm each is still required by the page before changing or removing it, and check that any newly added external dependency is intentional.
- [ ] Check which media and other assets are actually referenced before keeping or adding files. Remove an asset only after confirming it is unused; consider whether large media is necessary rather than making unmeasured performance claims.
- [ ] Review the interface at narrow and wide viewport sizes. Check that source selection, controls, and text remain visible and usable.
- [ ] If a sample fails to load, check whether the browser supports that file before attributing the issue to the page.

## Browser and platform reliability checklist

Use these checks after page changes to review browser and platform behavior. They are a checklist, not verified compatibility results.

- [ ] Identify the current browsers and platforms relevant to this page's HTML and JavaScript, then open the page in those browsers. Check the source-selection and clipping interface, and review the implementation before relying on media-processing or export behavior.
- [ ] Open the browser developer tools and inspect the Console and Network panel. Look for JavaScript errors, failed requests, and resources that do not load; distinguish a browser's inability to decode a sample from a page or request failure.
- [ ] Check local references in `index.html` against files at the expected paths. Check remote requests for the listed FFmpeg and JSZip CDN scripts and Google Fonts, and investigate failed or blocked requests rather than assuming those resources loaded.
- [ ] Compare the page at mobile and desktop viewport sizes. Check that source selection, clipping controls, and text remain visible and usable at both sizes; do not treat a resized desktop view as proof of testing on a mobile device.
- [ ] Record the browsers, devices or viewport sizes, and any issues actually reviewed before making compatibility claims. Do not describe the page as tested based on this checklist alone.

## Accessibility review checklist

Perform these checks on the clipping interface after changes; they are review steps, not a statement that the page has passed them:

- Use only the keyboard to move through source selection and any clipping controls present in `index.html`. Check that each control can be reached and operated, and that focus is clearly visible.
- Check that file-selection, playback, and clipping controls have meaningful labels and instructions. Confirm that status or error messages are understandable without relying only on visual changes.
- Check text and control contrast against their backgrounds, including labels over any video or preview area.
- If the page uses images, check that informative images have suitable alternatives and decorative images do not add redundant announcements.
- If transitions or other motion are used, check that they respect the user's reduced-motion preference.

## Personalizing the interface

Edit visible labels and presentation in `index.html`. The page loads FFmpeg and JSZip from CDN URLs and references Google Fonts; preserve these URLs unless you intend to change those dependencies. No separate asset files are listed at the root, so inspect the HTML's actual references before adding or replacing assets, and keep relative paths aligned with their files. Inspect `vercel.json` before making project-specific configuration changes.

Test with a short sample first. Verify the implementation and browser behavior before relying on privacy or performance claims for large videos.