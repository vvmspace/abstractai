# Abstract AI

## LLM APIs Abstraction concept

We should use abstraction layer for LLM APIs to be able to switch between different LLM providers easily.

`model` should be passed by parameter and based on `model` we should use different LLM providers following abstraction principles.

By default we use `gemini-2.5-flash` for free.

## LLM API Keys

API keys should be stored in environment variables, separated by commas, like:

```
LOCAL_LLM_API_KEY= # OpenAI compatibke
LOCAL_LLM_API_URL= # optional, if provided  
GEMINI_API_KEY=gemini_key1,gemini_key2,gemini_key3
OPENAI_API_KEY=openai_key
OPENROUTER_API_KEY=openrouter_key1,openrouter_key2
```

If there are more than 1 key for provider, we should use the random key from the list.

## Prompts templating

### Variables

%variable% %variable1|default%

## Methods

- .ask(prompt: string, model_and_fallbacks_by_commas?: string) `.ask('Hello')`, `.ask('Hello','local,gemma,openrouter:free')`
- .json(prompt: string, example_or_description: string | any, model_and_fallbacks_by_commas?: string): `.json('2+2=', { result: 4 })`, `.json('2+2=', 'result: number, example: { result: 4 }, 'gemma,gemini-2.5-flash')`, `.json('bla bla from 0 to 100', { rate: 100 }, 'local,gemma'))`

