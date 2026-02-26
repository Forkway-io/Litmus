Litmus — Post Export Repository (English Translation)

Post Export Repository

This repository contains automatically exported posts from various sources.

Repository Structure

The repository is organized as follows:
```
[root directory]/
├── [source_type]/
│   ├── [safe_source_name_id_[ID]]/
│   │   ├── YYYY-MM.csv
│   │   ├── YYYY-MM.csv
│   │   └── ...
│   ├── [another_source_id_[ID]]/
│   │   ├── YYYY-MM.csv
│   │   └── ...
│   └── ...
└── README.md
```
Structure Components

Source type — A category of the source (e.g., telegram, twitter, rss).
Safe source name — The source name sanitized from special characters.
Source ID — A unique source identifier in the system.
Monthly files — CSV files containing posts for a specific month.

CSV File Format

Each CSV file contains posts for one month and has the following columns:
Column
Description
Format
id
Internal post ID in the system
Number
external_id
External post ID from the source
String
message_preview
Message preview (first 50 + ... + last 50 characters)
String
hash
MD5 hash of the full message
String (32 characters)
published_at
Post publication time
ISO format (2023-10-01T12:30:45)
created_at
Record creation time in the system
ISO format
source_id
Source ID
Number
source_name
Source name
String


How to Check a Specific Channel

1. Find the channel by name
Go to the directory for the relevant source type and locate the folder with the channel name. The folder name is generated as follows:
The original channel name is sanitized from special characters
Repeated underscores are collapsed
"id[ID]" is appended at the end
For example, the channel "My Telegram Channel!" will be represented as: My_Telegram_Channel_id_123.

2. Browse the post history
Inside the channel folder, find monthly CSV files. Each file corresponds to one month and contains all posts published in that month.

3. Check a specific month
Open the CSV file for the desired month to view all posts published during that period.


How to Check a Post’s Content

Using message_preview
Each post includes a message_preview field that contains:
The first 50 characters of the message
Ellipsis
The last 50 characters of the message
This makes it possible to quickly assess the content without reading the full text.

Using the hash
The hash field contains the MD5 hash of the full message. This allows you to:
Verify message integrity
Detect changes in content
Compare whether posts are identical

Using timestamps
The published_at field contains the exact publication time in ISO format.


Search Example

Suppose you want to find posts from the Telegram channel "News Channel" for October 2023:
1. Navigate to: telegram/News_Channel_id_456/
2. Open the file: 2023-10.csv
3. Review all posts for that month

Working with CSV Files

CSV files can be opened in:
- Spreadsheet editors (Excel, Google Sheets, LibreOffice Calc)
- Text editors with CSV support
- Via the command line using csvkit, xsv, or similar utilities

Example: viewing via the command line

head -n 10 2023-10.csv

column -t -s, 2023-10.csv | less -S

Notes

• All file and directory names use safe characters
• Months are in YYYY-MM format
• Time is in UTC
• The repository is automatically updated when new posts appear
• CSV files use UTF-8 encoding
• Delimiter: comma
• The first row contains headers

