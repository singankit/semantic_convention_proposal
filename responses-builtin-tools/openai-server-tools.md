# Google Gemini Server Tools

## Request
```python
import os
from openai import OpenAI

client = OpenAI(
    api_key="...",
    base_url="...",
)

response = client.responses.create(
    model="gpt-4o-mini",
    tools=[
        {
            "type": "web_search"
        },
        {
            "type": "code_interpreter",
            "container": {"type": "auto"}
        }
    ],
    input="Find syntactially correct code to calculate factorial in Python using web search and execute it using code interpreter.",
    include=[
        'code_interpreter_call.outputs',
        'web_search_call.action.sources',
    ],
    tool_choice="required",
)

print(response.model_dump_json(indent=2))
```

## Response

# OpenAI API Response

**Response ID:** `resp_0be194b6f69aea1900695d80678e8c8194ba09d9d89684aed1`  
**Model:** `gpt-4o-mini`  
**Object:** `response`  
**Status:** `completed`  
**Date:** January 6, 2026

---

<details>
<summary><strong>📋 Basic Response Information</strong></summary>

| Field | Value |
|-------|-------|
| **ID** | `resp_0be194b6f69aea1900695d80678e8c8194ba09d9d89684aed1` |
| **Created At** | `1767735399.0` |
| **Model** | `gpt-4o-mini` |
| **Object** | `response` |
| **Status** | `completed` |
| **Store** | `true` |

**Null Fields:**
- `error`: `null`
- `incomplete_details`: `null`
- `instructions`: `null`
- `user`: `null`
- `content_filters`: `null`

</details>

---

<details>
<summary><strong>🎯 Output (3 items)</strong></summary>

<details>
<summary><strong>🔍 Output 1: Web Search Call</strong></summary>

**Type:** `web_search_call`  
**Status:** `searching`  
**ID:** `ws_0be194b6f69aea1900695d806aa95c81949ad5969b2ee4921c`

<details>
<summary><strong>Action Details</strong></summary>

- **Query:** `"Python code to calculate factorial"`
- **Type:** `search`
- **Sources:** `null`

</details>

</details>

<details>
<summary><strong>💻 Output 2: Code Interpreter Call</strong></summary>

**Type:** `code_interpreter_call`  
**Status:** `completed`  
**ID:** `ci_0be194b6f69aea1900695d806cb3188194958eb81e364182fe`  
**Container ID:** `cntr_695d8067e1cc8190bfe86c02dcad6ca20cf9c5a42d82e058`

<details>
<summary><strong>Python Code</strong></summary>

```python
# Defining a function to calculate factorial using an iterative approach
def factorial(n):
    if n < 0:
        return "Factorial not defined for negative numbers"
    factorial_result = 1
    for i in range(1, n + 1):
        factorial_result *= i
    return factorial_result

# Example usage
number = 7
factorial_result = factorial(number)
factorial_result
```

</details>

<details>
<summary><strong>Execution Output</strong></summary>

- **Type:** `logs`
- **Output:** `5040`

</details>

</details>

<details>
<summary><strong>💬 Output 3: Assistant Message</strong></summary>

**Type:** `message`  
**Role:** `assistant`  
**Status:** `completed`  
**ID:** `msg_0be194b6f69aea1900695d807015e48194b346fbb2302b9740`

<details>
<summary><strong>Content</strong></summary>

**Type:** `output_text`  
**Text:** 
```
The factorial of 7 is calculated to be **5040** using the iterative approach. If you have any more questions or need further assistance, feel free to ask!
```

**Additional Fields:**
- **Annotations:** `[]` (empty)
- **Logprobs:** `[]` (empty)

</details>

</details>

</details>

---

<details>
<summary><strong>🔧 Configuration & Settings</strong></summary>

<details>
<summary><strong>Model Parameters</strong></summary>

| Parameter | Value |
|-----------|-------|
| **Parallel Tool Calls** | `true` |
| **Temperature** | `1.0` |
| **Tool Choice** | `required` |
| **Top P** | `1.0` |
| **Background** | `false` |
| **Top Logprobs** | `0` |
| **Truncation** | `disabled` |

</details>

<details>
<summary><strong>Text Format Settings</strong></summary>

- **Format Type:** `text`
- **Verbosity:** `medium`

</details>

<details>
<summary><strong>Null Configuration Fields</strong></summary>

- `conversation`: `null`
- `max_output_tokens`: `null`
- `max_tool_calls`: `null`
- `previous_response_id`: `null`
- `prompt`: `null`
- `prompt_cache_key`: `null`
- `prompt_cache_retention`: `null`
- `safety_identifier`: `null`

</details>

</details>

---

<details>
<summary><strong>🛠️ Tools Configuration</strong></summary>

<details>
<summary><strong>Tool 1: Code Interpreter</strong></summary>

**Type:** `code_interpreter`

<details>
<summary><strong>Container Settings</strong></summary>

- **Type:** `auto`
- **File IDs:** `null`
- **Memory Limit:** `null`

</details>

</details>

<details>
<summary><strong>Tool 2: Web Search</strong></summary>

**Type:** `web_search`

<details>
<summary><strong>Search Settings</strong></summary>

- **Filters:** `null`
- **Search Context Size:** `medium`

<details>
<summary><strong>User Location</strong></summary>

- **City:** `null`
- **Country:** `US`
- **Region:** `null`
- **Timezone:** `null`
- **Type:** `approximate`

</details>

</details>

</details>

</details>

---

<details>
<summary><strong>🧠 Reasoning Configuration</strong></summary>

All reasoning fields are set to `null`:
- **Effort:** `null`
- **Generate Summary:** `null` 
- **Summary:** `null`

**Service Tier:** `default`

</details>

---

<details>
<summary><strong>📊 Usage Statistics</strong></summary>

<details>
<summary><strong>Token Usage Summary</strong></summary>

| Metric | Count |
|--------|-------|
| **Input Tokens** | **7,154** |
| **Output Tokens** | **144** |
| **Total Tokens** | **7,298** |

</details>

<details>
<summary><strong>Detailed Token Breakdown</strong></summary>

<details>
<summary><strong>Input Token Details</strong></summary>

- **Total Input Tokens:** `7,154`
- **Cached Tokens:** `0`

</details>

<details>
<summary><strong>Output Token Details</strong></summary>

- **Total Output Tokens:** `144`
- **Reasoning Tokens:** `0`

</details>

</details>

</details>


### Raw Json Response
<details>

<summary><strong>📄 Raw JSON Data</strong></summary>

```json
{
  "id": "resp_0be194b6f69aea1900695d80678e8c8194ba09d9d89684aed1",
  "created_at": 1767735399.0,
  "error": null,
  "incomplete_details": null,
  "instructions": null,
  "metadata": {},
  "model": "gpt-4o-mini",
  "object": "response",
  "output": [
    {
      "id": "ws_0be194b6f69aea1900695d806aa95c81949ad5969b2ee4921c",
      "action": {
        "query": "Python code to calculate factorial",
        "type": "search",
        "sources": null
      },
      "status": "searching",
      "type": "web_search_call"
    },
    {
      "id": "ci_0be194b6f69aea1900695d806cb3188194958eb81e364182fe",
      "code": "# Defining a function to calculate factorial using an iterative approach\r\ndef factorial(n):\r\n    if n < 0:\r\n        return \"Factorial not defined for negative numbers\"\r\n    factorial_result = 1\r\n    for i in range(1, n + 1):\r\n        factorial_result *= i\r\n    return factorial_result\r\n\r\n# Example usage\r\nnumber = 7\r\nfactorial_result = factorial(number)\r\nfactorial_result",
      "container_id": "cntr_695d8067e1cc8190bfe86c02dcad6ca20cf9c5a42d82e058",
      "outputs": [
        {
          "logs": "5040",
          "type": "logs"
        }
      ],
      "status": "completed",
      "type": "code_interpreter_call"
    },
    {
      "id": "msg_0be194b6f69aea1900695d807015e48194b346fbb2302b9740",
      "content": [
        {
          "annotations": [],
          "text": "The factorial of 7 is calculated to be **5040** using the iterative approach. If you have any more questions or need further assistance, feel free to ask!",
          "type": "output_text",
          "logprobs": []
        }
      ],
      "role": "assistant",
      "status": "completed",
      "type": "message"
    }
  ],
  "parallel_tool_calls": true,
  "temperature": 1.0,
  "tool_choice": "required",
  "tools": [
    {
      "container": {
        "type": "auto",
        "file_ids": null,
        "memory_limit": null
      },
      "type": "code_interpreter"
    },
    {
      "type": "web_search",
      "filters": null,
      "search_context_size": "medium",
      "user_location": {
        "city": null,
        "country": "US",
        "region": null,
        "timezone": null,
        "type": "approximate"
      }
    }
  ],
  "top_p": 1.0,
  "background": false,
  "conversation": null,
  "max_output_tokens": null,
  "max_tool_calls": null,
  "previous_response_id": null,
  "prompt": null,
  "prompt_cache_key": null,
  "prompt_cache_retention": null,
  "reasoning": {
    "effort": null,
    "generate_summary": null,
    "summary": null
  },
  "safety_identifier": null,
  "service_tier": "default",
  "status": "completed",
  "text": {
    "format": {
      "type": "text"
    },
    "verbosity": "medium"
  },
  "top_logprobs": 0,
  "truncation": "disabled",
  "usage": {
    "input_tokens": 7154,
    "input_tokens_details": {
      "cached_tokens": 0
    },
    "output_tokens": 144,
    "output_tokens_details": {
      "reasoning_tokens": 0
    },
    "total_tokens": 7298
  },
  "user": null,
  "content_filters": null,
  "store": true
}
```

</details>
