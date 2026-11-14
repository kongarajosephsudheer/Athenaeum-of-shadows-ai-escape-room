# Version 1 — Athenaeum of Shadows: AI Escape Room

## 1. Project Overview

Version 1 is an AI-powered escape room game set inside a mysterious Victorian library.

The game uses **Google Gemini as the AI Game Master**. Players interact with the game using natural language, and Gemini responds with clues, descriptions, and guidance.

## 2. Technologies Used

- Python
- Google Gemini API
- Gradio
- Google Colab

## 3. Game Story

The player is trapped inside the Athenaeum of Shadows, a mysterious Victorian library.

The objective is to solve three clues, unlock a drawer, collect the brass key, and escape through the exit door.

## 4. Main Features

- Natural language interaction with the AI Game Master.
- AI-generated descriptions and responses.
- Three interactive clues:
  - Desk
  - Astronomer painting
  - Bookshelf
- Drawer combination puzzle.
- Brass key collection.
- Final exit door challenge.
- Conversation history to maintain the interaction context.

## 5. How It Works

1. The player enters an action or question.
2. The message is sent to Google Gemini.
3. Gemini interprets the player's message using its system instructions and conversation history.
4. The AI generates a response based on the game scenario.
5. The player continues exploring until reaching the escape challenge.

## 6. Important Limitation

Version 1 relies mainly on LLM instructions and conversation history. It does not use deterministic Python validation for every game action.

Therefore, the AI may occasionally accept invalid actions or provide inconsistent game progress.

These limitations motivated the development of Version 2.

## 7. Project File

- `app_v1.py` — Python application for Version 1.

## 8. Security

The Gemini API key should be stored securely using environment variables or Colab Secrets. Never upload API keys or other private credentials to GitHub.

---

Project: Athenaeum of Shadows — AI Escape Room  
Version: 1.0  
Author: Joseph Sudheer Kongara
