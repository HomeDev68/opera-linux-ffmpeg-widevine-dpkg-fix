Opera Linux ffmpeg Widevine Dpkg Fix
---

# Fixing Opera Dpkg Error

If you've applied a fix for HTML5 video playback on Opera, it's possible you used the [fix-opera-linux-ffmpeg-widevine](https://github.com/Ld-Hagen/fix-opera-linux-ffmpeg-widevine) script. This guide will help you resolve the following Dpkg error that may occur:

### Error:
```bash
readlink: missing operand
Try 'readlink --help' for more information.
stat: missing operand
Try 'stat --help' for more information.
E: Problem executing scripts DPkg::Pre-Invoke 'stat -c %Z $(readlink -f $(which opera)) > /tmp/opera.timestamp'
E: Sub-process returned an error code
```

### Explanation:
The error occurs because the script that tries to retrieve the timestamp of the Opera executable (`opera.timestamp`) at `/tmp/opera.timestamp` is failing. You can inspect the script causing this issue, typically located at `/etc/apt/apt.conf.d/` or `/var/lib/dpkg/info/`, specifically named `99fix-opera`.

## Steps to Fix the Error:
To resolve this, follow these steps:

### 1. Clone the Repository
Navigate to the `/tmp` directory and clone this [repository](https://github.com/Ld-Hagen/fix-opera-linux-ffmpeg-widevine):
```bash
cd /tmp && git clone https://github.com/Ld-Hagen/fix-opera-linux-ffmpeg-widevine.git
```

### 2. Navigate to the Repository
Move into the root folder of the cloned repository:
```bash
cd /tmp/fix-opera-linux-ffmpeg-widevine
```

### 3. Make the Uninstall Script Executable
Make the `uninstall.sh` script executable:
```bash
chmod +x uninstall.sh
```

### 4. Run the Uninstall Script
Run the script to remove the problematic Opera fix. If the script runs successfully, proceed with further steps if needed.
```bash
sudo ./uninstall.sh
```

### 5. Update Dpkg cache
```bash
sudo dpkg --configure -a # or
sudo apt update
```

## License
This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

