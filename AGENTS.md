# flutter_soloud_docs - Documentation Guidelines & Rules

## Docs Engine
The documentation site is built with MDX and served via [docs.page](https://use.docs.page).

## Callout Rules
Do **NOT** use markdown-based GitHub alert blockquotes (such as `> [!NOTE]`, `> [!WARNING]`, `> [!TIP]`, `> [!IMPORTANT]`, `> [!CAUTION]`).
Always use the native docs.page MDX Callout components as documented at [docs.page Callouts](https://use.docs.page/components/callouts):

- `<Info>`: Context, notes, or helpful details that aid understanding.
- `<Warning>`: Cautions readers should weigh before continuing, deprecated or risky behavior.
- `<Error>`: Blockers, failures, or requirements preventing progress.
- `<Success>`: Confirmations or completed steps.

Example:
```mdx
<Info>
Useful information or note.
</Info>

<Warning>
Urgent warning or caution.
</Warning>
```

## Audio Streaming Limitations
Always remember and document:
- **MP4 and M4A containers are NOT supported for streaming** (`setBufferStream` / `setPullBufferStream`) because ISO base media file format containers require random-access/moov atom parsing.
- MP4/M4A files are supported for loading from assets, local files, URLs, or memory (`loadAsset`, `loadFile`, `loadUrl`, `loadMem`).
- For real-time streaming, supported formats include raw PCM, MP3, WAV, FLAC, AAC (ADTS streams), AC-3, E-AC-3, and Ogg containers with Opus, Vorbis, or FLAC.

## Linux Platform Dependencies
- Core audio formats (MP3, WAV, FLAC, Ogg Opus/Vorbis/FLAC) use built-in or bundled decoders and work out of the box on Linux.
- Extended OS-native formats (M4A, MP4 audio tracks, AAC, AC-3, E-AC-3) dynamically load FFmpeg shared libraries (`libavcodec` and `libavformat`) at runtime on Linux. The host system needs FFmpeg installed (e.g. `sudo apt install ffmpeg libavcodec-extra` or `sudo pacman -S ffmpeg`).

