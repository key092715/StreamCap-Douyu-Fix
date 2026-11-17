StreamCap v1.0.3 — Douyu FFmpeg input reconnect experiment

Changes:
- app/core/media/ffmpeg_builders/base.py: remove misplaced reconnect flags after -i; add correctly positioned and valued HTTP reconnect options only for Douyu FLV streams. Place HTTP headers immediately before -i.
- app/core/recording/stream_manager.py: enable this behavior only when platform_key == 'douyu'.

Scope and limitations:
- This is a SOURCE CODE patch, not a Windows EXE.
- Syntax and command construction have been checked locally. No real Douyu stream recording or Windows EXE build has been tested.
- If Douyu's refreshed stream URL requires new wsAuth credentials after 300 seconds, FFmpeg reconnecting to the original URL may not solve the issue. StreamCap's normal monitoring/restart remains as fallback.
- This patch does not merge files or implement 3-hour output. Those are separate follow-up changes after testing connection behavior.
- Keep original StreamCap and recordings backed up before trying a rebuilt application.
