# ayuclips

A single-page video-clipping interface for selecting a source video and preparing shorter segments. The page is in `index.html`, and its interface lists MP4, MOV, and WEBM as supported input types. The root also contains `vercel.json`; its role is not established here. The README does not establish the available processing or export behaviour, so verify the implementation before relying on a completed clip or output format.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>. After editing the page, reload it and check source selection with a short sample in a format the browser can decode. If the sample does not load, check whether the browser supports that file.

Test with a short sample first. Verify the implementation and browser behaviour before relying on privacy or performance claims for large videos.