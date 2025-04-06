# Time-Triggered Routines Web Application

A static web application that displays time-based routines fetched from a Google Spreadsheet. The application shows the current routine based on the day and time, displaying the content in an iframe.

## Overview

This application serves as a digital routine display system that:

1. Fetches routine data from a Google Spreadsheet
2. Determines the current applicable routine based on the current day and time
3. Displays the routine content in an iframe
4. Shows the next upcoming routine
5. Supports special dates (like holidays or specific events)
6. Includes Google Cast functionality for displaying on Chromecast devices

## How It Works

### Data Source

The application reads data from a Google Spreadsheet published as CSV:
- Spreadsheet URL: https://docs.google.com/spreadsheets/d/1_dIMHuBOkZdQ08XwRWkF5KZvlkm5hmRB8TaKQ_SpA5A/pub?output=csv
- The spreadsheet contains columns for:
  - Name: The name of the routine
  - Days: When the routine applies (e.g., "week" for weekdays, "wkend" for weekends, "all" for every day, or specific days like "mo,tu,we")
  - Time: When the routine starts (e.g., "8:00 AM")
  - URL: Link to content to display (typically Google Slides)

### Special Features

- **Day Parsing**: Supports various day formats including:
  - "week" (Monday-Friday)
  - "wkend" (Saturday-Sunday)
  - "all" (every day)
  - Day abbreviations (e.g., "mo,tu,we" or "su")
  
- **Special Days**: Supports special dates in "mm/dd" format that override regular routines

- **Sidebar Content**: A special "sidebar" entry can be used to display content in the left sidebar

- **Sound Notifications**: Optional sound alerts when routines change (requires user activation)

- **Chromecast Support**: Includes Google Cast functionality via the sender.html file

### Layout

The application has a two-column layout:
- Left column: Shows current date/time, next routine information, and optional sidebar content
- Right column: Displays the current routine name and its associated content in an iframe

## Technical Implementation

- Pure HTML, CSS, and JavaScript (no framework dependencies)
- Uses XMLHttpRequest to fetch CSV data from Google Sheets
- Parses and sorts routines by day and time
- Updates display every minute to check for routine changes
- Uses Google Cast API for Chromecast integration

## Usage

1. Set up a Google Spreadsheet with the following columns:
   - Name: Routine name
   - Days: When the routine applies
   - Time: When the routine starts
   - URL: Content to display (typically Google Slides)

2. Publish the spreadsheet to the web as CSV

3. The application will automatically:
   - Load the latest data
   - Display the current applicable routine
   - Update as time progresses

## Deployment

This is a static web application hosted on GitHub Pages at:
https://briandherbert.github.io/

## Future Enhancements (TODOs)

As noted in notes.txt:
- Auto-toggle proxy
- Use user-agent to hide buttons on casted device
- Add seconds display
