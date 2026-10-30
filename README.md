# ayuclips

A single-page video-clipping interface. The page is in `index.html`, where the interface lists MP4, MOV, and WEBM as supported input types. The root also contains `vercel.json`; inspect it before changing deployment-related settings. Verify the implementation before relying on clip processing or export behavior.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## Page resources

`index.html` loads FFmpeg and JSZip from CDN URLs and references Google Fonts. These are network-dependent resources, so check their requests separately from local files. Inspect the HTML before assuming other local assets exist or are used.

## Configuration and data handling

This is a static page, so its HTML and client-side values are delivered to the browser. Do not put secrets in client-side code. The README does not establish whether selected media stays in the browser or how output is handled; check the implementation before making privacy or data-retention claims. Use sample media for review and avoid adding private media to tracked files.

## Troubleshooting

- If the page does not appear as expected, confirm you opened `index.html` and inspect its asset references.
- Check the browser Console for script errors and the Network panel for failed requests.
- Verify each referenced local file exists at the expected path. Check CDN and font requests separately; a failed network request is not a missing local file.
- If a sample video fails to load, check whether the browser can decode it before attributing the issue to the page. Review the implementation before assuming processing or export succeeded.

## Contributor handoff

Keep changes scoped to the relevant parts of `index.html` or, for deployment-related edits, `vercel.json`. Preserve filenames and relative references; update references deliberately if a file moves. In the handoff, describe what changed and name the affected files. Before publishing, manually review the page and check that its visible behavior and documentation match the implementation.

## Manual review checklist

These are review steps, not verified results or performance measurements:

- [ ] Open `index.html` and review the source-selection and clipping interface.
- [ ] Try a short sample in a listed format that the browser can decode; observe the interface and verify implementation before claiming successful processing or export.
- [ ] Check local asset paths and confirm the FFmpeg, JSZip, and Google Fonts requests remain intentional.
- [ ] Review the interface at narrow and wide viewport sizes, including whether controls and text remain visible and usable.
- [ ] Review changed files, relative references, and README claims before publishing.