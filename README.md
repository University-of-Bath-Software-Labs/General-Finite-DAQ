# General Finite DAQ (LabVIEW)

A general-purpose LabVIEW application for **finite (N-sample) data acquisition** from **multiple analog input channels** on an **NI DAQ** device.  
It displays acquired data on a graph, provides basic analysis (means), and allows saving/loading datasets.

This repository includes:
- the **LabVIEW source project**
- a built **Windows .EXE**
- an **Installer** for deployment
- a **Configuration** folder containing saved settings and recovery data

> <img alt="Front Panel" src="https://github.com/user-attachments/assets/277318a3-a991-4d2a-ae8e-623e3627729e" />

---

## What it does

- Acquires **finite** analog input voltage data (N samples, N channels)
- Displays all channels on a graph
- Basic analysis:
  - **Mean of each channel**
  - **Overall mean across channels**
- Save acquired data to:
  - **CSV** (`.csv`)
  - **Text** (`.txt`)
  - **TDMS** (`.tdms`)
- Load previously saved data files and display them on the graph
- Saves settings to a config file so the application is ready to run next time
- Stores the most recent acquisition in a recovery file to help prevent data loss

---

## Related project (Continuous DAQ)

This project is similar in style and intended use to:

- **LabVIEW Continuous General DAQ (16 channels)**  
  https://github.com/University-of-Bath-Software-Labs/LabVIEW-Continuous-General-DAQ-16chls

The key difference is that **this repository is for finite acquisition** (collect a defined number of samples and stop).

---

## Quick start (choose one)

### Option A — Install (recommended)
Use this if you're setting up on a PC for the first time.

1. Go to:
   - `builds/General Finite Data Acquisition/Finite DAQ Installer/Volume/`
2. Run:
   - `install.exe`
3. Launch the application after installation (shortcut/location depends on install options)

### Option B — Run the EXE (no install)
1. Go to:
   - `builds/General Finite Data Acquisition/Finite DAQ EXE/`
2. Run:
   - `General Finite Data Acquisition.exe`

### Option C — Run from LabVIEW (source)
1. Go to:
   - `General Finite Data Acquisition/`
2. Open:
   - `General Finite Data Acquisition.lvproj`
3. Open and run:
   - `Main.vi`

> Note: You’ll need a compatible NI DAQ connected, and the required NI drivers installed (e.g., NI‑DAQmx).

---

## How to use (front panel controls)

### Configure Data Acquisition
Use this to choose:
- DAQ device and channels
- number of samples
- sample rate
- min/max voltage range

These settings are saved so you don’t have to re-enter them every time.

**Channel input examples**
- Single channel: `DeviceName/ai0`
- Range of channels: `DeviceName/ai0:3` (ai0 to ai3)
- Specific channels: `DeviceName/ai0, DeviceName/ai4`

### Acquire Data
Press **Acquire Data** to capture data using your saved configuration settings.  
Results are displayed on the graph.

### Save to File
1. Choose a file type from the **File Type** dropdown (`.csv`, `.txt`, or `.tdms`)
2. (Optional) tick **Open File Location** to open the folder after saving
3. Click **Save to File**

### Read Data File
Press **Read Data File** to load an existing dataset and display it on the graph.

### Utilities
- **Clear Graph** — clears displayed data
- **Reset Settings** — resets the application settings
- **Copy Graph Image** — copies the graph image to your clipboard
- **Copy Graph Data** — copies the graph data to your clipboard

---

## Configuration & recovery files

In the same folder as the LabVIEW project and `Main.vi`, there is a folder called:

- `General Finite Data Acquisition/Configuration/`

It contains:

- `Config.ini` — stores your last-used acquisition settings (device/channels, sample rate, etc.)
- `Recovery.bin` — stores the most recent acquisition data so it can be restored if the application closes unexpectedly

> Tip: If you want a “fresh start”, you can delete/replace these files (or use the **Reset Settings** button), but only do this if you don’t need the previous settings or last recovery data.

---

## Where to find things (repo layout)

- LabVIEW source:
  - `General Finite Data Acquisition/Main.vi`
  - `General Finite Data Acquisition/General Finite Data Acquisition.lvproj`
  - `General Finite Data Acquisition/Configuration/Config.ini`
  - `General Finite Data Acquisition/Configuration/Recovery.bin`

- Built application (EXE):
  - `builds/General Finite Data Acquisition/Finite DAQ EXE/General Finite Data Acquisition.exe`

- Installer:
  - `builds/General Finite Data Acquisition/Finite DAQ Installer/Volume/install.exe`

---

## Troubleshooting

**No device found / acquisition won’t start**
- Confirm the NI DAQ is connected and powered
- Check the device is visible in NI tools (e.g., NI MAX)
- Ensure the required NI drivers are installed

**Channel string errors**
- Double-check the channel format (examples above)
- Ensure the selected channels exist on the DAQ device

**File saving/loading issues**
- Confirm you have permission to write to the selected folder
- Try saving as **TDMS** for large datasets

---

## Support / contact

For support, improvements, or deployment help, contact the **Electronics & Software Labs** team.
