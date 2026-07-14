# PPSSPP Port for Data Frog SF3000

> ⚠️ **Experimental Project**
>
> This port of **PPSSPP** for the **Data Frog SF3000** is intended **only for experimental purposes**. Development will continue gradually. Expect bugs, crashes, and very low performance.

---

# Installation Guide

## Step 1 – Install the Emulator

Back up the following files:

| File | Where is it  |
|------|-------------|
| `rkgame` | `cubegm/` |
| `UI_Res.cpd` | `cubegm/` |
| `resource.cpd` | `cubegm/` |

Download the following files from the **Releases** page:

- `libemu_ppsp.so`
- `rkgame`
- `UI_Res.cpd`
- `resource.cpd`

Copy the files to your SD card:

| File | Destination |
|------|-------------|
| `libemu_ppsp.so` | `cubegm/cores/` |
| `rkgame` | `cubegm/` |
| `UI_Res.cpd` | `cubegm/` |
| `resource.cpd` | `cubegm/` |

If Windows asks whether to replace existing files, choose **Replace**.

---

## Step 2 – Add PSP Games

Create a new folder in the root of your SD card:

```
PSP/
```

Inside it, create the following:

```
PSP/
├── filelist.csv
└── images/
```

### Game Structure

For each game, create its own folder.

Example:

```
PSP/
├── cavestory/
│   └── EBOOT.PBP
├── images/
│   └── cavestory.png
└── filelist.csv
```

### Image Requirements

- Format: PNG
- Resolution: **320×240**

Place all images inside:

```
PSP/images/
```

### Editing `filelist.csv`

Open `filelist.csv` with Notepad or Excel.

Each game must follow this format:

```csv
FolderName\EBOOT.PBP,ImageName
```

Example:

```csv
cavestory\EBOOT.PBP,cavestory
```

---

## Step 3 – Configure CubeGM

Open:

```
cubegm/cores/Config.xml
```

Scroll to the bottom of the file and add:

```xml
<core>
    <emucore name="ppsspp-libretro" file="libemu_ppsp.so" />
    <supported_extensions>ISO</supported_extensions>
    <supported_extensions>PBP</supported_extensions>
    <supported_extensions>CHD</supported_extensions>
    <supported_extensions>CSO</supported_extensions>
    <supported_extensions>ELF</supported_extensions>
    <supported_extensions>PRX</supported_extensions>
</core>
```

Save the file.

---

Next, open:

```
cubegm/cores/filelist.xml
```

Add:

```xml
<file name="PSP/" core="libemu_ppsp.so" />
```

Save the file.

---

# Supported Formats

- ✅ PBP
- ✅ CHD
- ✅ CSO
- ✅ ELF
- ✅ PRX

## Current ISO Status

⚠️ **ISO files are currently NOT working.**

Attempting to launch an ISO will result in:

- Black screen
- Emulator crash

---

# Performance

This project is still in a very early stage.

Current performance:

- **2–5 FPS**
- Frequent crashes
- Many games are not playable yet

Future updates will focus on improving compatibility and stability.

---

# Disclaimer

This project is an unofficial experimental port of PPSSPP for the Data Frog SF3000.

It is provided **as-is**, without any guarantees of stability or compatibility.

Please report bugs and share test results through GitHub Issues.

---

# Credits

- PPSSPP Team
- Libretro
- Data Frog SF3000 community
- Everyone testing the project ❤️
