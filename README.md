# 🚀 Speedtest CLI (`st`)

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Python Version](https://img.shields.io/badge/python-2.7%20%7C%203.6%2B-brightgreen.svg)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/platform-linux%20%7C%20macOS%20%7C%20windows-lightgrey.svg)](#installation)

A modern, high-performance command-line interface for testing internet bandwidth using [Speedtest.net](https://www.speedtest.net/) servers. 

Featuring interactive progress bars, real-time transfer rates, ping radar animations, and a sleek summary results card directly in your terminal.

---

## ✨ Features

- **⚡ Fast & Lightweight**: Zero external Python dependencies—runs out-of-the-box on standard Python installations.
- **🎨 Modern CLI UI**: Interactive neon progress bars (`█`), live transfer speed updates in `Mbit/s`, and ping radar animations.
- **📊 Professional Summary Card**: Beautiful box-drawing summary displaying Ping, Download, Upload, Client ISP, Server Location, Distance, and Share URLs.
- **⌨️ Convenient Short Alias**: Convenient `st` command out-of-the-box, alongside standard `speedtest` and `speedtest-cli`.
- **🔒 Secure Connections**: Full support for HTTPS server communication (`--secure`).
- **🤖 Automation Ready**: Machine-readable JSON (`--json`), CSV (`--csv`), and simple text (`--simple`) output modes for scripts and CI/CD pipelines.

---

## 🖥️ Preview
<img width="770" height="306" alt="live_results" src="https://github.com/user-attachments/assets/b5af87f1-3734-43b2-8470-84c4f13ee896" />
<img width="795" height="303" alt="final_results" src="https://github.com/user-attachments/assets/6878d398-7d66-4d15-a37a-165ae575897b" /> 

---

## 📦 Installation

### Option 1: Install from Source (Recommended)

Clone the repository and install using `pip`:

```bash
git clone https://github.com/janiyaNIMA/speedtest-cli
cd speedtest-cli

# Install for user (modern Linux / PEP 668 managed environments)
pip install --user --break-system-packages .

# Or standard pip install
pip install --user .
```

### Option 2: System-Wide Symlink (Global Access)

To make `st` accessible to all users on Ubuntu / Linux:

```bash
sudo chmod +x speedtest.py
sudo ln -sf $(pwd)/speedtest.py /usr/local/bin/st
```

### Option 3: Shell Alias

Add an alias to your `~/.bashrc` or `~/.zshrc`:

```bash
echo "alias st='python3 $(pwd)/speedtest.py'" >> ~/.bashrc
source ~/.bashrc
```

---

## 🚀 Quick Start

Run a complete internet speed test using the short `st` command:

```bash
st
```

### Common Usage Examples

```bash
# Display results in simple text format
st --simple

# Generate a shareable result image URL from speedtest.net
st --share

# Use HTTPS connection for tests
st --secure

# Measure speed in Bytes instead of Bits
st --bytes

# Perform single-threaded test (simulates standard single file download)
st --single

# Export test results in JSON format
st --json

# Export test results in CSV format
st --csv
```

---

## 🎛️ Command-Line Options

| Flag | Short | Description |
| :--- | :--- | :--- |
| `--help` | `-h` | Show help message and exit |
| `--share` | | Generate and display a URL for the speedtest.net share results image |
| `--simple` | | Suppress UI animations, show basic text output |
| `--bytes` | | Display values in bytes (`MB/s`) instead of bits (`Mbit/s`) |
| `--single` | | Only use a single HTTP connection instead of multi-threading |
| `--secure` | | Use HTTPS instead of HTTP when connecting to speedtest.net servers |
| `--no-download` | | Skip the download test |
| `--no-upload` | | Skip the upload test |
| `--list` | | Display a list of speedtest.net servers sorted by distance |
| `--server SERVER` | | Specify a target server ID to test against (can be repeated) |
| `--exclude EXCLUDE` | | Exclude a server ID from selection |
| `--json` | | Output results in JSON format |
| `--csv` | | Output results in CSV format |
| `--version` | | Show version number and exit |

---

## 🔬 How It Works

1. **Config & Client Discovery**: Fetches client IP, ISP information, and server configuration from Speedtest.net API.
2. **Server Auto-Selection**: Downloads server list, calculates geographical distances, and pings nearby servers using low-latency HTTP GET requests to select the best server.
3. **Multi-Threaded Speed Test**: Spawns parallel worker threads (`HTTPDownloader` & `HTTPUploader`) to maximize socket throughput and measure true network capacity.
4. **Interactive UI**: Renders real-time byte transfers via terminal ANSI escape codes and presents a polished summary card.

---

## 📄 License

Distributed under the Apache License, Version 2.0. See [`LICENSE`](file:///home/janidu/workbench/speedtest-cli/LICENSE) for details.
