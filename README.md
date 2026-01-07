# Snapmaker U1 Timelapse Recovery Tool

A command-line utility to recover corrupted timelapse videos from the Snapmaker U1 3D printer.

## What It Does

In case of power outage, resource depletion or just weird timeouts, Snapmaker U1 3D printer sometimes produces unfinished timelapse videos.
These videos still contain some of the footage but are unplayable because their files are corrupted.
This tool extracts the raw H.264 video data from broken files and remuxes them into playable MP4 videos.

## Installation

### On Snapmaker U1 Printer

It is already bundled in paxx12's Extended Firmware for Snapmaker U1.
If you would like to run the custom firmware, it is here : https://github.com/paxx12/SnapmakerU1-Extended-Firmware

If you would like to run it without custom firmware, you'll have to get terminal access to the printer and copy the script there manually. Printer already comes with Python 3 and ffmpeg installed.

### On Your Computer

#### Requirements

- **Python 3.7+**
- **FFmpeg** - Must be installed and accessible in your PATH

## Usage

```shell
./fix_timelapse.py <input_broken_video.mp4> <output_fixed_video.mp4>
```

### If running paxx12's Extended Firmware everything is already set up, just do the following:

1. Access the printer's terminal via SSH
2. Locate the correct broken timelapse video file on the printer's storage

   ```shell
   ls -lah /userdata/.tmp_timelapse/*/*.mp4
   export ORIGINAL_TIMELAPSE="/userdata/.tmp_timelapse/20260107114733/broken_timelapse_f163_r24_classic.mp4"
   ```

3. Run the script:

    ```shell

    mv ${ORIGINAL_TIMELAPSE} ${ORIGINAL_TIMELAPSE}_broken

    /usr/local/bin/fix_timelapse.py \
    ${ORIGINAL_TIMELAPSE}_broken \
    ${ORIGINAL_TIMELAPSE}
    ```

Original video should be playable again in all the usual places (Orca, Fluidd, etc.)
Broken file will remain in the original directory with `_broken` suffix for backup. Feel free to delete it after confirming the recovered video works.

## How It Works

1. Extracts H.264 NAL units from the corrupted file
2. Create- a temporary `.h264` file
3. Remuxes with FFmpeg at 24fps (standard for Snapmaker U1)
4. Cleans up temporary files automatically

## Troubleshooting

- **"Could not find 'mdat' atom"**: File may not be an MP4 or is severely corrupted
- **"FFmpeg failed to mux"**: Check that FFmpeg is installed correctly
- **No video output**: Ensure the input file contains actual video data

## License

This tool is provided as-is under the MIT License. See the [LICENSE](LICENSE) file for details.