# essay-feedback-assistant
AI-powered essay feedback assistant built with Flowise
## Flow Architecture

![Essay Feedback Assistant Flow](Essay%20Feedback%20Assistant.png)

The flow consists of four nodes:

1. **Chat Prompt Template** — Defines the AI's behavior:
   - System instructions for constructive essay feedback
   - Human message placeholder `{input}` for student essays

2. **OpenRouter** — LLM provider using `openrouter/owl-alpha` model
   - Temperature: 0.9
   - Credential: flowise test

3. **Buffer Memory** — Maintains conversation context across sessions

4. **Conversation Chain** — Orchestrates the chat experience by combining:
   - The formatted prompt
   - The language model
   - The memory buffer
