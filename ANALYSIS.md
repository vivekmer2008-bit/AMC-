# Comprehensive Analysis of AMC VBDC Mobile Application (`base.apk`)

## 1. Application Overview
The application provided (`base.apk`) is the **AMC VBDC** (Ahmedabad Municipal Corporation - Vector Borne Disease Control) field worker application. It is used by health workers (MPHW) to perform residential and field inspections, capture mosquito breeding/density data, record blood samples, and upload geotagged inspection photos.

### Metadata
- **Original Package Name**: `com.amc.healthcare.apq`
- **Application Label**: `AMC VBDC` (Dev: `AMC VBDC Dev`)
- **Main Activity**: `com.amc.healthcare.apq.MainActivity`
- **Framework**: Flutter (compiled to native ARM64 `libapp.so`)
- **Version / Shorebird App ID**: `abe8b65a-61e7-4ed2-bf1d-054e97e16b39`

---

## 2. API Endpoints & Server Configuration

From `assets/flutter_assets/.env.prod` and `.env.dev`:
- **Production Base URL**: `https://api-amcmodules.ahmedabadcity.gov.in:8024`
- **Development Base URL**: `http://117.205.4.132:8012`

### Key API Routes Identified
- `/MPHWDashboard/residentialVbdInspection`
- `/MPHWDashboard/createVbdFieldInspection`
- `/MPHWDashboard/filedInspectionDetail`
- `/MPHWDashboard/filedInspectionList`
- `/MPHWDashboard/gpsLocation`
- `/FieldInspection/GetFieldInspectionList`
- `/FieldInspection/InsertFieldInspection`
- `/Inspection/InsertInspection`
- `/CrossInspection/GetList`
- `/CrossInspection/InsertCrossInspection`
- `/MphwInspection/InsertDailySummary`
- `/VBDC_Inspection_Documents/` (Photo storage endpoint)

---

## 3. Photo Upload & Location Workflow Analysis

The application enforces strict geo-fencing and photo capture requirements during field inspections:

1. **GPS Ward Validation**:
   - The app verifies user latitude and longitude against ward boundary geojson (`Ahmedabad_Ward_Boundary.geojson`).
   - Message displayed if outside ward: *"Please move to your ward to add an inspection."*

2. **Cooldown & Draft System**:
   - Inspection drafts are stored locally in SQLite (`inspection_drafts`).
   - A 2-hour cooldown timer is enforced before adding consecutive inspections.

3. **Photo Capture & Uploadation**:
   - Inspections require capturing live photos (e.g., action taken, breeding site, house details).
   - Images are processed via `ImagePickerFileProvider` and saved to document directories before multipart submission to the `/VBDC_Inspection_Documents` API endpoint.

---

## 4. App Cloner & Fake Camera / Spoofing Modifications

The `base.apk` file was processed with **App Cloner** (`com.applisto.appcloner`), injecting hooking libraries (`libaliuhook.so`, `liblsplant.so`) to bypass standard Android camera and GPS limitations.

### App Cloner Extensions Embedded:
- **Fake Camera (`FakeCameraReceiver` / `FakeCameraActivity`)**:
  - Intercepts system camera intents (`android.media.action.IMAGE_CAPTURE`).
  - Allows selecting pre-existing images from gallery/storage and presenting them to the app as live camera photos.
  - Controls available: Select picture, rotate clockwise/anticlockwise, flip.
- **Location Spoofing (`SpoofLocationReceiver` / `SpoofGpsTrackReceiver`)**:
  - Overrides standard location providers to mock coordinates anywhere in AMC wards.

---

## 5. Instructions for Creating / Replicating standard APK or Cloned APK

### Option A: Standard Build from Source (Flutter)
1. Ensure Flutter SDK (>= 3.x) is installed.
2. Build APK using:
   ```bash
   flutter build apk --release --target-platform android-arm64
   ```
3. Target API base URL in `.env.prod`: `https://api-amcmodules.ahmedabadcity.gov.in:8024`.

### Option B: Repackaging or Cloning via App Cloner
To replicate the exact behavior of `base.apk` with gallery photo upload capability (fake camera override):
1. Install App Cloner Premium or use APK Tool / LSPosed.
2. Enable **Fake Camera** option in App Cloner settings under *Navigation & Camera options*.
3. Enable **Spoof Location** if custom GPS placement is required.
4. Clone and sign the generated APK.
