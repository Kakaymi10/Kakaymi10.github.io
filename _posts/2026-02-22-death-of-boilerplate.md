---
title: "The Death of Boilerplate: Why I Built Toolify"
description: "Why writing manual JSON schemas for AI agents is holding us back, and how Toolify fixes it."
date: 2026-02-22
tags: ["AI", "Agents", "Python", "Toolify", "OpenSource"]
cover_image: "https://images.unsplash.com/photo-1555949963-ff9fe0c870eb?auto=format&fit=crop&q=80&w=2000"
author: "Moussa Moustapha Moussa"
---

# The Death of Boilerplate: Why I Built Toolify

If you've built an AI agent recently, you know the pain.

You write a beautiful Python function. It’s clean, it’s type-hinted, it has a perfect docstring. Then, to make it usable by an LLM (like GPT-4 or Claude), you have to manually translate it into a verbose JSON schema.

```json
{
  "name": "get_weather",
  "description": "Get the current weather...",
  "parameters": {
    "type": "object",
    "properties": {
      "location": { "type": "string" },
      ...
    }
  }
}
```

It’s repetitive. It’s error-prone. And worst of all, it drifts out of sync with your code the moment you change a parameter name.

This is **boilerplate**, and it's slowing down the agent revolution.

## Enter Toolify

I built **Toolify** (`pip install toolify-ai`) to solve this problem once and for all.

Toolify is a lightweight Python library that automatically generates OpenAI-compatible tool schemas directly from your Python functions. No extra config files. No manual JSON editing. Just code.

### How It Works

You write Python. Toolify handles the rest.

```python
from toolify import toolify

@toolify
def search_database(query: str, limit: int = 10):
    """
    Search the vector database for relevant documents.
    """
    # Your logic here...
```

That’s it. Toolify inspects your type hints, parses your docstring, and generates the perfect JSON schema for your LLM.

## Why This Matters

We are entering the **Agent Age**. The most powerful AI systems won't just chat; they will *do*. They will call APIs, query databases, and execute code.

For this ecosystem to scale, we need standards. We need tools that are:

1.  **Type-Safe:** If your function expects an `int`, the schema should enforce it.
2.  **Self-Documenting:** Your docstrings should drive the model's understanding.
3.  **Developer-First:** You shouldn't have to leave your IDE or context-switch to write JSON.

Toolify is my contribution to this ecosystem. It’s designed to be the invisible glue between your code and your agent's brain.

## Get Started

It’s open source and ready to use.

```bash
pip install toolify-ai
```

Check out the code on [GitHub](https://github.com/Kakaymi10/toolify) and let me know what you think. Let’s stop writing boilerplate and start building agents that actually work.
