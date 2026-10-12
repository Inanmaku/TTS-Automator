# ElevenLabs Google Sheets Text-to-Speech Generator

A Google Apps Script project that integrates the ElevenLabs API with Google Sheets to automate voice generation from Google Docs. Demonstrates API integration, automation, and error handling.

Ideal for voice generation, audiobook creation, script narration, and batch text-to-speech workflows.

## Features

- Generates MP3 files using the ElevenLabs Text-to-Speech API
- Reads text directly from Google Docs
- Automatically saves audio to Google Drive
- Custom menu in Google Sheets
- Supports multiple voices and per-row error handling
- Works with free plans within their limits and supports paid plans

## How It Works

The Google Sheet uses three columns:

| Column | Purpose |
|---|---|
| A | Voice Name (exact name from ElevenLabs) |
| B | Google Docs URL |
| C | Output (MP3 link or error message) |

Generated files are saved to `Google Drive/ElevenLabs_MP3s/` with filenames such as `Rachel – Elegant_1700000000000.mp3`.

## Important: Voice Name Rules

ElevenLabs uses descriptive voice names, for example:

- `Rachel – Elegant`
- `Adam – Deep`
- `Bella – Warm`
- `Josh – Conversational`

**Copy the full voice name exactly as returned by the ElevenLabs API.** Shortened names may not work because the script matches voice names exactly.

## Google Docs Requirements

Your document must be accessible to the Google account running the script and contain readable text. Restricted documents or documents the script cannot access may cause errors such as `No text found in doc`.

## Setup

1. Create a Google Sheet and open **Extensions → Apps Script**.
2. Paste the script and save it.
3. Replace `your_api_key` with your own ElevenLabs API key. Get one at [elevenlabs.io](https://elevenlabs.io).
4. Reload the spreadsheet.
5. Enter the exact voice name in column A and the Google Docs URL in column B. Leave column C for the output.
6. Select **ElevenLabs TTS → Generate Voices**.

The script retrieves the document text, generates the MP3, saves it to Drive, and writes the link or an error message to column C.

## Free and Paid Plans

**Free plan:** Usage is limited by your account's available quota, character limits, and API rate limits. You may need to wait if you reach a limit.

**Paid plans:** Available quotas and features depend on your subscription. You can change the model in the script if your account supports it.

For example, change:

`const MODEL_ID = "eleven_multilingual_v2";`

to:

`const MODEL_ID = "eleven_multilingual_v3";`

Check ElevenLabs' current model availability and plan limits before switching.


## Tech Stack

- Google Apps Script (JavaScript)
- ElevenLabs REST API
- Google Sheets and Google Docs
- Google Drive

