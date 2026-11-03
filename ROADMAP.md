# Roadmap

GPU Media Player 360 plays video on the Xbox 360 by using the console's own GPU video decoder instead of the CPU.
RGH/JTAG consoles only.

## Done
- [x] Found the system's GPU H.264 decoder (`dash.ExtraAVCodecs.xex`) and mapped its interface
- [x] Own driver for it, without Microsoft's XAV player layer
- [x] Decoded pictures stay on the GPU and are drawn directly (YUV to RGB shader)
- [x] 720p 60 fps 15 Mbps decodes at about 80 fps
- [x] 1080p 30 fps 20 Mbps decodes at a steady 30 fps in tests
- [x] Player app: file browser, audio and subtitle tracks, seeking, aspect ratio, brightness (from Simple 360 Player)
- [x] FFmpeg fallback for everything the GPU path cannot do
- [x] First beta release (v0.1)

## In progress
- [ ] Fix the console lock-up seen in the first test of the full player
- [ ] Verify audio/video sync, seeking and end of file on the GPU path
- [ ] Clean shutdown of the decoder (it is left open when the app exits)

## Planned
- [ ] 1080p 60 fps (about 50 fps decoded so far, marked experimental)
- [ ] Smoother picture: the screen swap can stall while the decoder works
- [ ] Moonlight game streaming client (needs low-latency decoding)
- [ ] H.265 / AV1 research
- [ ] Reuse the decoder in Multiplex 360 (Plex), a Jellyfin client and a YouTube client
- [ ] HD DVD player research: the add-on used a GPU decoder too
- [ ] Documentation of how the decoder works
