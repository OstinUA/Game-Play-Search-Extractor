# Google Play Search Extractor

A lightweight Chrome Extension built with Manifest V3 designed to extract and export application links from Google Play Store search result pages. 

This tool helps developers, ASO specialists, and researchers quickly gather lists of app URLs without manual copying. It intelligently filters for unique, visible items, ensuring high-quality data extraction.

## Features

* **Smart Extraction**: Captures links only from the visible search results area.
* **Noise Reduction**: Automatically ignores hidden elements and footer links.
* **Deduplication**: Ensures every extracted URL is unique (removes duplicate listings of the same app).
* **Clean Formatting**: Exports raw, clean URLs (removes unnecessary tracking parameters).
* **Manifest V3**: Compliant with the latest Chrome Extension security and performance standards.

## Installation

Since this extension is not yet published on the Chrome Web Store, you can install it in "Developer Mode":

1.  Clone this repository:
    ```bash
    git clone [https://github.com/OstinUA/Google-Play-Search-Extractor.git](https://github.com/OstinUA/Google-Play-Search-Extractor.git)
    ```
2.  Open Chrome and navigate to `chrome://extensions/`.
3.  Enable **Developer mode** using the toggle switch in the top right corner.
4.  Click the **Load unpacked** button.
5.  Select the directory where you cloned the repository.

## Usage

1.  Navigate to the [Google Play Store](https://play.google.com/store/search).
2.  Perform a search (e.g., "Strategy Games").
3.  Scroll down to load more results if necessary.
4.  Click the extension icon in the Chrome toolbar.
5.  Click the **"Собрать только видимые игры"** (Collect visible games) button.
6.  The extension will display the count of found apps and populate the text area with clean URLs.
7.  Copy the results from the text area.

## Technical Details

* **Manifest Version**: 3
* **Permissions**: `activeTab`, `scripting`
* **Host Permissions**: `https://play.google.com/*`
* **Logic**: The script checks `offsetParent` to determine visibility and validates that the link is not within the `<footer>` tag before extraction.

## 📂 Project Structure

```text
├── content.js      # Background content script (auto-run)
├── manifest.json   # Extension configuration
├── popup.html      # Extension popup UI
├── popup.js        # Logic for the popup actions and link extraction
└── icons/          # Extension icons
