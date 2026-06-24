# essay-feedback-assistant
AI-powered essay feedback assistant built with Flowise
## Flow Architecture

![Essay Feedback Assistant Flow](Essay%20Feedback%20Assistant.png)
Screenshot Description

The image shows a Flowise Chatflow titled "Essay Feedback Assistant" with four connected nodes on a dotted canvas:
| Node                     | Position  | Details                                                                                                                                                                                                                                        |
| ------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Chat Prompt Template** | Left      | Contains the system instructions for the essay feedback assistant. System Message begins: *"You are a supportive essay feedback assistant for students. For each essay: 1. LIST 3-5 specific things the..."* Human Message is set to `{input}` |
| **OpenRouter**           | Top-right | The LLM provider node connected to credential "flowise test". Model: `openrouter/owl-alpha`. Temperature: `0.9`                                                                                                                                |
| **Buffer Memory**        | Bottom    | Stores conversation history. Output connects to the Conversation Chain                                                                                                                                                                         |
| **Conversation Chain**   | Right     | The orchestrator node with inputs: Chat Model, Memory, Chat Prompt Template, Input Moderation, and Additional Parameters                                                                                                                       |


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

Connections:
ChatPromptTemplate output → ConversationChain (Chat Prompt Template input)
ChatOpenRouter output → ConversationChain (Chat Model input)
BufferMemory output → ConversationChain (Memory input)
