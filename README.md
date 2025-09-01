# JB_CCTV

A lightweight, configurable CCTV system for QBCore servers.  
Open, rotate, and manage security cameras across the map with simple exports that can be used by any script.

---

## 📦 Features
- Configurable list of cameras with positions, rotation, and labels (`config.lua`)
- Rotatable cameras (per-camera toggle: `canRotate = true`)
- Arrow key rotation (↑ ↓ ← →)
- Player frozen while in CCTV, no “foot shuffle”
- NUI overlay with camera label, ID, status, and time
- Exports for opening, closing, and managing cameras
- QBCore locale support (uses `Lang:t()`)

---

## ⚙️ Installation
1. Clone or download this resource into your `resources/` folder.
2. Ensure it in your `server.cfg`:
   ```cfg
   ensure jb_cctv
Configure cameras in config.lua.

Adjust NUI overlay (in html/) if you want a different look.

🎮 Usage
/cam [id] – open a specific camera (test command included)

/camoff – close the camera view

Use arrow keys (↑ ↓ ← →) to rotate cameras that support rotation (canRotate = true in config)

Press Backspace to close the camera

📖 Exports
You can call these from any other resource:

ViewCamera(cameraId)
Open a camera by its ID.
Pass 0 (or nothing) to close.

lua
Copy code
exports['jb_cctv']:ViewCamera(31) -- open Vangelico CAM#1
exports['jb_cctv']:ViewCamera(0)  -- close
CloseCamera()
Closes the current camera view.

lua
Copy code
exports['jb_cctv']:CloseCamera()
GetCameras()
Returns a copy of the cameras table for read-only usage.

lua
Copy code
local cams = exports['jb_cctv']:GetCameras()
for id, cam in pairs(cams) do
    print(id, cam.label, cam.isOnline)
end
SetCameraOnline(key, isOnline)
Toggle one camera or a list of cameras.

lua
Copy code
-- disable a single cam
exports['jb_cctv']:SetCameraOnline(31, false)

-- disable multiple cams
exports['jb_cctv']:SetCameraOnline({31, 32, 33}, false)

-- re-enable them
exports['jb_cctv']:SetCameraOnline({31, 32, 33}, true)
SetAllCamerasOnline(isOnline)
Enable or disable all cameras.

lua
Copy code
exports['jb_cctv']:SetAllCamerasOnline(false) -- disable all
exports['jb_cctv']:SetAllCamerasOnline(true)  -- enable all
🛠️ Configuration
Edit config.lua:

lua
Copy code
Config.SecurityCameras = {
    hideradar = false, -- hide radar when in CCTV

    cameras = {
        [1] = {
            label = 'Pacific Bank CAM#1',
            coords = vector3(257.45, 210.07, 109.08),
            r = { x = -25.0, y = 0.0, z = 28.05 },
            canRotate = false,
            isOnline = true,
        },
        [31] = {
            label = 'Vangelico Jewelry CAM#1',
            coords = vector3(-627.54, -239.74, 40.33),
            r = { x = -35.0, y = 0.0, z = 5.78 },
            canRotate = true, -- this one can rotate
            isOnline = true,
        },
    }
}
🎨 NUI Overlay
The overlay (html/index.html) shows:

Camera label

Camera ID

Status (online/offline)

Time (updates every second)

Close instruction (Backspace)

You can edit the HTML/CSS/JS to re-style it.

❤️ Support the Developer
If you like this resource and want to support development of more FiveM scripts:
👉 Buy my scripts or donate here
https://inferno-interactive.tebex.io/
Every purchase helps keep new releases coming 🚀

📜 License
This resource is provided as-is.
Do not redistribute or resell without permission.
