# Environment Variables Setup Guide

This project now uses environment variables to store sensitive credentials instead of hardcoding them in the configuration file. This provides better security and prevents accidental exposure of your credentials.

## Setup Instructions

### 1. Install python-dotenv

The project now requires the `python-dotenv` package to load environment variables:

```bash
pip install python-dotenv
```

Or if you're using the requirements.txt:

```bash
pip install -r requirements.txt
```

### 2. Create your .env file

1. Copy the `.env.example` file to `.env`:
   ```bash
   cp .env.example .env
   ```

2. Edit the `.env` file and replace the placeholder values with your actual credentials:

```env
# Reddit API Credentials
# Get these from https://www.reddit.com/prefs/apps
REDDIT_CLIENT_ID=your_actual_client_id
REDDIT_CLIENT_SECRET=your_actual_client_secret
REDDIT_USERNAME=your_actual_username
REDDIT_PASSWORD=your_actual_password

# TikTok TTS Session ID (optional)
# Only needed if using TikTok TTS
TIKTOK_SESSIONID=your_actual_session_id

# ElevenLabs API Key (optional)
# Only needed if using ElevenLabs TTS
ELEVENLABS_API_KEY=your_actual_api_key
```

### 3. How to get Reddit API credentials

1. Go to https://www.reddit.com/prefs/apps
2. Click "Create App" or "Create Another App"
3. Fill in the form:
   - **Name**: Your app name
   - **App type**: Select "script"
   - **Description**: Optional description
   - **About URL**: Leave blank
   - **Redirect URI**: http://localhost:8080
4. Click "Create app"
5. Your `client_id` is the string under "personal use script"
6. Your `client_secret` is the "secret" value

### 4. Security Notes

- **Never commit your .env file** - It's already included in .gitignore
- **Keep your credentials secure** - Don't share them publicly
- **Use environment variables in production** - For deployment, set environment variables directly in your hosting environment instead of using .env files

### 5. Alternative: Direct Environment Variables

Instead of using a .env file, you can also set environment variables directly in your system:

**On macOS/Linux:**
```bash
export REDDIT_CLIENT_ID="your_client_id"
export REDDIT_CLIENT_SECRET="your_client_secret"
export REDDIT_USERNAME="your_username"
export REDDIT_PASSWORD="your_password"
```

**On Windows:**
```cmd
set REDDIT_CLIENT_ID=your_client_id
set REDDIT_CLIENT_SECRET=your_client_secret
set REDDIT_USERNAME=your_username
set REDDIT_PASSWORD=your_password
```

### 6. Fallback Behavior

If environment variables are not set, the application will fall back to the values in `config.toml`. However, these should only be placeholder values now for security reasons.

## Migration from Old Setup

If you're migrating from the old setup where credentials were stored in `config.toml`:

1. Copy your credentials from `config.toml` to the new `.env` file
2. Replace the sensitive values in `config.toml` with placeholder text
3. Make sure your `.env` file is not tracked by git (it should be in .gitignore)

The application will automatically load your credentials from the environment variables and override the placeholder values in the config.
