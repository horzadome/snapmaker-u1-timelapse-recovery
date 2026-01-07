# ithu

A command-line utility to recover corrupted timelapse videos from the Snapmaker U1 3D printer.

## What It Does

The Snapmaker U1 sometimes produces corrupted MP4 timelapse files that won't play in standard video players. This tool extracts the raw H.264 video data from broken files and remuxes them into playable MP4 videos.

## Requirements

- **Python 3.7+**
- **FFmpeg** - Must be installed and accessible in your PATH

### Installing FFmpeg

- **Ubuntu/Debian**: `sudo apt install ffmpeg`
- **macOS**: `brew install ffmpeg`
- **Windows**: Download from [ffmpeg.org](https://ffmpeg.org/download.html)

## Usage

### Basic Usage

```bash
./fix_timelapse.py broken_video.mp4
```

This creates `broken_video_fixed.mp4` in the same directory.

### Specify Output File

```bash
./fix_timelapse.py broken_video.mp4 recovered.mp4
```

### Make Executable (Linux/macOS)

```bash
chmod +x fix_timelapse.py
```

## Output

The tool will:

1. Extract H.264 NAL units from the corrupted file
2. Create a temporary `.h264` file
3. Remux with FFmpeg at 24fps (standard for Snapmaker U1)
4. Clean up temporary files automatically

## Troubleshooting

- **"Could not find 'mdat' atom"**: File may not be an MP4 or is severely corrupted
- **"FFmpeg failed to mux"**: Check that FFmpeg is installed correctly
- **No video output**: Ensure the input file contains actual video data

## License

This tool is provided as-is for recovering Snapmaker U1 timelapse videos.
