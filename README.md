# Gemini API

Generate text and build conversations with Gemini models through Ace Data Cloud.

[API documentation](https://platform.acedata.cloud/documents/gemini-chat-completion-integration?lang=en&utm_source=github&utm_medium=referral&utm_campaign=evergreen) · [Models and pricing](https://platform.acedata.cloud/services/gemini?utm_source=github&utm_medium=referral&utm_campaign=evergreen) · [中文文档](https://platform.acedata.cloud/documents/gemini-chat-completion-integration?lang=zh-cn&utm_source=github&utm_medium=referral&utm_campaign=evergreen)

## Get an API key

1. Open [Applications](https://platform.acedata.cloud/console/applications?lang=en&utm_source=github&utm_medium=referral&utm_campaign=evergreen) and sign in or register.
2. Find **General Application** and click the copy button marked **1**. If needed, select **Initialize General Application** first. Confirm access to this service and enough balance for your request.

![Copy the API key from General Application using the button marked 1](https://raw.githubusercontent.com/AceDataCloud/SunoDify/8d3d03570e73324220f111f7fe343da0792a8071/_assets/tutorial/get-api-key-en.png)

3. Save the copied key in your terminal. The examples add the `Bearer` prefix in the HTTP header.

```bash
export ACEDATACLOUD_API_KEY='YOUR_API_KEY'
```

## Quickstart

### Request

```bash
curl --fail-with-body --silent --show-error https://api.acedata.cloud/gemini/chat/completions \
  --header "Authorization: Bearer $ACEDATACLOUD_API_KEY" \
  --header 'Content-Type: application/json' \
  --data '{
  "model": "gemini-4-neon",
  "messages": [
    {
      "role": "user",
      "content": "Explain what an API is in one sentence."
    }
  ],
  "stream": false
}'
```

### Response JSON

Illustrative response. Your request returns its own ID, text and token usage.

```json
{
  "id": "chatcmpl-example",
  "object": "chat.completion",
  "created": 1790000000,
  "model": "gemini-4-neon",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "An API lets software request data or actions from another service."
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 18,
    "completion_tokens": 15,
    "total_tokens": 33
  }
}
```

Read `choices[0].message.content` for the answer and `usage` for token counts.

## APIs and Guides

Explore the supported endpoints and integration guides for Gemini.

| API | Path | Integration Guidance |
| ---- | ---- | ------------ |
| [Gemini Chat Completion API](https://platform.acedata.cloud/documents/gemini-chat-completions?utm_source=github&utm_medium=referral&utm_campaign=evergreen) | `/gemini/chat/completions` | [Gemini Chat Completion API Integration Guide](docs/gemini_chat_completions_api_integration_guide.md) |
| [Gemini Generate Content API](https://platform.acedata.cloud/documents/gemini-generate-content-api?utm_source=github&utm_medium=referral&utm_campaign=evergreen) | `/v1/models/{model}:generateContent` | [Gemini Generate Content API Integration Guide](docs/gemini_generate_content_api_integration_guide.md) |

## Troubleshooting

- For authentication errors, open [Manage Keys](https://platform.acedata.cloud/console/credentials?lang=en&utm_source=github&utm_medium=referral&utm_campaign=evergreen) to check the key’s allowed APIs, expiration and usage limit.
- For insufficient balance, open the application and review its balance and the current service price.
- For request validation errors, compare the model and required fields with the linked API reference.
- For a long-running or failed task, retain `task_id` and `trace_id` when contacting [support](https://platform.acedata.cloud/support?utm_source=github&utm_medium=referral&utm_campaign=evergreen).

## Trial account concurrency

Accounts with neither a successful paid top-up nor an administrator's manual credit addition may run **one billable request at a time across the entire account**, shared by all API keys and services. Rewards, redemption cards and transferred credits do not count as paid top-ups. A successful paid top-up or manual credit addition removes this trial restriction; balance and key usage-limit checks still apply.

A new billable request returns `429 too_many_requests` while another is running. Wait for the active request's final result before submitting the next one. Free task polling remains available.

For async APIs, acceptance or a task ID is not completion: keep querying the same task until its final result. A disconnect or proxy timeout does not mean execution stopped. If a task has no terminal result for a long time, contact support with `trace_id`.

This restriction changes neither trial API availability nor pricing; fees are settled after execution based on actual usage.
