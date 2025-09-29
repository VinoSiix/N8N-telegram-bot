
# Telegram AI Assistant with Web Search and Voice Transcription

This n8n workflow creates an intelligent Telegram bot that can process both text and voice messages, determine if online research is needed, and provide accurate responses using multiple AI models.

## Workflow Overview

The workflow integrates **Telegram**, **Google Gemini**, **Cohere**, and **Tavily Search** to create a smart assistant that:
1. Receives messages from Telegram (text or voice)
2. Transcribes voice messages to text
3. Determines if internet search is required for the query
4. Either performs a web search and summarizes results, or provides a direct answer
5. Sends the response back to the user via Telegram

## Nodes and Functionality

### Triggers
- **Telegram Trigger** - Listens for incoming Telegram messages
- **When chat message received** - Alternative chat trigger for testing

### Message Processing
- **Switch** - Routes messages based on type (text or voice)
- **Get a file** - Downloads voice message files from Telegram
- **Transcribe a recording** - Converts voice messages to text using Google Gemini

### AI Decision Making
- **Internet needed?** - Uses Google Gemini to determine if web search is required
- **If** - Conditional routing based on AI decision

### Search and Response
- **Search** - Performs web search using Tavily API when needed
- **Summary** - Summarizes search results using Google Gemini
- **Answer** - Provides direct answers using Cohere AI

### Memory
- **Simple Memory** - Maintains conversation context for AI models

## Credentials Required

1. **Telegram API** - For bot communication
2. **Google PaLM API** - For Gemini language models and transcription
3. **Cohere API** - For direct question answering
4. **Tavily API** - For web search capabilities

## How It Works

1. User sends a message to the Telegram bot (text or voice)
2. The workflow receives the message via webhook
3. If it's a voice message:
   - The audio file is downloaded
   - Google Gemini transcribes the voice to text
4. The text (from original message or transcription) is analyzed by Google Gemini to determine if internet search is needed
5. Based on the decision:
   - **If search needed**: Tavily performs web search → Google Gemini summarizes results → Response sent to Telegram
   - **If no search needed**: Cohere provides direct answer → Response sent to Telegram
6. Conversation memory maintains context for follow-up questions

## Setup Instructions

1. Create a Telegram bot using BotFather and obtain the API token
2. Get API keys for:
   - Google Gemini
   - Cohere
   - Tavily Search
3. Configure credentials in n8n for all services
4. Deploy the workflow and use the provided webhook URL for your Telegram bot
5. Test by sending messages to your bot

## Features

- ✅ **Multi-modal input**: Handles both text and voice messages
- ✅ **Intelligent routing**: Automatically decides when to search online
- ✅ **Voice transcription**: Converts audio messages to text
- ✅ **Web search integration**: Uses Tavily for accurate information retrieval
- ✅ **Multiple AI models**: Leverages Google Gemini and Cohere for different tasks
- ✅ **Conversation memory**: Maintains context for better interactions
- ✅ **Conditional responses**: Provides search-based answers or direct responses as appropriate

## Example Usage

- **Direct Answer Query**: "What is 2+2?"
- **Search Required Query**: "What's the weather forecast for New York tomorrow?"
- **Voice Message**: Send a voice note asking any question

The bot will automatically determine the best approach and respond accordingly.

---

*Built with n8n, Google Gemini, Cohere, and Tavily Search*
