# ayuclips

A single-page video-clipping interface for selecting a source video and preparing shorter segments. The page is in `index.html`, and its interface lists MP4, MOV, and WEBM as supported input types. The root also contains `vercel.json`; inspect it before changing deployment-related settings. Verify the implementation before relying on completed clip or export behavior.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## Troubleshooting

These are diagnostic steps, not reports of known issues:

1. Confirm that `index.html` is the page you intend to open. If the page does not appear as expected, inspect its references to local files and preserve their relative paths when moving files.
2. Open the browser developer tools and check the Console for script errors and the Network panel for failed requests.
3. Check that each required local asset referenced in `index.html` exists at the expected path. The root-file list does not establish separate local asset files, so verify actual references rather than assuming files are present.
4. Distinguish local files from network-dependent resources: the page loads FFmpeg and JSZip from CDN URLs and references Google Fonts. Check those network requests separately; a blocked or unavailable remote resource is different from a missing local file.
5. If a sample video fails to load, check whether the browser can decode that file before attributing the behavior to the page. Review the implementation before assuming processing or export succeeded.

## Configuration and data handling

This is a static page, and its HTML and scripts are delivered to the browser. Do not put passwords, private API keys, or other secrets in client-side code or configuration. No `.env.example` is listed among the root files. If you add a configuration template, use placeholders and keep real secrets out of tracked files.

The interface accepts a source video, but this README does not establish whether media stays in the browser, is uploaded, or how output is handled. Check the implementation before making privacy or data-retention claims. Use a sample video when reviewing the interface and avoid including private media in tracked files. Review `vercel.json` before changing it.

## Manual review checklist

Use these actions after editing the page; they are review steps, not verified results or performance measurements.

- [ ] Open `index.html` and review the source-selection and clipping interface.
- [ ] Try selecting a short sample in a listed format that the browser can decode. Observe the interface response and verify the implementation before assuming a format is processed or exported successfully.
- [ ] Inspect image, audio, video, font, stylesheet, and script references in `index.html`; check every local path against an existing file.
- [ ] Confirm that the FFmpeg and JSZip CDN scripts and Google Fonts requests are still intentional before changing or removing them.
- [ ] Check which media and other assets are actually referenced before keeping or adding files. Remove assets only after confirming they are unused; consider whether large media is necessary.
- [ ] Review the interface at narrow and wide viewport sizes. Check that source selection, controls, and text remain visible and usable.

## Accessibility review checklist

Perform these checks on the clipping interface after changes; they are review steps, not verified results:

- Use only the keyboard to move through source selection and clipping controls present in `index.html`. Check that controls can be reached and operated, with visible focus.
- Check that file-selection, playback, and clipping controls have meaningful labels and instructions. Confirm status or error messages are understandable without relying only on visual changes.
- Check text and control contrast, including labels over any video or preview area.
- If images are used, check that informative images have suitable alternatives and decorative images do not add redundant announcements.
- If transitions or other motion are used, check that they respect the user's reduced-motion preference.

## Personalizing the interface

Edit visible labels and presentation in `index.html`. Preserve the FFmpeg and JSZip CDN URLs and Google Fonts references unless intentionally changing those dependencies. Inspect actual HTML references before adding or replacing assets, keep relative paths aligned with their files, and inspect `vercel.json` before making project-specific configuration changes. Test with a short sample first; verify implementation and browser behavior before relying on privacy or performance claims for large videos.