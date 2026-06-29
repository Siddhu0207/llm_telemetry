# LLM Telemetry Dashboard

A real-time, terminal-based telemetry interface for tracking Large Generation Model (LLM) inference metrics, token attention weights, and runtime hardware events. Built with C++ using **FTXUI** for the dashboard layout and integrated with **llama.cpp** for native hardware inference tracing.

## Features

* **Hardware Layer Wiretap:** Real-time tracking of token pass sequences directly from `ggml` layers with Apple Silicon (`METAL`) optimization.
* **Attention Matrix Visualizer:** A dynamically scaling token-to-token attention grid with strict column constraints and alignment.
* **Runtime Metrics Inspector:** Live rendering of tensor shapes, data types (`float32`), sparsity rates, and system latency deltas.
* **Numerical Anomaly Ledger:** Streaming notification alert engine capturing memory blocks, GPU VRAM fallbacks, and mathematical outlier spikes (e.g., activations exceeding $> 6.0$).

## Tech Stack
* **Language:** C++17 / C++20
* **Build System:** CMake
* **TUI Framework:** FTXUI (Functional Terminal User Interface)
* **Inference Backend:** llama.cpp

## Getting Started

### Prerequisites
Ensure you have CMake and a C++ compiler installed on your system.

### Build Instructions
From the root directory of the project, run:
```bash
cmake -B build
cmake --build build
# LLM Telemetry Dashboard

A real-time, terminal-based telemetry interface for tracking LLM inference metrics.

## 📥 Model Download
To run this project locally, download the model weights file and place it inside your local `/models/` directory:
* 📦 **[Download tiny-model.gguf (468 MB)](sha256:74a4da8c9fdbcd15bd1f6d01d621410d31c6fc00986f5eb687824e7b93d7a9db)**
