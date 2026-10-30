# ayuclips

A single-page video-clipping interface for selecting a source video and preparing shorter segments. The page is in `index.html`, and its interface lists MP4, MOV, and WEBM as supported input types. The root also contains `vercel.json`; its role is not established here. The README does not establish the available processing or export behaviour, so verify the implementation before relying on a completed clip or output format.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## Manual review checklist

Use these actions after editing the page; they are not verified results.

- Open the known entry page, `index.html`, and review the source-selection and clipping interface.
- Try selecting a short sample in a listed format that the browser can decode. Observe the interface response and review the implementation before assuming a format is processed or exported successfully.
- Inspect image, media, and other resource references in the HTML. Check local paths against the files they reference and note external resources that are unavailable.
- Review the interface at narrow and wide viewport sizes. Check that source selection, controls, and text remain visible and usable.
- If a sample fails to load, check whether the browser supports that file before attributing the issue to the page.

## Accessibility review checklist

Perform these checks on the clipping interface after changes; they are review steps, not a statement that the page has passed them:

- Use only the keyboard to move through source selection and any clipping controls present in `index.html`. Check that each control can be reached and operated, and that the current focus is clearly visible.
- Check that file-selection, playback, and clipping controls have meaningful labels and instructions. Confirm that status or error messages are understandable without relying only on visual changes.
- Check text and control contrast against their backgrounds, including labels over any video or preview area.
- If the page uses images, check that informative images have suitable alternatives and decorative images do not add redundant announcements.
- If transitions or other motion are used, check that they respect the user's reduced-motion preference.

## Personalizing the interface

Edit visible labels and presentation in `index.html`. The page loads FFmpeg and JSZip from CDN URLs and references Google Fonts; preserve those URLs unless you intend to change those dependencies. No separate asset files are listed at the root, so check the existing HTML references before adding or replacing assets, and keep relative paths aligned with their files. The purpose of `vercel.json` is not documented here; inspect it before making project-specific configuration changes.

Test with a short sample first. Verify the implementation and browser behaviour before relying on privacy or performance claims for large videos.