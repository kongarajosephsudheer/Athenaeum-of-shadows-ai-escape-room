# 🗝️ AI-Powered Escape Room (Version 1 & Version 2)

An interactive text-based escape room powered by Google's Gemini API (`google-genai`) and Gradio. The player wakes up inside a locked Victorian library and must examine objects, uncover hidden clues, and solve puzzles to unlock the exit door.

---

## 📖 Project Overview

This repository demonstrates the architectural evolution of an LLM-driven interactive game across two versions:

* **Version 1 — Interactive AI Escape Room (Naive Prompt-Only Baseline):** Uses a pure conversational loop where Gemini acts as the Game Master, maintaining room rules, object states, and narrative progression entirely within the system prompt and chat transcript.
* **Version 2 — Reliable AI Escape Room (State-Validated Engine):** *(In Progress / Planned Upgrade)* Decouples game rules and state tracking into a deterministic Python state machine with function-calling validation to prevent hallucinations, state drift, and adversarial prompt injections.

---

## 🏰 Room Scenario & Puzzle Design (Version 1)

The player is trapped inside a locked Victorian library containing five interactive objects:

1. **Bookshelf:** Holds four protruding books stamped with the digits `3, 8, 1, 4`.
2. **Oak Desk:** Features a locked center drawer requiring a 4-digit numeric code.
3. **Locked Drawer:** Opens with code `3814` to reveal an ornate brass key.
4. **Astronomer Painting:** An antique portrait pointing upward[cite: 13].
5. **Exit Door:** A heavy wooden door secured with a brass keyhole[cite: 13].

### Winning Walkthrough
1. `Examine the bookshelf` $\rightarrow$ Discover the four digits (`3814`)[cite: 13].
2. `Unlock the drawer with 3814` $\rightarrow$ Open the desk drawer to reveal the brass key[cite: 13].
3. `Take the brass key` $\rightarrow$ Collect the key[cite: 13].
4. `Unlock the exit door` $\rightarrow$ Use the brass key to escape the library[cite: 13].

---

## 🏗️ System Architecture (Version 1)

In Version 1, all game logic relies on in-context learning and prompt instructions[cite: 13]:

```text
+-------------------+       Natural Language        +-----------------------+
|   Player (Gradio) | ----------------------------> |  Conversation History |
+-------------------+                               +-----------------------+
         ^                                                      |
         |                                                      v
         |           Unvalidated Narrative          +-----------------------+
         +----------------------------------------- |  Gemini LLM (Prompt)  |
                                                    | (Rules + Story + Mem) |
                                                    +-----------------------+
