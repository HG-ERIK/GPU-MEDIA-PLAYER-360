# GPU-MEDIA-PLAYER-360
plays video files on the GPU instead of every other third party video player which uses the cpu which has obvious bottlenecks and limits to around 720p max 

# Roadmap

GPU Media Player 360 plays video on the Xbox 360 by using the console's own GPU video decoder instead of the CPU.
RGH/JTAG consoles only.

## Done
- [x] Found the system's GPU H.264 decoder (`dash.ExtraAVCodecs.xex`) and mapped its interface
- [x] Own driver for it, without Microsoft's XAV player layer
- [x] Decoded pictures stay on the GPU and are drawn directly (YUV to RGB shader)
- [x] 720p 60 fps 15 Mbps decodes at about 80 fps
- [x] 1080p 30 fps 20 Mbps plays with under 1% of frames skipped
- [x] 1080p 30 fps 30 Mbps plays to the end (about 3% of frames skipped)
- [x] Player app: file browser, audio and subtitle tracks, seeking, aspect ratio, brightness (from Simple 360 Player)
- [x] FFmpeg fallback for everything the GPU path cannot do
- [x] Beta releases (v0.1, v0.1.1, v0.1.2)
- [x] Fixed the random crashes: the system decoder's own thread worked on the decoder at the same time as ours
- [x] Fixed the file browser freezing after ~100 s
- [x] 4 minutes of 1080p30 30 Mbps with seeking, end of file and browsing afterwards: no crash
- [x] Fixed the random crash/lock-up (stream headers were resent before every keyframe)
- [x] Clean shutdown of the decoder (per file, and when the app exits to the dashboard)

## In progress
- [ ] Fewer skipped frames at 30 Mbps (7% now) and 720p60 (about 47 of 60 frames shown)
- [ ] Launching another title straight from playback crashes that title once

## Planned
- [ ] 1080p 60 fps (about 50 fps decoded so far, marked experimental)
- [ ] Smoother picture: the screen swap can stall while the decoder works
- [ ] **HEVC (H.265)**: the next big step once the H.264 items above are done. The console's decoder only
      knows H.264 / VC-1 / WMV, so HEVC needs our own decoder (CPU + GPU shaders); research comes first
- [ ] Moonlight game streaming client (needs low-latency decoding)
- [ ] Reuse the decoder in Multiplex 360 (Plex), a Jellyfin client and a YouTube client
- [ ] HD DVD player research: the add-on used a GPU decoder too
- [ ] Documentation of how the decoder works
- [ ] Far off: 10-bit colour / HDR sources and other special formats, AV1 research
