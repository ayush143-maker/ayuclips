# ayuclips

A single-page video-clipping interface. The page is in `index.html`, where MP4, MOV, and WEBM are listed as supported input types. Verify the implementation before relying on clip processing or export behavior; listed formats do not by themselves confirm those features work.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## Resources and data handling

`index.html` loads FFmpeg and JSZip from CDN URLs and references Google Fonts. These requests require network access; check them separately from local file references. Inspect the HTML to identify any local assets actually used.

The page’s HTML and client-side values are delivered to the browser, so do not put secrets in client-side code. The supplied information does not establish whether selected media stays in the browser or how output is handled. Check the implementation before making privacy, processing, or data-retention claims. Use sample media for review and avoid adding private media to tracked files.

## Files and configuration

- `index.html` — page entry point and clipping interface.
- `vercel.json` — configuration file; inspect its contents before changing deployment-related settings. Its presence does not establish that a particular publishing configuration is correct or that the page has been published.

When editing the page, preserve local relative paths or update them deliberately if files move. For troubleshooting, check the browser Console and Network panel for script errors and failed requests. If a sample video fails to load, check whether the browser can decode it before attributing the issue to the page.