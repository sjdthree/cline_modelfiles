# DeepCoder: 14B Model Documentation

## Overview

DeepCoder is a state-of-the-art 14-billion parameter model designed for advanced code generation and understanding. It is optimized for integration with platforms like Ollama and Hugging Face, providing developers with powerful tools for building intelligent applications.

### Key Features:
- **14B Parameters**: High capacity for complex code generation tasks.
- **Optimized for Context**: Supports extended context windows for better understanding of large codebases.
- **Seamless Integration**: Works with Ollama and Hugging Face for flexible deployment options.

For more details, visit:
- [Ollama DeepCoder Library](https://ollama.com/library/deepcoder:14b)
- [Hugging Face DeepCoder Model](https://huggingface.co/agentica-org/DeepCoder-14B-Preview)

---

## Deployment Instructions

### Adjusting Context Window for Ollama

**REALLY IMPORTANT FACT:** If you plan to run Ollama with code generation, follow these steps to move the default context window from 2048 to 8192. By default, Ollama uses a context window size of 2048 tokens.

This can be overridden with the `OLLAMA_CONTEXT_LENGTH` environment variable. For example, to set the default context window to 8K, use:

```bash
OLLAMA_CONTEXT_LENGTH=8192 ollama serve
```

To change this when using `ollama run`, use the `/set` parameter:

```bash
/set parameter num_ctx 4096
```

When using the API, specify the `num_ctx` parameter:

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",
  "prompt": "Why is the sky blue?",
  "options": {
    "num_ctx": 4096
  }
}'
```
### Pull the deepcoder model that fits your machine

14b = 9GB file size
```bash
ollama run deepcoder
```
1.5b = 1.1GB file size
```bash
ollama run deepcoder:1.5b
```
### Configure in RooCode or Cline with 
localhost:11434 
and select the deepcoder model

---

## Additional Resources

For further information and updates, refer to the following:
- [Ollama DeepCoder Library](https://ollama.com/library/deepcoder:14b)
- [Hugging Face DeepCoder Model](https://huggingface.co/agentica-org/DeepCoder-14B-Preview)
