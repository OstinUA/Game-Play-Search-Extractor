# Game Store Link Extractor

A versatile Chrome Extension built with **Manifest V3** designed to extract and export application links from both **Google Play Store** and **Apple App Store** search result pages.

This tool helps developers, ASO specialists, and researchers quickly gather lists of app URLs without manual copying. It automatically detects the active store, filters for unique, visible items, and cleans the URLs for international use.

## Features

* **Dual Store Support**: Works seamlessly on `play.google.com` and `apps.apple.com`.
* **Smart Extraction**: Captures links only from the visible search results area, ignoring hidden elements.
* **Noise Reduction**: Automatically excludes footer links and navigation menus (e.g., `#globalnav` on Apple).
* **Deduplication**: Ensures every extracted URL is unique using Set logic.
* **Clean Formatting**:
    * **Google Play**: Extracts the `id` parameter to form clean URLs.
    * **App Store**: Extracts the ID via regex (`/id\d+/`) and removes regional codes (e.g., `/us/`, `/ru/`).

## Installation

Since this extension is not published on the Chrome Web Store, you can install it in "Developer Mode":

1.  Clone this repository:
    ```bash
    git clone [https://github.com/OstinUA/Game-Play-Search-Extractor.git](https://github.com/OstinUA/Game-Play-Search-Extractor.git)
    ```
2.  Open Chrome and navigate to `chrome://extensions/`.
3.  Enable **Developer mode** using the toggle switch in the top right corner.
4.  Click the **Load unpacked** button.
5.  Select the directory where you cloned the repository.

## Usage

### Google Play Store
1.  Navigate to [Google Play Search](https://play.google.com/store/search).
2.  Perform a search (e.g., "Strategy Games") and scroll to load results.
3.  Click the extension icon. The status will show **"Google Play Store"**.
4.  Click **"Собрать ссылки"** (Collect links).

### Apple App Store
1.  Navigate to [App Store Search](https://www.apple.com/us/search) or any category page.
2.  Ensure apps are visible on the screen.
3.  Click the extension icon. The status will show **"Apple App Store"**.
4.  Click **"Собрать ссылки"** (Collect links).

## Technical Details

* **Manifest Version**: 3
* **Permissions**: `activeTab`, `scripting`
* **Architecture**: The extension uses the `chrome.scripting` API to inject the specific extraction logic dynamically based on the active tab's domain.

## Project Structure

```text
├── icons/          # Extension icons
├── manifest.json   # Extension configuration and permissions
├── popup.html      # User interface
└── popup.js        # Core logic: URL detection and extraction algorithms
