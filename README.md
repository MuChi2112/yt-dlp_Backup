# yt-dlp_Backup


## Overview
This script is designed to automate the process of downloading multiple `.ts` (Transport Stream) files from a specified base URL, merging them into a single file, and converting the result into an MP4 format. It is particularly useful for handling video streams segmented into multiple `.ts` files, a common practice in video streaming technologies.

## Prerequisites
Before running this script, ensure you have the following installed:
- Python 3.x
- `requests` library for Python (for downloading files)
- `ffmpeg` (for merging and converting files)

You can install the `requests` library using pip if you haven't already:
```bash
pip install requests
```

Ensure `ffmpeg` is installed and accessible from your system's PATH. You can download it from [FFmpeg's official website](https://ffmpeg.org/download.html).

## How to Use

1. **URL**: Press F12, find Newtwork layer. You should see lots of file in Name List. What you need to do is to find the url of the video and also the law of it. Using a video from [niconico](https://www.nicovideo.jp/watch/sm17073592) as example:

![img](https://github.com/MuChi2112/yt-dlp_Backup/blob/main/example_pic/example_pic.png?raw=true)

URL of the .ts file been highlight is the URL of the .ts file. 

note: URL of .ts file change every time, please run the code with website and F12 open.


2. **Configuration**: Before running the script, you need to set up a few variables:
   - `save_path`: The directory where the `.ts` files will be downloaded and processed. This script will create the directory if it doesn't exist.
   - `start_file` and `end_file`: The range of file indexes to download. The script will download files starting from `start_file` to `end_file`, inclusive. Usually to download whole video, `start_file` would be 1. To get `end_file`, will have to go to the end of the video and check which .ts file is the last of it.
   - `base_url_front` and `base_url_end`: Parts of the URL that will be concatenated with the file index to form the full URL for downloading. The full URL is constructed as `base_url_front + str(i) + base_url_end` where `i` is the file index.
   
   - `video_name`: The desired name for the final MP4 video file.

3. **Running the Script**: With Python installed, run the script in a terminal or command prompt. Ensure you are in the directory containing the script or provide the full path to the script.

4. **Post-Execution**: After the script completes execution, the specified `save_path` directory will contain the final MP4 video file. All intermediary `.ts` files and the `filelist.txt` used for merging will be deleted to clean up the workspace.

## Notes
- The script includes error handling for HTTP requests, so it will notify you if any file fails to download due to network issues or incorrect URLs.
- The script uses `ffmpeg` with the `concat` protocol, which is a straightforward and efficient way to merge `.ts` files without re-encoding, preserving the original quality.
- This script assumes that all `.ts` files are named sequentially and can be sorted numerically to be merged in the correct order.

## Disclaimer
This script is provided as-is for educational purposes. Ensure you have the right to download and convert any content you use with this script. Respect copyright laws and the terms of service for any content you access.
