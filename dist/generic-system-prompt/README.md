# Generic system-prompt install

For any LLM that takes a system prompt — GPT-4/5, Gemini, Llama, Mistral, local models via Ollama / LM Studio / vLLM, or any agent framework that exposes a system-prompt field.

## Install

Paste the contents of `system-prompt.md` from this folder into:

- ChatGPT custom GPT instructions
- Claude.ai project custom instructions
- OpenAI API `system` role message
- Anthropic API `system` parameter
- Gemini API `systemInstruction`
- Ollama Modelfile `SYSTEM` directive
- LangChain `SystemMessage`
- AutoGen, CrewAI, or any agent framework's system prompt field

## Verify

After the model finishes a task, type "did you do your best?" The model should run the audit protocol.

## Caveat

Adherence to long system prompts varies by model. In rough order of reliability:

1. Claude 3.5 Sonnet and above (highest adherence)
2. GPT-4o / GPT-5
3. Gemini 1.5 Pro / 2.0
4. Llama 3.1 70B+
5. Smaller local models (often need the trigger phrase made more explicit)
