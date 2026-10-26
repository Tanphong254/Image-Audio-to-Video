# Image + Audio to Video

Create an MP4 from one still image and one audio file using GitHub Actions + FFmpeg.

## Run it

1. Open **Actions** → **Build video from image + audio**.
2. Choose **Run workflow**.
3. Paste direct-download URLs for the image and audio.
4. Choose resolution and FPS, then start the run.
5. Download `output-video` from the completed run's Artifacts section.

## Inputs

- `image_url`: direct URL to a single image.
- `audio_url`: direct URL to an audio file (MP3, WAV, M4A, AAC, etc.).
- `resolution`: `1920x1080`, `1280x720`, or `1080x1920`.
- `fps`: 24, 30, or 60.

The URLs must be accessible without logging in and should return the actual media bytes, not an HTML preview page. Dropbox shared links can sometimes be converted by adding `dl=1`; test that the server actually returns the full file.

## Validation

The workflow checks HTTP status, downloaded file size, image decoding, audio decoding, and audio duration. It fails instead of silently creating a tiny video if the server returns an incomplete audio file.

## Notes

- Output video duration follows the audio duration.
- Image is scaled to fit the selected frame while preserving aspect ratio; remaining space is black.
- This repo does not store your input media in Git.
- GitHub Actions run time and artifact retention are subject to your GitHub plan and repository settings.
