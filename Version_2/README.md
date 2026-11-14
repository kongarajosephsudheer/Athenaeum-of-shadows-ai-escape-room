# Version 2 — Athenaeum of Shadows: Reliable AI Escape Room

## 1. Project Overview
Version 2 is a deterministic, state-validated AI escape room game set inside the Athenaeum of Shadows, a mysterious Victorian library.
Unlike Version 1, which relied solely on LLM prompts, Version 2 separates natural-language intent classification (via Google Gemini function calling) from Python rule enforcement and structured state tracking to guarantee consistent, cheat-proof gameplay.

## 2. Technologies Used
- Python
- Google Gemini API (`google-genai` with Tool Calling)
- Gradio (with `gr.State` per-session isolation)
- Google Colab

## 3. Game Story
The player awakens trapped inside the Athenaeum of Shadows, a locked Victorian library.
To escape, the player must uncover three sequential clues hidden across the room's objects, determine the four-digit combination (`3814`) for the locked desk drawer, retrieve the ornate brass key, and unlock the heavy oak exit door.

## 4. Main Features
- Deterministic Python state engine tracking clues, locks, inventory, and escape status.
- Gemini function calling (`examine`, `unlock_drawer`, `take_item`, `unlock_door`) for structured action classification.
- Per-session state isolation (`gr.State`) so multiple players have independent game progress.
- Live HTML room dashboard displaying real-time clue progress (`0/3` to `3/3`), drawer lock status, inventory contents, and exit status.
- Sequential three-clue puzzle progression:
  - Desk note (Clue 1)
  - Astronomer painting directions (Clue 2)
  - Bookshelf numbered volumes (Clue 3)
- Strict regex passcode validation (`3814`) and inventory-enforced door unlocking.
- Adversarial defense against prompt injection, administrator impersonation, false state claims, and secret-code leakage.
- One-click game reset functionality.

## 5. How It Works
1. The player enters a natural-language action or selects a preset command.
2. Google Gemini analyzes the input using defined tool declarations (`temperature=0.1`) and selects at most one valid game action (or rejects rule-bypass attempts without invoking tools).
3. The Python game engine validates the action against the player's current `gr.State` dictionary (checking clue order, lock flags, and inventory items).
4. Python updates the game state and renders the updated HTML room dashboard alongside the Game Master's response.
5. The player progresses step-by-step until unlocking the exit door to achieve `ESCAPED!` status.

## 6. Key Improvements Over Version 1
Version 1 relied purely on LLM instructions, making it susceptible to forgotten inventory states, invalid action acceptance, and prompt-injection exploits.
Version 2 stores all puzzle solutions and rules strictly in Python logic outside the LLM prompt, ensuring 100% deterministic rule enforcement and reliable state consistency across every turn.

## 7. Project File
- `app_v2.py` (or `App_version_2.ipynb`) — Python application and notebook for Version 2.

## 8. Security
The Gemini API key must be stored securely using environment variables or Google Colab Secrets (`GEMINI_API_KEY`). Never hardcode or upload API keys or private credentials to GitHub.

---
Project: Athenaeum of Shadows — AI Escape Room  
Version: 2  
Author: Joseph Sudheer Kongara
