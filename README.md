# Browser AI Coder

> An in-browser coding environment where an AI Agent writes and executes Python for you. powered by WebAssembly, WebLLM, and Pyodide.

[Demo](https://kazum.github.io/browser-ai-coder/) | [Source](https://github.com/kazum/browser-ai-coder)

This project is a fork of [wasi-fs-access](https://github.com/GoogleChromeLabs/wasi-fs-access) by Google Chrome Labs. It extends the original WASI shell with an embedded Large Language Model and Python runtime, creating a fully local, privacy-centric AI coding assistant.

## Features

-   **AI Agent (`coder`)**: Integrated Qwen2.5-Coder model (via WebLLM) running entirely in your browser (WebGPU required).
-   **Python Runtime**: Execute Python 3.11 scripts directly in the shell (via Pyodide) with full access to mounted files.
-   **Local Filesystem Access**: Mount your local directories to the browser environment safely using the [File System Access API](https://wicg.github.io/file-system-access/).
-   **Zero Server Dependency**: No data is sent to the cloud. Your code and prompts stay on your device.

## Usage

1.  Open the [Demo](https://kazum.github.io/browser-ai-coder/).
2.  Mount a local directory:
    ```bash
    $ mount /work
    ```
    (Select a folder on your computer when prompted)
3.  Start the AI coder:
    ```bash
    $ coder
    ```
4.  Ask the AI to write code:
    ```
    (coder) > Create a python script to calculate Fibonacci numbers and save it to /work/fib.py
    ```
5.  Run the code:
    ```bash
    $ python /work/fib.py
    ```

## Browser Support

Requires a modern browser with support for:
-   WebAssembly (WASI)
-   File System Access API (Chrome, Edge, Opera)
-   WebGPU (for AI features)
-   SharedArrayBuffer (for Python/AI performance)

## Development

```bash
# Install dependencies
npm install

# Build the project
npm run build

# Run a local server (SharedArrayBuffer headers required)
# Recommended to use a server that supports COOP/COEP, or use the included coi-serviceworker hack.
npx serve .
```

## Credits & License

Forked from [GoogleChromeLabs/wasi-fs-access](https://github.com/GoogleChromeLabs/wasi-fs-access).
Original code is Apache-2.0 Licensed.
Modifications for AI/Python integration are also under Apache-2.0.

-   **Shell & WASI integration**: [GoogleChromeLabs/wasi-fs-access](https://github.com/GoogleChromeLabs/wasi-fs-access)
-   **LLM Runtime**: [WebLLM](https://github.com/mlc-ai/web-llm) by MLC AI
-   **Python Runtime**: [Pyodide](https://github.com/pyodide/pyodide)
