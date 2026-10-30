# ayuclips

Ayuclips is a browser-based video clipper in `index.html`. It reads a selected video, divides it into sequential clips, and exports MP4 files using FFmpeg WebAssembly in the browser.

## Open locally

Open `index.html` in a browser, or serve the project folder over HTTP:

```sh
python -m http.server 8000
```

Then visit <http://localhost:8000>. Loading the page locally does not by itself ensure that video processing can run; see the isolation requirement below.

## Select, configure, and export

Select one video through the file picker or drop zone. The picker accepts `video/*`; the handler also recognizes common filename extensions including MP4, MOV, M4V, WEBM, MKV, AVI, MPEG, MPG, and 3GP. Unsupported or unreadable files produce an on-page status message. A browser video preview appears, and the page reads duration, resolution, and file size from the file metadata.

“Analyse source” marks this already-read metadata as ready for settings; it does not perform a separate content-analysis pass. Choose a preset clip duration of 1, 1.5, 2, 2.5, 3, or 5 minutes, or enter a custom duration. Custom values are clamped to 6–7200 seconds. The planned number of clips is the source duration divided by clip duration, rounded up, so the last clip may be shorter.

Quality presets map to FFmpeg settings: Fast uses `ultrafast`/CRF 25, Balanced uses `veryfast`/CRF 22, and Higher uses `slow`/CRF 18. Each sequential clip is re-encoded as MP4 with H.264 video, AAC audio at 128 kbps, and `+faststart`. The Stop button requests a stop after the current clip finishes. Completed clips get individual download links; a separate control packages them into a ZIP with JSZip.

## Runtime requirements and data handling

The selected file is loaded into FFmpeg’s virtual filesystem as an array buffer. Files larger than 900 MB trigger a warning to confirm because browser memory may be insufficient; smaller files can still exceed available memory. Processing requires `SharedArrayBuffer` and `crossOriginIsolated`, normally requiring COOP/COEP response headers. The included root `vercel.json` is relevant to deployment, but a plain local Python server may not provide the required headers. Follow the processing error’s guidance to deploy with COOP/COEP headers and include that configuration.

FFmpeg and JSZip scripts load from public CDNs, and the FFmpeg core loads from unpkg. Video processing is performed in the browser; no remote processing service is identified. Avoid private media when testing unless you have reviewed browser handling and storage. Do not add media files to the repository unnecessarily.