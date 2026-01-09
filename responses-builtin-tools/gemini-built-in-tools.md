# Google Gemini Server Tools

## Request
```python
from google import genai
from google.genai import types

client = genai.Client(api_key="...")

response = client.models.generate_content(
    model="gemini-2.5-flash",
    contents="Find syntactially correct code to calculate factorial in Python using web search and execute it using code interpreter.",
    config=types.GenerateContentConfig(
        tools=[
            types.Tool(code_execution=types.ToolCodeExecution),
            types.Tool(google_search=types.GoogleSearch()),
        ]
    ),
)

print(response.model_dump_json(indent=2))
```

## Response

**Response ID:** `rmldaeK0JsyhqtsPnsrP6A0`  
**Model Version:** `gemini-2.5-flash`  
**Date:** January 6, 2026

---

<details>
<summary><strong>📡 SDK HTTP Response</strong></summary>

<details>
<summary><strong>Headers</strong></summary>

| Header | Value |
|--------|-------|
| **Content-Type** | `application/json; charset=UTF-8` |
| **Vary** | `Origin, X-Origin, Referer` |
| **Content-Encoding** | `gzip` |
| **Date** | `Tue, 06 Jan 2026 19:59:42 GMT` |
| **Server** | `scaffolding on HTTPServer2` |
| **X-XSS-Protection** | `0` |
| **X-Frame-Options** | `SAMEORIGIN` |
| **X-Content-Type-Options** | `nosniff` |
| **Server-Timing** | `gfet4t7; dur=3848` |
| **Alt-Svc** | `h3=":443"; ma=2592000,h3-29=":443"; ma=2592000` |
| **Transfer-Encoding** | `chunked` |

</details>

**Body:** `null`

</details>

---

<details>
<summary><strong>🤖 Candidates</strong></summary>

<details>
<summary><strong>Content</strong></summary>

**Role:** `model`

<details>
<summary><strong>Parts (8 items)</strong></summary>

<details>
<summary><strong>🔍 Part 1: Search Query</strong></summary>

**Type:** Executable Code

```python
concise_search("python code factorial")
```

**Language:** `PYTHON`

</details>

<details>
<summary><strong>✅ Part 2: Search Execution Result</strong></summary>

**Type:** Code Execution Result

- **Outcome:** `OUTCOME_OK`
- **Output:** 
```
Looking up information on Google Search.
```

</details>

<details>
<summary><strong>💻 Part 3: Factorial Implementation</strong></summary>

**Type:** Executable Code

```python
import math

def calculate_factorial(n):
    if n < 0:
        return "Factorial is not defined for negative numbers."
    else:
        return math.factorial(n)

# Test the function
print(calculate_factorial(5))
print(calculate_factorial(0))
print(calculate_factorial(-3))
```

**Language:** `PYTHON`

</details>

<details>
<summary><strong>📊 Part 4: Code Execution Output</strong></summary>

**Type:** Code Execution Result

- **Outcome:** `OUTCOME_OK`
- **Output:**
```
120
1
Factorial is not defined for negative numbers.
```

</details>

<details>
<summary><strong>📝 Part 5: Explanation Text</strong></summary>

**Type:** Text

```
The syntactically correct Python code to calculate a factorial using the `math.factorial` function is:
```

</details>

<details>
<summary><strong>📋 Part 6: Code Block Display</strong></summary>

**Type:** Text (Formatted Code Block)

````python
import math

def calculate_factorial(n):
    if n < 0:
        return "Factorial is not defined for negative numbers."
    else:
        return math.factorial(n)

# Test the function
print(calculate_factorial(5))
print(calculate_factorial(0))
print(calculate_factorial(-3))
````

</details>

<details>
<summary><strong>📝 Part 7: Output Introduction</strong></summary>

**Type:** Text

```
And the execution output is:
```

</details>

<details>
<summary><strong>📤 Part 8: Final Output Display</strong></summary>

**Type:** Text (Formatted Output)

```
120
1
Factorial is not defined for negative numbers.
```

</details>

</details>

</details>

<details>
<summary><strong>🔗 Grounding Metadata</strong></summary>

<details>
<summary><strong>🔍 Web Search Queries</strong></summary>

- `python code factorial`

</details>

<details>
<summary><strong>🎨 Search Entry Point (HTML/CSS)</strong></summary>

<details>
<summary><strong>Rendered Content</strong></summary>

```html
<style>
.container {
  align-items: center;
  border-radius: 8px;
  display: flex;
  font-family: Google Sans, Roboto, sans-serif;
  font-size: 14px;
  line-height: 20px;
  padding: 8px 12px;
}
.chip {
  display: inline-block;
  border: solid 1px;
  border-radius: 16px;
  min-width: 14px;
  padding: 5px 16px;
  text-align: center;
  user-select: none;
  margin: 0 8px;
  -webkit-tap-highlight-color: transparent;
}
.carousel {
  overflow: auto;
  scrollbar-width: none;
  white-space: nowrap;
  margin-right: -12px;
}
.headline {
  display: flex;
  margin-right: 4px;
}
.gradient-container {
  position: relative;
}
.gradient {
  position: absolute;
  transform: translate(3px, -9px);
  height: 36px;
  width: 9px;
}
@media (prefers-color-scheme: light) {
  .container {
    background-color: #fafafa;
    box-shadow: 0 0 0 1px #0000000f;
  }
  .headline-label {
    color: #1f1f1f;
  }
  .chip {
    background-color: #ffffff;
    border-color: #d2d2d2;
    color: #5e5e5e;
    text-decoration: none;
  }
  .chip:hover {
    background-color: #f2f2f2;
  }
  .chip:focus {
    background-color: #f2f2f2;
  }
  .chip:active {
    background-color: #d8d8d8;
    border-color: #b6b6b6;
  }
  .logo-dark {
    display: none;
  }
  .gradient {
    background: linear-gradient(90deg, #fafafa 15%, #fafafa00 100%);
  }
}
@media (prefers-color-scheme: dark) {
  .container {
    background-color: #1f1f1f;
    box-shadow: 0 0 0 1px #ffffff26;
  }
  .headline-label {
    color: #fff;
  }
  .chip {
    background-color: #2c2c2c;
    border-color: #3c4043;
    color: #fff;
    text-decoration: none;
  }
  .chip:hover {
    background-color: #353536;
  }
  .chip:focus {
    background-color: #353536;
  }
  .chip:active {
    background-color: #464849;
    border-color: #53575b;
  }
  .logo-light {
    display: none;
  }
  .gradient {
    background: linear-gradient(90deg, #1f1f1f 15%, #1f1f1f00 100%);
  }
}
</style>
<div class="container">
  <div class="headline">
    <svg class="logo-light" width="18" height="18" viewBox="9 9 35 35" fill="none" xmlns="http://www.w3.org/2000/svg">
      <path fill-rule="evenodd" clip-rule="evenodd" d="M42.8622 27.0064C42.8622 25.7839 42.7525 24.6084 42.5487 23.4799H26.3109V30.1568H35.5897C35.1821 32.3041 33.9596 34.1222 32.1258 35.3448V39.6864H37.7213C40.9814 36.677 42.8622 32.2571 42.8622 27.0064V27.0064Z" fill="#4285F4"/>
      <path fill-rule="evenodd" clip-rule="evenodd" d="M26.3109 43.8555C30.9659 43.8555 34.8687 42.3195 37.7213 39.6863L32.1258 35.3447C30.5898 36.3792 28.6306 37.0061 26.3109 37.0061C21.8282 37.0061 18.0195 33.9811 16.6559 29.906H10.9194V34.3573C13.7563 39.9841 19.5712 43.8555 26.3109 43.8555V43.8555Z" fill="#34A853"/>
      <path fill-rule="evenodd" clip-rule="evenodd" d="M16.6559 29.8904C16.3111 28.8559 16.1074 27.7588 16.1074 26.6146C16.1074 25.4704 16.3111 24.3733 16.6559 23.3388V18.8875H10.9194C9.74388 21.2072 9.06992 23.8247 9.06992 26.6146C9.06992 29.4045 9.74388 32.022 10.9194 34.3417L15.3864 30.8621L16.6559 29.8904V29.8904Z" fill="#FBBC05"/>
      <path fill-rule="evenodd" clip-rule="evenodd" d="M26.3109 16.2386C28.85 16.2386 31.107 17.1164 32.9095 18.8091L37.8466 13.8719C34.853 11.082 30.9659 9.3736 26.3109 9.3736C19.5712 9.3736 13.7563 13.245 10.9194 18.8875L16.6559 23.3388C18.0195 19.2636 21.8282 16.2386 26.3109 16.2386V16.2386Z" fill="#EA4335"/>
    </svg>
    <svg class="logo-dark" width="18" height="18" viewBox="0 0 48 48" xmlns="http://www.w3.org/2000/svg">
      <circle cx="24" cy="23" fill="#FFF" r="22"/>
      <path d="M33.76 34.26c2.75-2.56 4.49-6.37 4.49-11.26 0-.89-.08-1.84-.29-3H24.01v5.99h8.03c-.4 2.02-1.5 3.56-3.07 4.56v.75l3.91 2.97h.88z" fill="#4285F4"/>
      <path d="M15.58 25.77A8.845 8.845 0 0 0 24 31.86c1.92 0 3.62-.46 4.97-1.31l4.79 3.71C31.14 36.7 27.65 38 24 38c-5.93 0-11.01-3.4-13.45-8.36l.17-1.01 4.06-2.85h.8z" fill="#34A853"/>
      <path d="M15.59 20.21a8.864 8.864 0 0 0 0 5.58l-5.03 3.86c-.98-2-1.53-4.25-1.53-6.64 0-2.39.55-4.64 1.53-6.64l1-.22 3.81 2.98.22 1.08z" fill="#FBBC05"/>
      <path d="M24 14.14c2.11 0 4.02.75 5.52 1.98l4.36-4.36C31.22 9.43 27.81 8 24 8c-5.93 0-11.01 3.4-13.45 8.36l5.03 3.85A8.86 8.86 0 0 1 24 14.14z" fill="#EA4335"/>
    </svg>
    <div class="gradient-container"><div class="gradient"></div></div>
  </div>
  <div class="carousel">
    <a class="chip" href="https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGIE0wsb3pfYUQC2EsTz6zI8w8j_eYjNgvELeGBjh6BIzeNAUNfm-T83jNDnkHXryMcdIuKVSMLAdqyQ7Y1Wbn9B7QvPUBfnmWrhXk1V7MZuNKxRRD7deQ0qEZ68rr_fRbajMXZPHgEhH6MQXolzHNkH9k9zfrpZpLjG3NI4eplsP-Ggk7ldqgePgUtLIXP18ZIr15O6ud_">python code factorial</a>
  </div>
</div>
```

</details>

</details>

**Null Fields:**
- `google_maps_widget_context_token`: `null`
- `grounding_chunks`: `null`
- `grounding_supports`: `null`
- `retrieval_metadata`: `null`
- `retrieval_queries`: `null`
- `sdk_blob`: `null`
- `source_flagging_uris`: `null`

</details>

**Additional Candidate Fields:**
- **Index:** `0`
- **Finish Reason:** `STOP`
- **Citation Metadata:** `null`
- **Finish Message:** `null`
- **Token Count:** `null`
- **Avg Logprobs:** `null`
- **Logprobs Result:** `null`
- **Safety Ratings:** `null`
- **URL Context Metadata:** `null`

</details>

---

<details>
<summary><strong>📊 Usage Metadata</strong></summary>

<details>
<summary><strong>Token Counts Summary</strong></summary>

| Metric | Count |
|--------|-------|
| **Cached Content Token Count** | 16 |
| **Candidates Token Count** | 212 |
| **Prompt Token Count** | 22 |
| **Thoughts Token Count** | 114 |
| **Tool Use Prompt Token Count** | 303 |
| **Total Token Count** | **651** |

</details>

<details>
<summary><strong>Detailed Token Breakdowns</strong></summary>

<details>
<summary><strong>Cache Token Details</strong></summary>

- **Modality:** TEXT
- **Token Count:** 16

</details>

<details>
<summary><strong>Prompt Token Details</strong></summary>

- **Modality:** TEXT  
- **Token Count:** 22

</details>

<details>
<summary><strong>Tool Use Prompt Token Details</strong></summary>

- **Modality:** TEXT
- **Token Count:** 303

</details>

</details>

**Null Fields:**
- `candidates_tokens_details`: `null`
- `traffic_type`: `null`

</details>

---

<details>
<summary><strong>🗂️ Additional Response Fields</strong></summary>

- **Create Time:** `null`
- **Prompt Feedback:** `null`
- **Automatic Function Calling History:** `[]` (empty array)
- **Parsed:** `null`

</details>

### Raw Json Response
<details>

<summary><strong>📄 Raw JSON Data</strong></summary>

```json
{
  "sdk_http_response": {
    "headers": {
      "content-type": "application/json; charset=UTF-8",
      "vary": "Origin, X-Origin, Referer",
      "content-encoding": "gzip",
      "date": "Tue, 06 Jan 2026 19:59:42 GMT",
      "server": "scaffolding on HTTPServer2",
      "x-xss-protection": "0",
      "x-frame-options": "SAMEORIGIN",
      "x-content-type-options": "nosniff",
      "server-timing": "gfet4t7; dur=3848",
      "alt-svc": "h3=\":443\"; ma=2592000,h3-29=\":443\"; ma=2592000",
      "transfer-encoding": "chunked"
    },
    "body": null
  },
  "candidates": [
    {
      "content": {
        "parts": [
          {
            "media_resolution": null,
            "code_execution_result": null,
            "executable_code": {
              "code": "concise_search(\"python code factorial\")\n",
              "language": "PYTHON"
            },
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": null,
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": {
              "outcome": "OUTCOME_OK",
              "output": "Looking up information on Google Search.\n"
            },
            "executable_code": null,
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": null,
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": null,
            "executable_code": {
              "code": "import math\n\ndef calculate_factorial(n):\n    if n < 0:\n        return \"Factorial is not defined for negative numbers.\"\n    else:\n        return math.factorial(n)\n\n# Test the function\nprint(calculate_factorial(5))\nprint(calculate_factorial(0))\nprint(calculate_factorial(-3))\n",
              "language": "PYTHON"
            },
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": null,
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": {
              "outcome": "OUTCOME_OK",
              "output": "120\n1\nFactorial is not defined for negative numbers.\n"
            },
            "executable_code": null,
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": null,
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": null,
            "executable_code": null,
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": "The syntactically correct Python code to calculate a factorial using the `math.factorial` function is:\n\n",
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": null,
            "executable_code": null,
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": "```python\nimport math\n\ndef calculate_factorial(n):\n    if n < 0:\n        return \"Factorial is not defined for negative numbers.\"\n    else:\n        return math.factorial(n)\n\n# Test the function\nprint(calculate_factorial(5))\nprint(calculate_factorial(0))\nprint(calculate_factorial(-3))\n```",
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": null,
            "executable_code": null,
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": "\n\nAnd the execution output is:\n\n",
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          },
          {
            "media_resolution": null,
            "code_execution_result": null,
            "executable_code": null,
            "file_data": null,
            "function_call": null,
            "function_response": null,
            "inline_data": null,
            "text": "```\n120\n1\nFactorial is not defined for negative numbers.\n```",        
            "thought": null,
            "thought_signature": null,
            "video_metadata": null
          }
        ],
        "role": "model"
      },
      "citation_metadata": null,
      "finish_message": null,
      "token_count": null,
      "finish_reason": "STOP",
      "avg_logprobs": null,
      "grounding_metadata": {
        "google_maps_widget_context_token": null,
        "grounding_chunks": null,
        "grounding_supports": null,
        "retrieval_metadata": null,
        "retrieval_queries": null,
        "search_entry_point": {
          "rendered_content": "<style>\n.container {\n  align-items: center;\n  border-radius: 8px;\n  display: flex;\n  font-family: Google Sans, Roboto, sans-serif;\n  font-size: 14px;\n  line-height: 20px;\n  padding: 8px 12px;\n}\n.chip {\n  display: inline-block;\n  border: solid 1px;\n  border-radius: 16px;\n  min-width: 14px;\n  padding: 5px 16px;\n  text-align: center;\n  user-select: none;\n  margin: 0 8px;\n  -webkit-tap-highlight-color: transparent;\n}\n.carousel {\n  overflow: auto;\n  scrollbar-width: none;\n  white-space: nowrap;\n  margin-right: -12px;\n}\n.headline {\n  display: flex;\n  margin-right: 4px;\n}\n.gradient-container {\n  position: relative;\n}\n.gradient {\n  position: absolute;\n  transform: translate(3px, -9px);\n  height: 36px;\n  width: 9px;\n}\n@media (prefers-color-scheme: light) {\n  .container {\n    background-color: #fafafa;\n    box-shadow: 0 0 0 1px #0000000f;\n  }\n  .headline-label {\n    color: #1f1f1f;\n  }\n  .chip {\n    background-color: #ffffff;\n    border-color: #d2d2d2;\n    color: #5e5e5e;\n    text-decoration: none;\n  }\n  .chip:hover {\n    background-color: #f2f2f2;\n  }\n  .chip:focus {\n    background-color: #f2f2f2;\n  }\n  .chip:active {\n    background-color: #d8d8d8;\n    border-color: #b6b6b6;\n  }\n  .logo-dark {\n    display: none;\n  }\n  .gradient {\n    background: linear-gradient(90deg, #fafafa 15%, #fafafa00 100%);\n  }\n}\n@media (prefers-color-scheme: dark) {\n  .container {\n    background-color: #1f1f1f;\n    box-shadow: 0 0 0 1px #ffffff26;\n  }\n  .headline-label {\n    color: #fff;\n  }\n  .chip {\n    background-color: #2c2c2c;\n    border-color: #3c4043;\n    color: #fff;\n    text-decoration: none;\n  }\n  .chip:hover {\n    background-color: #353536;\n  }\n  .chip:focus {\n    background-color: #353536;\n  }\n  .chip:active {\n    background-color: #464849;\n    border-color: #53575b;\n  }\n  .logo-light {\n    display: none;\n  }\n  .gradient {\n    background: linear-gradient(90deg, #1f1f1f 15%, #1f1f1f00 100%);\n  }\n}\n</style>\n<div class=\"container\">\n  <div class=\"headline\">\n    <svg class=\"logo-light\" width=\"18\" height=\"18\" viewBox=\"9 9 35 35\" fill=\"none\" xmlns=\"http://www.w3.org/2000/svg\">\n      <path fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M42.8622 27.0064C42.8622 25.7839 42.7525 24.6084 42.5487 23.4799H26.3109V30.1568H35.5897C35.1821 32.3041 33.9596 34.1222 32.1258 35.3448V39.6864H37.7213C40.9814 36.677 42.8622 32.2571 42.8622 27.0064V27.0064Z\" fill=\"#4285F4\"/>\n      <path fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M26.3109 43.8555C30.9659 43.8555 34.8687 42.3195 37.7213 39.6863L32.1258 35.3447C30.5898 36.3792 28.6306 37.0061 26.3109 37.0061C21.8282 37.0061 18.0195 33.9811 16.6559 29.906H10.9194V34.3573C13.7563 39.9841 19.5712 43.8555 26.3109 43.8555V43.8555Z\" fill=\"#34A853\"/>\n      <path fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M16.6559 29.8904C16.3111 28.8559 16.1074 27.7588 16.1074 26.6146C16.1074 25.4704 16.3111 24.3733 16.6559 23.3388V18.8875H10.9194C9.74388 21.2072 9.06992 23.8247 9.06992 26.6146C9.06992 29.4045 9.74388 32.022 10.9194 34.3417L15.3864 30.8621L16.6559 29.8904V29.8904Z\" fill=\"#FBBC05\"/>\n      <path fill-rule=\"evenodd\" clip-rule=\"evenodd\" d=\"M26.3109 16.2386C28.85 16.2386 31.107 17.1164 32.9095 18.8091L37.8466 13.8719C34.853 11.082 30.9659 9.3736 26.3109 9.3736C19.5712 9.3736 13.7563 13.245 10.9194 18.8875L16.6559 23.3388C18.0195 19.2636 21.8282 16.2386 26.3109 16.2386V16.2386Z\" fill=\"#EA4335\"/>\n    </svg>\n    <svg class=\"logo-dark\" width=\"18\" height=\"18\" viewBox=\"0 0 48 48\" xmlns=\"http://www.w3.org/2000/svg\">\n      <circle cx=\"24\" cy=\"23\" fill=\"#FFF\" r=\"22\"/>\n      <path d=\"M33.76 34.26c2.75-2.56 4.49-6.37 4.49-11.26 0-.89-.08-1.84-.29-3H24.01v5.99h8.03c-.4 2.02-1.5 3.56-3.07 4.56v.75l3.91 2.97h.88z\" fill=\"#4285F4\"/>\n      <path d=\"M15.58 25.77A8.845 8.845 0 0 0 24 31.86c1.92 0 3.62-.46 4.97-1.31l4.79 3.71C31.14 36.7 27.65 38 24 38c-5.93 0-11.01-3.4-13.45-8.36l.17-1.01 4.06-2.85h.8z\" fill=\"#34A853\"/>\n      <path d=\"M15.59 20.21a8.864 8.864 0 0 0 0 5.58l-5.03 3.86c-.98-2-1.53-4.25-1.53-6.64 0-2.39.55-4.64 1.53-6.64l1-.22 3.81 2.98.22 1.08z\" fill=\"#FBBC05\"/>\n      <path d=\"M24 14.14c2.11 0 4.02.75 5.52 1.98l4.36-4.36C31.22 9.43 27.81 8 24 8c-5.93 0-11.01 3.4-13.45 8.36l5.03 3.85A8.86 8.86 0 0 1 24 14.14z\" fill=\"#EA4335\"/>\n    </svg>\n    <div class=\"gradient-container\"><div class=\"gradient\"></div></div>\n  </div>\n  <div class=\"carousel\">\n    <a class=\"chip\" href=\"https://vertexaisearch.cloud.google.com/grounding-api-redirect/AUZIYQGIE0wsb3pfYUQC2EsTz6zI8w8j_eYjNgvELeGBjh6BIzeNAUNfm-T83jNDnkHXryMcdIuKVSMLAdqyQ7Y1Wbn9B7QvPUBfnmWrhXk1V7MZuNKxRRD7deQ0qEZ68rr_fRbajMXZPHgEhH6MQXolzHNkH9k9zfrpZpLjG3NI4eplsP-Ggk7ldqgePgUtLIXP18ZIr15O6ud_\">python code factorial</a>\n  </div>\n</div>\n",
          "sdk_blob": null
        },
        "source_flagging_uris": null,
        "web_search_queries": [
          "python code factorial"
        ]
      },
      "index": 0,
      "logprobs_result": null,
      "safety_ratings": null,
      "url_context_metadata": null
    }
  ],
  "create_time": null,
  "model_version": "gemini-2.5-flash",
  "prompt_feedback": null,
  "response_id": "rmldaeK0JsyhqtsPnsrP6A0",
  "usage_metadata": {
    "cache_tokens_details": [
      {
        "modality": "TEXT",
        "token_count": 16
      }
    ],
    "cached_content_token_count": 16,
    "candidates_token_count": 212,
    "candidates_tokens_details": null,
    "prompt_token_count": 22,
    "prompt_tokens_details": [
      {
        "modality": "TEXT",
        "token_count": 22
      }
    ],
    "thoughts_token_count": 114,
    "tool_use_prompt_token_count": 303,
    "tool_use_prompt_tokens_details": [
      {
        "modality": "TEXT",
        "token_count": 303
      }
    ],
    "total_token_count": 651,
    "traffic_type": null
  },
  "automatic_function_calling_history": [],
  "parsed": null
}
```

</details>
