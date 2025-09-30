
# Telegram AI Assistant Bot

A powerful Telegram bot built with n8n that combines voice transcription, web search, weather information, calendar integration, image generation, and crypto price checking into a single intelligent assistant.

## Features

- **Voice Message Support**: Automatically transcribes voice messages and processes the text content
- **Web Search**: Performs intelligent web searches using Tavily AI for general knowledge queries
- **Weather Information**: Provides current weather information for Phuket, Thailand
- **Calendar Integration**: Creates events in Google Calendar
- **Image Generation**: Generates images using Google Gemini based on user requests
- **Crypto Price Checking**: Retrieves cryptocurrency prices and market information
- **Smart Routing**: Automatically determines the appropriate action based on user input

## Workflow Overview

The bot processes incoming Telegram messages through the following flow:

1. **Message Reception**: Listens for incoming messages via Telegram Trigger
2. **Content Detection**: Switch node determines if message is text or voice
3. **Voice Processing**: If voice message:
   - Downloads the audio file
   - Transcribes using Google Gemini
   - Simplifies transcription to remove non-speech sounds
4. **Intent Analysis**: AI agent analyzes what services are needed (internet search, weather/calendar, crypto, image generation)
5. **Action Routing**: Switch nodes route to appropriate services based on intent
6. **Response Generation**: Various AI agents and tools generate responses
7. **Telegram Response**: Sends processed response back to user

## Node Breakdown

### Core Nodes
- **Telegram Trigger2**: Listens for incoming Telegram messages
- **what is needed?**: Analyzes message intent and determines required services
- **Switch nodes**: Route messages based on content type and required actions

### Voice Processing
- **Get a file1**: Downloads voice message files from Telegram
- **Transcribe a recording1**: Transcribes audio using Google Gemini
- **Simplify audio**: Cleans transcription by removing non-speech content

### AI Processing
- **Multiple Google Gemini Chat Models**: Provide language model capabilities for various agents
- **Weather or calendar**: Processes weather and calendar requests for text messages
- **Weather or calendar voice**: Processes weather and calendar requests for voice messages
- **AI Agent nodes**: Handle general AI queries and crypto price checking

### External Services
- **Search2/Search3**: Web search using Tavily
- **OpenWeatherMap/OpenWeatherMap1**: Weather information retrieval
- **Create an event in Google Calendar**: Calendar event creation
- **Generate an image/Generate an image1**: Image creation using Google Gemini

### Response Handling
- **Summary/Summaryy**: Summarizes search results
- **Send a text message**: Sends text responses back to Telegram
- **Send a photo message1**: Sends generated images back to Telegram

## Setup Requirements

1. **Telegram Bot Token**: Create a bot via BotFather and obtain the API token
2. **Google Gemini API Key**: Required for voice transcription and AI processing
3. **Google Calendar API**: Setup OAuth credentials for calendar integration
4. **OpenWeatherMap API Key**: For weather information services
5. **Tavily API Key**: For web search capabilities

## Usage

Simply send a message to your Telegram bot:
- **Text messages**: Will be processed directly for intent analysis
- **Voice messages**: Will be transcribed and then processed
- The bot automatically determines what information or service you need and responds accordingly

## Response Types

- **General Knowledge**: Web search results with AI summarization
- **Weather Information**: Current weather conditions for Phuket
- **Calendar Events**: Event creation confirmation
- **Image Generation**: Generated images based on your description
- **Crypto Information**: Cryptocurrency prices and market data

## Technical Architecture

The workflow uses a modular approach with dedicated AI agents for different functions:
- Intent classification agent
- Web search and summarization agents
- Weather and calendar processing agents
- Image generation agents
- Crypto price checking agents

All processing is handled through Google Gemini language models with appropriate routing logic to ensure efficient and accurate responses.

---

*Built with n8n - The workflow automation platform*
