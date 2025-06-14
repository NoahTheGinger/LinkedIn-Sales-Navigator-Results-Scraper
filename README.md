# LinkedIn Sales Navigator Scraper

A powerful userscript to automate the scraping of lead search results from LinkedIn Sales Navigator. It handles pagination, extracts detailed profile information, and exports the collected data into a clean, organized Markdown file.

![Scraper UI](https://github-production-user-asset-6210df.s3.amazonaws.com/186960734/455103587-49742159-46cb-4d16-b54d-0acbaa9ef90e.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250614%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250614T024132Z&X-Amz-Expires=300&X-Amz-Signature=9a9e52e00a3037f29f0953307615761cb5e43ac5f37a018847f908f95df67ad9&X-Amz-SignedHeaders=host)

## Features

- **Automated Scraping**: Extracts lead data from LinkedIn Sales Navigator search result pages.
- **Full Pagination Support**: Automatically navigates through all available pages of search results.
- **Robust Data Extraction**: Captures essential data points for each lead, including:
  - Full Name & Profile URL
  - Profile Image URL
  - Current Title & Company (with URL)
  - Location
  - Connection Degree
  - Recent and Previous Experience
  - Mutual Connections & Shared Education
- **Intelligent Loading**: A smart, iterative scrolling mechanism reliably handles lazy-loading to ensure all 25 profiles per page are loaded before extraction.
- **User-Friendly UI**: An on-page interface to start the scraping process, monitor progress, and export results.
- **Markdown Export**: Generates a clean, well-formatted Markdown file containing all scraped profiles, perfect for reporting or importing into other systems.
- **Configurable**: Easily tweak settings like delays, timeouts, and scroll behavior at the top of the script file.

## Installation

To use this script, you need a userscript manager browser extension. [Tampermonkey](https://www.tampermonkey.net/) is recommended.

1.  **Install a Userscript Manager**:
    -   [Tampermonkey for Chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
    -   [Tampermonkey for Firefox](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/)
    -   [Tampermonkey for Edge](https://microsoftedge.microsoft.com/addons/detail/tampermonkey/iikmkjmpaadaobahmlepofnechongfnn)

2.  **Install the Userscript**:
    -   Open the `LinkedIn-Sales-Navigator-Scraper.user.js` file.
    -   Your userscript manager should automatically detect it and prompt you to install it.
    -   Click **Install**.

## Usage

1.  Navigate to a LinkedIn Sales Navigator people search results page.
    -   Example URL: `https://www.linkedin.com/sales/search/people...`
2.  The **SN Scraper** UI will appear in the top-right corner of the page.
3.  Click the **Start Scraping** button to begin the process. The script will start on the current page and automatically navigate through all subsequent pages.
4.  You can monitor the progress in the UI, which shows the current page and the total number of profiles collected.
5.  Once the scrape is complete, the **Export MD** button will be enabled. Click it to download the Markdown file with all the collected data.

## Configuration

The script includes a `CONFIG` object at the top of the file that allows you to customize its behavior:

-   `DELAY_BETWEEN_PAGES`: Time (in ms) to wait after scraping a page before navigating to the next one.
-   `MAX_RETRIES`: Number of times to retry a failed operation.
-   `BATCH_SIZE`: The expected number of results per page (typically 25).
-   `SCROLL_STEP_PX`: The distance (in pixels) to scroll in each step to trigger lazy-loading.
-   `SCROLL_PAUSE_MS`: The pause (in ms) between each scroll step.
-   `LOAD_TIMEOUT_MS`: The maximum time (in ms) to wait for all profiles on a single page to load.

## Disclaimer

This script is intended for personal use to automate data collection. LinkedIn's terms of service prohibit scraping. Use this tool responsibly and at your own risk. Abusing this script may lead to restrictions on your LinkedIn account.

## 🚀 Features

- **Complete Pagination Support**: Automatically scrapes all pages in your search results
- **Smart Data Extraction**: Captures comprehensive profile information including:
  - Name and profile URL
  - Profile image
  - Current job title and company
  - Location
  - Connection degree (1st, 2nd, 3rd)
  - Mutual connections
  - Shared education
  - Previous work experience
  - Company URLs
- **Beautiful Markdown Export**: Generates well-formatted markdown files with all collected data
- **Progress Tracking**: Real-time UI showing scraping progress and status
- **Error Handling**: Robust error handling with retry mechanisms
- **Configurable Delays**: Respectful scraping with customizable delays between pages

## 📋 Prerequisites

- **Tampermonkey** (Chrome) or **Greasemonkey** (Firefox) browser extension
- Active LinkedIn Sales Navigator subscription
- Access to LinkedIn Sales Navigator search results

## 🛠️ Installation

1. **Install Tampermonkey/Greasemonkey**:
   - Chrome: [Tampermonkey](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo)
   - Firefox: [Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)

2. **Install the Userscript**:
   - Copy the contents of `LinkedIn-Sales-Navigator-Scraper.user.js`
   - Open Tampermonkey dashboard
   - Click "Create a new script"
   - Paste the code and save (Ctrl+S)

3. **Verify Installation**:
   - Navigate to any LinkedIn Sales Navigator search results page
   - You should see a "SN Scraper" widget in the top-right corner

## 🎯 Usage

### Basic Usage

1. **Navigate to Sales Navigator**: Go to LinkedIn Sales Navigator and perform your search
2. **Start the Scraper**: Click the "Start Scraping" button in the scraper widget
3. **Monitor Progress**: Watch the progress bar and status updates
4. **Export Results**: Once complete, click "Export MD" to download your results

### Advanced Configuration

You can modify the scraping behavior by editing these constants in the script:

```javascript
const CONFIG = {
    DELAY_BETWEEN_PAGES: 3000, // 3 seconds between pages
    WAIT_FOR_RESULTS: 2000,    // 2 seconds to wait for results to load
    MAX_RETRIES: 3,            // Maximum retries for failed operations
    BATCH_SIZE: 25             // Expected results per page
};
```

## 📊 Data Extracted

For each profile, the scraper captures:

| Field | Description | Example |
|-------|-------------|---------|
| **Name** | Full name | "Daniel Gindi" |
| **Profile URL** | Direct link to LinkedIn profile | `https://linkedin.com/in/...` |
| **Title** | Current job title | "Data Analyst" |
| **Company** | Current company | "Bentex" |
| **Company URL** | Direct link to company page | `https://linkedin.com/company/...` |
| **Location** | Geographic location | "New York City Metropolitan Area" |
| **Connection Degree** | Relationship level | "2nd", "3rd" |
| **Mutual Connections** | Shared connections count | "6 mutual connections" |
| **Shared Education** | Educational connections | "Shared education" |
| **Experience** | Current role duration | "6 months in role" |
| **Previous Experience** | Past work history | "2023 – 2024 (1 yr 5 mos) Shamco..." |
| **Profile Image** | Profile photo URL | `https://media.licdn.com/...` |

## 📝 Output Format

The scraper generates a beautiful markdown file with the following structure:

```markdown
# LinkedIn Sales Navigator Search Results

**Date**: 2024-01-15
**Search URL**: https://www.linkedin.com/sales/search/people?...
**Total Profiles**: 47

---

## 1. Daniel Gindi

![Profile Image](https://media.licdn.com/...)

**Title**: Data Analyst
**Company**: Bentex
**Location**: New York City Metropolitan Area
**Connection**: 2nd
**Mutual Connections**: 6 mutual connections
**Shared Education**: Shared education
**Experience**: 6 months in role
**Previous Experience**: 2023 – 2024 (1 yr 5 mos) Shamco Management Corp. Software Coordinator
**Profile URL**: [View Profile](https://linkedin.com/...)
**Company URL**: [View Company](https://linkedin.com/...)

---
```

## ⚡ Performance & Behavior

- **Respectful Scraping**: Built-in delays prevent overwhelming LinkedIn's servers
- **Smart Navigation**: Uses URL parameters for reliable page navigation
- **Async Loading**: Waits for dynamic content to load before scraping
- **Memory Efficient**: Processes one page at a time to avoid memory issues
- **Progress Tracking**: Real-time updates on scraping progress

## 🔧 Technical Details

### DOM Selectors Used

The scraper targets these specific LinkedIn Sales Navigator elements:

- **Search Results Container**: `#search-results-container`
- **Profile Cards**: `[data-x-search-result="LEAD"]`
- **Pagination**: `[data-sn-view-name="search-pagination"]`
- **Profile Names**: `[data-view-name="search-results-lead-name"]`
- **Companies**: `[data-view-name="search-results-lead-company-name"]`

### URL Pattern Matching

The script activates on URLs matching:
```
https://www.linkedin.com/sales/search/people*
```

### Pagination Strategy

The scraper detects pagination by:
1. Finding the current page from active pagination button
2. Determining total pages from highest numbered button
3. Navigating using URL parameters (`?page=N`)
4. Waiting for content to load before scraping each page

## 🛡️ Error Handling

- **Network Issues**: Automatic retries for failed requests
- **Missing Elements**: Graceful handling of incomplete profile data
- **Navigation Failures**: Robust page navigation with fallbacks
- **Memory Management**: Efficient data handling for large result sets

## 📁 File Output

- **Filename Format**: `linkedin-sales-navigator-results-YYYY-MM-DD.md`
- **Encoding**: UTF-8 text
- **Format**: Standard Markdown with proper formatting
- **Size**: Typically 10-50KB for 25-100 profiles

## ⚠️ Important Notes

- **Respect LinkedIn's Terms**: Use responsibly and in accordance with LinkedIn's Terms of Service
- **Rate Limiting**: Built-in delays help avoid being flagged by LinkedIn
- **Data Privacy**: All data remains local - nothing is sent to external servers
- **Browser Requirements**: Modern browser with ES6+ support required

## 🔍 Troubleshooting

### Common Issues

1. **Scraper UI not appearing**:
   - Ensure Tampermonkey is enabled
   - Check that you're on a Sales Navigator search results page
   - Refresh the page

2. **No profiles detected**:
   - Wait for search results to fully load
   - Check that results are visible on the page
   - Try refreshing and waiting longer

3. **Export button disabled**:
   - Ensure profiles have been scraped first
   - Check browser console for errors

4. **Navigation issues**:
   - Verify you have access to multiple pages
   - Check your Sales Navigator subscription status

### Debug Mode

To enable debug logging, open browser console and run:
```javascript
localStorage.setItem('sn-scraper-debug', 'true');
```

## 🤝 Contributing

Feel free to submit issues, feature requests, or improvements!

## 📄 License

This project is provided as-is for educational and personal use. Please respect LinkedIn's Terms of Service and use responsibly.
