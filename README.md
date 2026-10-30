# ayuclips

**ayuclips** is a browser-based video clipping tool designed to turn longer videos into shorter, shareable segments. The interface is built around selecting a source video and preparing clips for short-form formats, with MP4, MOV, and WEBM listed as supported input types.

## Open locally

The current repository is a standalone web page. Open index.html in a modern browser, or serve the project over HTTP:

    python -m http.server 8000

Then visit http://localhost:8000.

## Working with video

Test with a short sample before using a large file, and check that the browser can decode the selected format. The page advertises local processing, but verify the current implementation and browser behaviour before relying on privacy or performance guarantees for large videos. Keep the original media separate from any exported clips.
