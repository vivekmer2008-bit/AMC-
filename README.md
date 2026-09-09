# AMC VBDC Application & APK Clone Analysis

This repository contains the analysis and context for the AMC VBDC (Ahmedabad Municipal Corporation - Vector Borne Disease Control) mobile application (`base.apk`).

## Quick Overview

- **App Name**: AMC VBDC (`com.amc.healthcare.apq`)
- **Technology Stack**: Flutter (Dart) + Native Android Extensions + App Cloner Mods
- **Backend API**: `https://api-amcmodules.ahmedabadcity.gov.in:8024` (Production) / `http://117.205.4.132:8012` (Dev)
- **Key Modules**:
  - Residential VBD Inspection
  - Field Inspection & Summary Reports
  - Cross Inspection
  - MPHW (Multi-Purpose Health Worker) Dashboard
  - GPS Location verification & Photo Uploads with Cooldowns

## Repository Structure

- `base.apk`: The reference APK file for the AMC VBDC application.
- `ANALYSIS.md`: Complete reverse engineering and feature analysis, including photo upload mechanisms, location spoofing/fake camera integration, and API endpoint details.
