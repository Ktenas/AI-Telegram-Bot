# AI Telegram Bot

A lightweight Telegram bot that integrates with OpenWebUI API to provide AI-powered conversational responses. This bot acts as a bridge between Telegram users and OpenWebUI's language models, enabling seamless AI interactions through Telegram.

## Features

- 🤖 **AI-Powered Responses**: Leverages OpenWebUI API for intelligent, context-aware replies
- 💬 **Simple Interface**: Direct message interaction with the bot
- 🔄 **Real-time Processing**: Continuous polling for instant message handling
- ⚙️ **Configurable**: Easy setup through environment variables
- 🛡️ **Error Handling**: Robust error handling for API failures

## Prerequisites

Before running the bot, ensure you have:

- Python 3.6 or higher
- A Telegram Bot Token (from [@BotFather](https://t.me/botfather))
- Access to an OpenWebUI instance with API endpoint
- OpenWebUI API token

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Ktenas/AI-Telegram-Bot.git
   cd AI-Telegram-Bot
   ```

2. **Install required dependencies**:
   ```bash
   pip install requests
   ```

   Alternatively, if you're using a virtual environment (recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install requests
   ```

## Configuration

The bot requires three environment variables to be set:

### Required Environment Variables

- `TELEGRAM_BOT_TOKEN`: Your Telegram bot token from BotFather
- `OPENWEBUI_API`: The OpenWebUI API endpoint (should end with `/api/chat/completions`)
- `OPENWEBUI_TOKEN`: Your OpenWebUI API authentication token

### Setting Environment Variables

**Linux/Mac:**
```bash
export TELEGRAM_BOT_TOKEN="your_telegram_bot_token"
export OPENWEBUI_API="https://your-openwebui-instance.com/api/chat/completions"
export OPENWEBUI_TOKEN="your_openwebui_token"
```

**Windows (Command Prompt):**
```cmd
set TELEGRAM_BOT_TOKEN=your_telegram_bot_token
set OPENWEBUI_API=https://your-openwebui-instance.com/api/chat/completions
set OPENWEBUI_TOKEN=your_openwebui_token
```

**Windows (PowerShell):**
```powershell
$env:TELEGRAM_BOT_TOKEN="your_telegram_bot_token"
$env:OPENWEBUI_API="https://your-openwebui-instance.com/api/chat/completions"
$env:OPENWEBUI_TOKEN="your_openwebui_token"
```

### Using a .env File (Optional)

For development, you can create a `.env` file in the project root (this file is git-ignored):

```env
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
OPENWEBUI_API=https://your-openwebui-instance.com/api/chat/completions
OPENWEBUI_TOKEN=your_openwebui_token
```

Then install and use `python-dotenv`:
```bash
pip install python-dotenv
```

## Usage

1. **Set up your environment variables** as described in the Configuration section.

2. **Run the bot**:
   ```bash
   python telegram_openwebui_bot
   ```

3. **Start chatting**: Open Telegram and search for your bot. Send any message to receive an AI-generated response!

The bot will start polling for messages and respond to any text sent to it.

## How It Works

1. The bot continuously polls the Telegram API for new messages
2. When a message is received, it forwards the text to the OpenWebUI API
3. OpenWebUI processes the request using the configured model (default: `chatgpt-4o-latest`)
4. The AI response is sent back to the user via Telegram

## Model Configuration

By default, the bot uses the `chatgpt-4o-latest` model with a temperature of 0.7. To change the model or parameters, edit the `ask_openwebui()` function in the `telegram_openwebui_bot` file:

```python
payload = {
    "messages": [{"role": "user", "content": prompt}],
    "temperature": 0.7,
    "model": "your-preferred-model"
}
```

## Troubleshooting

### Bot doesn't respond
- Verify your `TELEGRAM_BOT_TOKEN` is correct
- Check that your bot is not already running elsewhere
- Ensure your environment variables are properly set

### API errors
- Confirm your `OPENWEBUI_API` endpoint is correct and accessible
- Verify your `OPENWEBUI_TOKEN` is valid
- Check the console output for detailed error messages

### Connection issues
- Ensure you have internet connectivity
- Check if your OpenWebUI instance is running and accessible
- Verify firewall settings aren't blocking the connection

## Contributing

Contributions are welcome! Feel free to:

- Report bugs
- Suggest new features
- Submit pull requests

## License

This project is open source and available under the MIT License.

## Acknowledgments

- Built with the [Telegram Bot API](https://core.telegram.org/bots/api)
- Powered by [OpenWebUI](https://github.com/open-webui/open-webui)

## Support

For issues, questions, or suggestions, please open an issue on the [GitHub repository](https://github.com/Ktenas/AI-Telegram-Bot/issues).
