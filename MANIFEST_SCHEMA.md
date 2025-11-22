# Manifest Schema

This document describes the schema for `manifest.json`, which serves as the single source of truth for launcher and game build information.

## Purpose

The `manifest.json` file contains metadata about available launcher versions and game builds. It is hosted in the `maximum_security_dist` repository and is used by the launcher to determine what versions are available for download.

## Top-Level Fields

- `manifest_version` (integer): Version of the manifest schema. Currently `1`.

## Launcher Section

The `launcher` object contains information about the latest launcher release:

- `version` (string): Version string from `launcher/package.json`.
- `windows` (object): Windows-specific launcher metadata:
  - `url` (string): URL to download the launcher installer. Will eventually point to a GitHub Release asset.
  - `sha256` (string): SHA256 hash of the installer file for integrity verification.
  - `size_bytes` (integer): Size of the installer file in bytes.
- `notes` (string): Release notes or changelog for this launcher version.

## Game Builds Section

`game_builds` is an array of objects, each representing a game build:

- `version` (string): Game version identifier.
- `label` (string): Human-friendly name for this build.
- `channel` (string): Release channel, e.g. `"stable"` or `"experimental"`.
- `recommended` (boolean): Whether this build is recommended for general use.
- `windows` (object): Windows-specific game build metadata:
  - `url` (string): URL to download the game zip. Will eventually point to a GitHub Release asset.
  - `sha256` (string): SHA256 hash of the zip file for integrity verification.
  - `size_bytes` (integer): Size of the zip file in bytes.
- `changelog` (string, optional): Changelog or release notes for this game version.

## Future Integration

Currently, URLs are set to `"TO_BE_FILLED_WITH_GITHUB_RELEASE_URL"` placeholders. In a future iteration, these will be replaced with actual GitHub Release asset URLs when the build scripts are integrated with GitHub Releases.
