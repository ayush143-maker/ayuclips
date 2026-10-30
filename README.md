# ayuclips

A browser-based video clipping interface for preparing shorter segments from longer videos. Visitors can select a source video; the interface lists MP4, MOV, and WEBM as supported input types. The README does not establish what processing or export behaviour is available, so verify the implementation before relying on a completed clip or output format.

## Open locally

Open `index.html` in a modern browser, or serve the project folder over HTTP:

    python -m http.server 8000

Then visit http://localhost:8000.

## Working with video

Test with a short sample first and check that the browser can decode the selected format. Verify the implementation and browser behaviour before relying on privacy or performance claims for large videos.