# eac3to-repack

> **Note**
> This is an unofficial release. Original is here https://forum.doom9.org/showthread.php?t=125966

As of v3.36, libDcaDec was updated to `0.2.0` in the official eac3to. The only changes in this compared to the official one are:

- Updated `libFLAC` to `1.4.3`
- Deleted `success.wav` and `error.wav`

Download it from [Releases](https://github.com/cannibalChipper/eac3to-repack/releases/tag/v3.36.1)

### Usage
You can use eac3to to demux BDMVs
```
> eac3to /BDMV/
1) 00004.mpls, 00006.m2ts, 0:24:38
   - Chapters, 7 chapters
   - h264/AVC, 1080p24 /1.001 (16:9)
   - DTS Master Audio, English, stereo, 48kHz
   - DTS Master Audio, Japanese, stereo, 48kHz
```
The above gives you a numbered list, which you can then use to select it and demux it with `eac3to /BDMV/ 1) -demux`

The same also applies to individual files

```
> eac3to.exe 00006.m2ts
M2TS, 1 video track, 2 audio tracks, 2 subtitle tracks, 0:24:38, 24p /1.001
1: Chapters, 7 chapters
2: h264/AVC, 1080p24 /1.001 (16:9)
3: DTS Master Audio, English, 2.0 channels, 24 bits, 48kHz
   (core: DTS, 2.0 channels, 1509kbps, 48kHz)
4: DTS Master Audio, Japanese, 2.0 channels, 24 bits, 48kHz
   (core: DTS, 2.0 channels, 1509kbps, 48kHz)
5: Subtitle (PGS), English
6: Subtitle (PGS), English
```
Now you can select, extract and convert them all at once by using the numbers corresponding to each track.

```
eac3to 00006.m2ts 3: ENG.2.0.flac 4: JPN.2.0.*
```
This will select the third and fourth tracks, transcode the third track losslessly to FLAC, but the fourth track will be extracted without any transcoding because no codec was specified (useful for lossy tracks where you don't want to transcode them).

### Adding eac3to to PATH

Since you'll be using eac3to from terminal, you would want the convenience of using it from anywhere. To do this, add it to PATH by following the steps below:

1. Open the Start Search, type in `env`, and choose `Edit the system environment variables`.
2. Click the `Environment Variables…` button.
3. Under the `System Variables` section (the lower half), find the row with `Path` in the first column, and click `edit`.
4. The `Edit environment variable` UI will appear. Here, you can click `New` and add the path of the directory containing `eac3to.exe`.
5. Dismiss all of the dialogs by choosing `OK`. Your changes are saved.
