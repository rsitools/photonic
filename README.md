# 📸 PhotonKit

**PhotonKit** is a mildly opinionated backup tool that helps you copy and organize your photos and videos from memory cards, phones, or cameras into your main storage drive — automatically grouped by date and camera.

It is opinionated in that it assumes and imposes a directory structure and processing rules. It uses EXIF data in photos to organize content into folders like `2025/2025-05-24/camera-name/`.


---

## ✅ What PhotonKit Does

- Copies your photos/videos into target folders in the following structure:

```

YourTargetStorageDrive/
└── 2025/
  └── 2025-05-24/
    └── canon-eos-r5/
        ├── jpg/
        ├── raw/
        └── video/

```

- Works with:
  - `.jpg`, `.jpeg`, `.heic` (from iPhones)
  - RAW files: `.cr3`, `.cr2`, `.nef`, `.arw`
  - Video: `.mov`, `.mp4`, `.avi`

- Reads the **camera name** and **photo date** automatically.
- Skips hidden or duplicate files safely.

---

## 🚀 How to Run

### 1. Make sure ExifTool is installed (once)

Open Terminal and run:

```bash
brew install exiftool
````

### 2. Run Photonic

Replace the folder paths below with your actual source and target:

```bash
python backup/photo_backup.py \
  --source "/Volumes/SDCARD" \
  --target "/Volumes/PhotoDrive"
```

* `--source`: the folder or memory card where your photos are
* `--target`: your main backup drive

✅ By default, PhotonKit skips duplicates — great for safely resuming interrupted backups.


## 🗃 To Allow Duplicate Renaming

To allow multiple versions of a file (e.g., IMG_1234.jpg, IMG_1234-1.jpg), explicitly set:

```bash
python backup/photo_backup.py \
  --source "/Volumes/SDCARD" \
  --target "/Volumes/PhotoDrive" \
  --skip-dupe false
```


---

## 🔄 Resume Backups Anytime

If something crashes or you unplug a drive — just run the same command again. PhotonKit will:

✅ Skip files it already copied
✅ Continue copying only new files



---

## 🧼 Safe by Design

* Never overwrites files
* Skips system/hidden files
* Uses real photo metadata to organize folders
* Friendly with Finder, Lightroom, and other workflows

---

## 🧠 Why Use PhotonKit?

If you've ever thought:

* "Where did I put that trip folder again?"
* "Why is everything dumped in one place?"
* "I don’t want to lose or overwrite anything!"

Photonic does the organizing for you.

---

## ✨ Coming Soon

* A preview mode (dry-run)
* Logging of what was copied

---

Made with ❤️ for photo wranglers.

## 🪪 License

Photonic is released under the [MIT License](LICENSE).