# Server Tool Call and Response Representation

This document outlines potential standardized representations for server tool calls and responses, drawing from analysis of current implementations across major AI platforms.

## Design Principles

Based on the [comparison analysis](comparison.md), the following design principles emerge:

- **Separation**: Tool calls and responses should be clearly separable for observability and debugging
- **Consistency**: All server tools should follow the same structural pattern
- **Extensibility**: Structure should accommodate different tool types and future additions
- **Clarity**: Clear distinction between tool invocation and tool results

## Proposed Representation

### Option 1: Extending Existing tool_call_part to Support Built-in Tools

This approach uses polymorphic tool calls with type discriminators within the existing `tool_call` and `tool_call_response` message parts:

#### Tool Call Request Part
```json
{
  "type": "tool_call",
  "id": "call_VSPygqKTWdrhaFErNvMV18Yl", 
  "name": "code_interpreter",
  "tool_call": {
    "type": "code_interpreter",
    "code": "import random\n\n# Generate a random number\nrandom_number = random.randint(1, 100)\n\n# Execute some operation with the random number (e.g., squaring it)\nresult = random_number ** 2\n\nrandom_number, result",
    "container_id": "cntr_690bdbfed8688190884efd4c7ae6435b0db1f006442e8941"
  }
}
```

#### Tool Call Response Part  
```json
{
  "type": "tool_call_response",
  "id": "call_VSPygqKTWdrhaFErNvMV18Yl",
  "response": {
    "type": "code_interpreter", 
    "outputs": [
      {
        "type": "logs",
        "logs": "(89, 7921)"
      }
    ]
  }
}
```

### Option 2: New Part for Server Tools (`server_tool_call`)

Following the pattern that achieves 100% separability:

#### Server Tool Call
```json
{
  "type": "server_tool_call",
  "id": "call_123",
  "name": "code_interpreter",
  "server_tool_call": {
    "type": "code_interpreter",
    "code": "print(10 + 20)",
    "container_id": "container_xyz"
  }
}
```

#### Server Tool Call Response
```json
{
  "type": "server_tool_call_response", 
  "id": "call_123",
  "server_tool_call_response": {
    "type": "code_interpreter",
    "outputs": [
      {
        "type": "logs",
        "logs": "(10, 20)"
      }
    ]
  }
}
```

### Option 3: Unified Tool Call Object

This approach combines tool calls and responses into a single object, similar to some existing platform implementations:

#### Unified Server Tool Object
```json
{
  "type": "server_tool",
  "id": "call_123",
  "name": "code_interpreter",
  "tool_call": {
    "type": "code_interpreter",
    "code": "import random\n\n# Generate a random number\nrandom_number = random.randint(1, 100)\n\n# Execute some operation with the random number (e.g., squaring it)\nresult = random_number ** 2\n\nrandom_number, result",
    "container_id": "cntr_690bdbfed8688190884efd4c7ae6435b0db1f006442e8941"
  },
  "tool_response": {
    "type": "code_interpreter",
    "outputs": [
      {
        "type": "logs",
        "logs": "(89, 7921)"
      }
    ]
  },
  "status": "completed"
}
```

**Alternative Unified Structure:**
```json
{
  "type": "server_tool_execution",
  "id": "call_123", 
  "name": "code_interpreter",
  "request": {
    "type": "code_interpreter",
    "code": "print('Hello, World!')",
    "container_id": "container_xyz"
  },
  "response": {
    "type": "code_interpreter",
    "outputs": [
      {
        "type": "logs", 
        "logs": "Hello, World!"
      }
    ]
  },
  "execution_metadata": {
    "status": "completed",
    "duration_ms": 250,
    "timestamp": "2026-01-12T10:30:45Z"
  }
}
```

## Schema Evolution: Current vs. Option 1

### Current ToolCallRequestPart Schema
```json
{
  "ToolCallRequestPart": {
    "additionalProperties": true,
    "description": "Represents a tool call requested by the model.",
    "properties": {
      "type": {
        "const": "tool_call",
        "description": "The type of the content captured in this part.",
        "title": "Type",
        "type": "string"
      },
      "id": {
        "anyOf": [
          { "type": "string" },
          { "type": "null" }
        ],
        "default": null,
        "description": "Unique identifier for the tool call.",
        "title": "Id"
      },
      "name": {
        "description": "Name of the tool.",
        "title": "Name",
        "type": "string"
      },
      "arguments": {
        "default": null,
        "description": "Arguments for the tool call.",
        "title": "Arguments"
      }
    },
    "required": ["type", "name"],
    "title": "ToolCallRequestPart",
    "type": "object"
  }
}
```

### Enhanced ToolCallRequestPart Schema (Option 1)
```json
{
  "ToolCallRequestPart": {
    "additionalProperties": true,
    "description": "Represents a tool call requested by the model.",
    "properties": {
      "type": {
        "const": "tool_call",
        "description": "The type of the content captured in this part.",
        "title": "Type",
        "type": "string"
      },
      "id": {
        "anyOf": [
          { "type": "string" },
          { "type": "null" }
        ],
        "default": null,
        "description": "Unique identifier for the tool call.",
        "title": "Id"
      },
      "name": {
        "description": "Name of the tool.",
        "title": "Name",
        "type": "string"
      },
      "tool_call": {
        "description": "Polymorphic tool call details with type discriminator.",
        "oneOf": [
          { "$ref": "#/$defs/FunctionToolCall" },
          { "$ref": "#/$defs/CodeInterpreterToolCall" }
        ],
        "title": "Tool Call"
      }
    },
    "required": ["type", "name", "tool_call"],
    "title": "ToolCallRequestPart",
    "type": "object"
  }
}
```

### Current ToolCallResponsePart Schema
```json
{
  "ToolCallResponsePart": {
    "additionalProperties": true,
    "description": "Represents a tool call result sent to the model or a built-in tool call outcome and details.",
    "properties": {
      "type": {
        "const": "tool_call_response",
        "description": "The type of the content captured in this part.",
        "title": "Type",
        "type": "string"
      },
      "id": {
        "anyOf": [
          { "type": "string" },
          { "type": "null" }
        ],
        "default": null,
        "description": "Unique tool call identifier.",
        "title": "Id"
      },
      "response": {
        "description": "Tool call response.",
        "title": "Response"
      }
    },
    "required": ["type", "response"],
    "title": "ToolCallResponsePart",
    "type": "object"
  }
}
```

### Enhanced ToolCallResponsePart Schema (Option 1)
```json
{
  "ToolCallResponsePart": {
    "additionalProperties": true,
    "description": "Represents a tool call result sent to the model or a built-in tool call outcome and details.",
    "properties": {
      "type": {
        "const": "tool_call_response",
        "description": "The type of the content captured in this part.",
        "title": "Type",
        "type": "string"
      },
      "id": {
        "anyOf": [
          { "type": "string" },
          { "type": "null" }
        ],
        "default": null,
        "description": "Unique tool call identifier.",
        "title": "Id"
      },
      "response": {
        "description": "Polymorphic tool call response with type discriminator.",
        "oneOf": [
          { "$ref": "#/$defs/FunctionToolCallResponse" },
          { "$ref": "#/$defs/CodeInterpreterToolCallResponse" }
        ],
        "title": "Response"
      }
    },
    "required": ["type", "response"],
    "title": "ToolCallResponsePart",
    "type": "object"
  }
}
```

### Key Changes
- **Request**: Replaced generic `arguments` field with structured `tool_call` field using polymorphic schema
- **Response**: Enhanced `response` field from untyped to polymorphic with type discriminator
- **Extensibility**: Added `oneOf` patterns to support multiple tool types (function, code_interpreter, etc.)
- **Type Safety**: Each tool type now has its own dedicated schema definition
- **Backward Compatibility**: Function tools continue to work through `FunctionToolCall` type

