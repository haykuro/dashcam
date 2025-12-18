# Haykuro Enhancements

- **Multi-file event browser**
  - Organizes clips by **recorded timestamp**, grouping the typical Tesla `front/back/left/right` files for a single event under one parent row.
  - Lets you quickly switch between individual camera angles or select the grouped event entry.

- **Multi-camera grid view**
  - Selecting an event with multiple cameras shows a **2×2 synchronized grid** (front/back/left/right where available).
  - Playback controls (play/pause, scrubber, keyboard arrows) and SEI metadata remain tied to a primary camera so playback stays smooth, while secondary cameras update periodically for context.

- **Thumbnail timeline**
  - Displays a strip of **evenly spaced frame thumbnails** under the seek bar.
  - Clicking a thumbnail jumps directly to that frame, making it easier to spot and navigate to significant events.

### Screenshot
<img width="1661" height="821" alt="image" src="https://github.com/user-attachments/assets/c902e80a-04ce-401a-8bca-48c3b6c8e9c7" />

---

# Dashcam Tools

This repo contains tools for viewing Tesla Dashcam videos and extracting their associated metadata. This includes information such as vehicle speed, steering wheel angle, and self-driving state. Supported MP4 files can be found on the flash drive plugged into your Tesla (usually in the glovebox), or by downloading a clip via the Tesla mobile app's Dashcam Viewer.

This metadata also appears in the Dashcam Viewer during playback on supported vehicle displays and the Tesla App.

## Dashcam SEI Explorer (Easiest)

**[Use the online SEI Explorer →](https://teslamotors.github.io/dashcam/sei_explorer.html)**

Just drag and drop your MP4 file to view the clip and associated SEI metadata. Works entirely in your browser - your files never leave your computer.

## Files

* [`sei_explorer.html`](sei_explorer.html)
    * Web-based video player that displays SEI metadata alongside video playback. Uses [`dashcam-mp4.js`](dashcam-mp4.js) for MP4 parsing and SEI metadata extraction.
* [`sei_extractor.py`](sei_extractor.py)
    * Python-based metadata extractor. Command-line tool for extracting SEI data from MP4 files.
* [`dashcam.proto`](dashcam.proto)
    * The protobuf spec that is used to decode SEI data in the MP4 file(s).

## Troubleshooting

Not all Tesla-generated dashcam clips contain SEI data. Only clips recorded on Tesla firmware 2025.44.25 or later and HW3 or above contain SEI data. If car is parked, SEI data may not be present.

If no SEI metadata is found, ensure your dashcam footage meets these requirements.
