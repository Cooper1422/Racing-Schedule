# 🏁 Racing Schedule Discord Bot

A Discord bot that automatically posts daily race reminders from your iRacing schedule stored in Google Sheets.

## Features

- ✅ **Daily Reminders at 8 AM EST** - Automatically posts race info every morning
- ✅ **Google Sheets Integration** - Pull schedule directly from your spreadsheet
- ✅ **Detailed Race Info** - Shows date, time, class, track, laps, fast repairs, and tires
- ✅ **Friendly Messages** - Posts a nice message if there's no race that day
- ✅ **Manual Command** - Use `!race` to check today's race anytime

## Setup Instructions

### Step 1: Create a Google Sheet

1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet
2. Name it: **Racing Schedule**
3. Add these column headers in the first row:
   - `Date` (format: MM/DD/YYYY)
   - `Time` (format: HH:MM AM/PM)
   - `Race Class`
   - `Track`
   - `Laps`
   - `Fast Repairs`
   - `Tires`

4. Add your races below (example):

| Date | Time | Race Class | Track | Laps | Fast Repairs | Tires |
|------|------|-----------|-------|------|--------------|-------|
| 06/15/2026 | 08:00 PM | GT3 | Silverstone | 30 | On | Road |
| 06/22/2026 | 07:00 PM | F4 | Monza | 25 | Off | Soft |

### Step 2: Set Up Google Service Account

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project (name: `Racing Schedule Bot`)
3. Enable the **Google Sheets API** and **Google Drive API**
4. Go to "Credentials" → Create a new "Service Account"
5. Generate a JSON key and download it
6. Rename the file to `credentials.json` and place it in your project folder
7. Share your Google Sheet with the service account email (found in the JSON file)

### Step 3: Create a Discord Bot

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click "New Application" and name it `Racing Schedule Bot`
3. Go to the "Bot" section and click "Add Bot"
4. Copy the **Token** (you'll need this)
5. Under "OAuth2" → "URL Generator":
   - Select scopes: `bot`
   - Select permissions: `Send Messages`, `Embed Links`, `Read Message History`
   - Copy the generated URL and open it to add the bot to your Discord server

### Step 4: Get Your Channel ID

1. In Discord, enable **Developer Mode** (User Settings → Advanced → Developer Mode)
2. Right-click your main chat channel and select "Copy Channel ID"
3. Save this ID (you'll need it)

### Step 5: Deploy the Bot

#### Option A: Railway (Recommended - Free & Easy)

1. Go to [Railway.app](https://railway.app)
2. Sign in with GitHub
3. Create a new project → "Deploy from GitHub repo"
4. Connect your `Racing-Schedule` repository
5. Add environment variables:
   - `DISCORD_TOKEN` = Your Discord bot token
   - `CHANNEL_ID` = Your Discord channel ID
6. Railway will automatically deploy and run your bot 24/7

#### Option B: Run Locally (For Testing)

1. Clone this repository:
   ```bash
   git clone https://github.com/Cooper1422/Racing-Schedule.git
   cd Racing-Schedule
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Create a `.env` file in the project folder:
   ```
   DISCORD_TOKEN=your_discord_bot_token
   CHANNEL_ID=your_channel_id
   ```

4. Place your `credentials.json` in the project folder

5. Run the bot:
   ```bash
   python bot.py
   ```

## Usage

### Automatic Daily Reminder
The bot will automatically post at 8 AM EST every day with today's race info (or a friendly message if there's no race).

### Manual Command
Type `!race` in your Discord server to check today's race anytime.

## Troubleshooting

### Bot isn't posting?
- Check that your Google Sheet is named exactly `Racing Schedule`
- Verify the service account email has access to the sheet
- Make sure `CHANNEL_ID` and `DISCORD_TOKEN` are correct
- Check Railway/local logs for errors

### Wrong time zone?
- The bot uses EST (Eastern Standard Time). To change, edit `bot.py` and replace `'US/Eastern'` with your timezone

### Can't find Channel ID?
- Make sure Developer Mode is enabled in Discord
- Right-click the channel and look for "Copy Channel ID" option

## Support

If you run into issues:
1. Check the logs (Railway dashboard or console output)
2. Verify all credentials are correct
3. Make sure your Google Sheet has the exact column names
4. Ensure the bot has permission to send messages in the channel

## License

Feel free to use and modify as needed!

---

**Happy Racing! 🏎️**
