# Gemini API

Google Gemini generative services, including chat completions and native generate content API.

![Platform](https://img.shields.io/badge/platform-Ace%20Data%20Cloud-0f766e?style=flat-square) ![API](https://img.shields.io/badge/type-AI%20API-2563eb?style=flat-square) ![Docs](https://img.shields.io/badge/docs-online-16a34a?style=flat-square)

API home page: [Ace Data Cloud - Gemini](https://platform.acedata.cloud/service/gemini)

Keywords: gemini-api, google-gemini, chat-completions, generate-content, rest-api, ai-api, developer-tools, AI API, REST API, Developer API, Ace Data Cloud

## Why Use Gemini on Ace Data Cloud

- Unified developer platform with one API key, billing system, and usage tracking
- Production-ready AI API endpoints served from [https://api.acedata.cloud](https://api.acedata.cloud)
- English integration guides, API references, and service documentation
- Global-ready workflow for developers building chat, image, video, music, and search products

## Overview

Google Gemini is a powerful AI conversation system that supports both OpenAI-compatible chat completions format and Google's native `generateContent` / `streamGenerateContent` endpoints. Gemini models support multi-modal inputs (text and images), thinking mode, function calling, and JSON mode.

## Application Process

To use the Gemini API, apply for the corresponding service on the [Gemini Chat Completion API](https://platform.acedata.cloud/documents/ae54bf9b-af41-4072-b969-3756b6d66834) page. After entering the page, click the "Acquire" button.

There is a free quota available for first-time applicants, allowing you to use this API for free.

## Quick Start

- Base URL: [https://api.acedata.cloud](https://api.acedata.cloud)
- Service page: [Gemini on Ace Data Cloud](https://platform.acedata.cloud/service/gemini)
- Docs: [Developer documentation](https://docs.acedata.cloud)

```bash
curl --request POST "https://api.acedata.cloud/gemini/chat/completions" \
  --header "Authorization: Bearer YOUR_API_KEY" \
  --header "Content-Type: application/json" \
  --data '{
    "model": "gemini-2.5-flash",
    "messages": [{"role": "user", "content": "Hello!"}]
  }'
```

## APIs and Guides

Explore the supported endpoints and integration guides for Gemini.

| API | Path | Integration Guidance |
| ---- | ---- | ------------ |
| [Gemini Chat Completion API](https://platform.acedata.cloud/documents/ae54bf9b-af41-4072-b969-3756b6d66834) | `/gemini/chat/completions` | [Gemini Chat Completion API Integration Guide](docs/gemini_chat_completions_api_integration_guide.md) |
| [Gemini Generate Content API](https://platform.acedata.cloud/documents/gemini-generate-content-api) | `/v1beta/models/{model}:generateContent` | [Gemini Generate Content API Integration Guide](docs/gemini_generate_content_api_integration_guide.md) |
