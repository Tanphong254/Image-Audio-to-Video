# Image + Audio to Video

Create an MP4 from one image and one audio file using GitHub Actions + FFmpeg.

## Before running

1. Upload your image to the repository's root folder and name it exactly `image.jpg` (the file can contain JPG, PNG, or another ImageMagick-supported image format).
2. Open **Actions** → **Build video from image + audio**.
3. Click **Run workflow**.
4. Fill in only these two fields:
   - **Audio URL**: a direct-download link to the audio file.
   - **Video resolution**: 360p, 480p, 720p, or 1080p.
5. Start the workflow. When it finishes, download `output-video` from the run's **Artifacts** section.

## Resolution mapping

- 360p: 640×360
- 480p: 854×480
- 720p: 1280×720
- 1080p: 1920×1080

The video uses 30 FPS automatically. Its duration follows the audio duration. The image is scaled to fit while preserving aspect ratio; any remaining space is black.

## Audio link requirements

The URL must be accessible without signing in and should return the actual audio file, not an HTML preview page. Dropbox shared links may need `dl=1`; verify that the link downloads the complete file.

The workflow checks the downloaded audio's file size, duration, and decodability. It stops with an error instead of producing a misleading short video if the host returns an incomplete file.

## Note

The image is stored in the repository when you upload it, so only upload an image you're comfortable keeping there. GitHub Actions artifacts are retained for 7 days.
