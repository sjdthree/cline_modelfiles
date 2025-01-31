# DeepSeek-R1 Model Integration with Cline via Ollama

This guide provides instructions on integrating the DeepSeek-R1 model with the Cline AI coding assistant, enabling local AI-driven coding assistance without relying on external APIs.

## Prerequisites

- **Software:**
  - [Visual Studio Code (VSCode)](https://code.visualstudio.com/)
  - [Ollama](https://ollama.com/)

## Hardware used in this setup

- **Operating System:** Windows 11
- **Memory:** 32 GB RAM (lower amounts may work but could result in slower performance)
- **GPU:** NVIDIA RTX 3080 with 10 GB VRAM (lower-spec GPUs may work but with reduced performance)

## Steps to Set Up

1. **Install Visual Studio Code (VSCode):**
   - Download and install VSCode from the [official website](https://code.visualstudio.com/).

2. **Install Ollama:**
   - Ollama is an engine that facilitates running large language models (LLMs) locally.
   - Download and install Ollama from the [official website](https://ollama.com/).

3. **Download the Model:**
   - Obtain the quantized GGUF model file suitable for your hardware. For this guide, we'll use`DeepSeek-R1-Distill-Qwen-14B-Q4_K_M.gguf`. [link](hf.co/roleplaiapp/DeepSeek-R1-Distill-Qwen-14B-Q4_K_M-GGUF)

   - Alternatively obtain model via Ollama with:
   ```bash
   ollama pull hf.co/roleplaiapp/DeepSeek-R1-Distill-Qwen-14B-Q4_K_M-GGUF
   ```

   - Ensure the model file is placed in a directory accessible to Ollama.

4. **Register the Model with Ollama:**
   - In the same directory as your GGUF model file, download the model definition file named [`DeepSeek-R1-Distill-Qwen-14B-Q4_K_M.model`](./Deepseek-r1-Distill-Qwen-14B-Q4_K_M.model)



   - Register the model with Ollama by running the following command in your terminal:

     ```bash
     ollama create DeepSeek-R1-14B-Q4_K_M -f DeepSeek-R1-Distill-Qwen-14B-Q4_K_M.model
     ```

   - Start the Ollama server:

     ```bash
     ollama serve
     ```

5. **Configure Cline:**
   - Install the Cline extension in VSCode.
   - Configure Cline to use the locally hosted DeepSeek-R1 model through Ollama.

## Performance Tuning

- **GPU Layers (`-ngl`):** Adjust the number of layers offloaded to the GPU based on your VRAM capacity. For an RTX 3080 with 10 GB VRAM, setting `-ngl 28` is recommended.
- **Batch Size (`-b`):** The default is 2048. Depending on your system's performance, you can adjust this to 4096 or 1024.
- **Parallel Processing (`--parallel`):** If not processing multiple requests simultaneously, set this to 1 or omit it.

Example Windows command to start the model with performance tuning:

```bash
llama-server.exe -m ../LLM-models/DeepSeek-R1-Distill-Qwen-14B-Q6_K.gguf -ngl 28 -b 2048 --temp 0.6