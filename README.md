### **1. MP4Box Installation**
- Install [MP4Box](https://gpac.io/downloads/gpac-nightly-builds/), and ensure that [MP4Box](https://gpac.io/downloads/gpac-nightly-builds/) is correctly added to the environment variables.

### **2. Downloading AAC Using Python**
- To download AAC files, I recommend using WorldObservationLog's [AppleMusicDecrypt](https://github.com/WorldObservationLog/AppleMusicDecrypt).

### **3. Supported Codecs**
- `alac (audio-alac-stereo)`
- `ec3 (audio-atmos / audio-ec3)`
- `ac3 (audio-ac3)`
- `aac (audio-stereo)`
- `aac-binaural (audio-stereo-binaural)`
- `aac-downmix (audio-stereo-downmix)`

### **Apple Music ALAC / Dolby Atmos Downloader**
Original script by Sorrow. Modified by me to include some fixes and improvements.

### **How to Use**
1. Create a virtual device on Android Studio with an image that doesn't have Google APIs.
2. Install [this version](https://www.apkmirror.com/apk/apple/apple-music/apple-music-3-6-0-beta-release/apple-music-3-6-0-beta-4-android-apk-download/) of Apple Music. You will also need [SAI](https://f-droid.org/pt_BR/packages/com.aefyr.sai.fdroid/) to install it.
3. Launch Apple Music and sign in to your account (subscription required).
4. Port forward 10020 TCP: `adb forward tcp:10020 tcp:10020`.
5. [Start frida server.](https://frida.re/docs/android/)
6. Start the frida agent: `frida -U -l agent.js -f com.apple.android.music`.

7. Build the project: `go build -o appleDL .`.
- Start downloading some albums / playlists: `./appleDL URL`.
- Start downloading singles: `./appleDL --select URL` (input numbers separated by spaces).
- For dolby atmos: `./appleDL --atmos URL`.

### **Downloading Lyrics**
1. Open [Apple Music](https://music.apple.com) and log in.
2. Open the Developer tools, Click `Application -> Storage -> Cookies -> https://music.apple.com`.
3. Find the cookie named `media-user-token` and copy its value.
4. Paste the cookie value obtained in step 3 into the `config.yaml` and save it.
5. Start the script as usual.
