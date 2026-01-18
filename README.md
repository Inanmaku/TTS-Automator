# ElevenLabs Google Sheets Text-to-Speech Generator

This project demonstrates API integration, automation with Google Apps Script, and handling third-party rate limits.
Built as a practical automation project to demonstrate real-world API usage, error handling, and Google Apps Script workflows.

It’s ideal for:
Voice generation
Audiobook creation
Script narration
Batch text-to-speech workflows
Testing ElevenLabs voices quickly

Features:
Uses ElevenLabs Text-to-Speech API
Reads text directly from Google Docs
Outputs MP3 files
Automatically saves audio to Google Drive
Custom menu inside Google Sheets
Supports multiple voices
Error handling per row
Works with the free ElevenLabs plan (limited) and fully supports paid plans
Easily configurable for paid ElevenLabs plans

How the System Works:
Google Sheet
 ├── Column A → Voice Name (exact name from ElevenLabs)
 ├── Column B → Google Doc URL
 ├── Column C → Output (MP3 link or error message)

Google Drive
 └── ElevenLabs_MP3s/
      ├── VoiceName_timestamp.mp3

Required Sheet Format:
| Column | Purpose                                        |
| ------ | ---------------------------------------------- |
| A      | **Voice Name** (must match ElevenLabs exactly) |
| B      | **Google Docs URL**                            |
| C      | **Output** (auto-generated)                    |

Example:
| Voice Name       | Google Doc URL                                                                | Output |
| ---------------- | ----------------------------------------------------------------------------- | ------ |
| Rachel – Elegant | [https://docs.google.com/document/d/](https://docs.google.com/document/d/)... | (auto) |

IMPORTANT: Voice Name Rules:
ElevenLabs now uses full descriptive voice names, such as:

Rachel – Elegant
Adam – Deep
Bella – Warm
Josh – Conversational

You must copy the full name exactly
Shortened names will NOT work

The script matches voice names exactly as returned by the ElevenLabs API.

Google Docs Requirements:

Your Google Doc must:
Be accessible to your Google account
Be viewable without restrictions
Contain plain text
NOT be in “restricted access” mode
If the script cannot read the document, it will return: No text found in doc

Setup Instructions:

Create the Google Sheet:
Open Google Sheets
Click Extensions → Apps Script
Paste the full script
Save

Add Your ElevenLabs API Key:
Find this line:
const API_KEY = "your_api_key"
Replace with:
const API_KEY = "sk-xxxxxxxxxxxxxxxxxxxx"

You can get your key from:
https://elevenlabs.io

After saving:
Reload the page
A new menu will appear:
ElevenLabs TTS → Generate Voices

Fill the Sheet
Enter voice name (exact match)
Paste Google Docs link
Leave column C empty

Generate Audio:
Click: ElevenLabs TTS → Generate Voices
The script will:
Fetch the document text
Send it to ElevenLabs
Generate an MP3
Save it to Drive
Paste the file link into Column C

Files are saved automatically to:
Google Drive / ElevenLabs_MP3s
Example filenames:
Rachel – Elegant_1700000000000.mp3
Adam – Deep_1700000001234.mp3

Free Plan:
If you are using the free ElevenLabs plan:
You can only generate a few times
After ~3 requests, you may hit:
Rate limits
Character limits
Temporary lockouts
You may need to wait before running again

Paid Plan:
Paid plans should use the eleven_multilingual_v3 model for best performance and higher limits.

How to enable v3
Change this line in the script: 
const MODEL_ID = "eleven_multilingual_v2";
to:
const MODEL_ID = "eleven_multilingual_v3";
That’s all.

Security Notes:
Never share your API key publicly
Don’t commit your API key to GitHub
Use private repositories or environment variables
Restrict Google Doc access if needed

License:
Free to use and modify for personal or commercial projects.
No warranty provided.

Tech Stack:
- Google Apps Script (JavaScript)
- ElevenLabs REST API
- Google Sheets & Google Docs
- Google Drive API
