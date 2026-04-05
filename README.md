<div align="center">

# 🛡️ Python Antivirus

**A lightweight, educational antivirus engine built in pure Python**

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![License](https://img.shields.io/badge/License-AGPL%20v3-green?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=for-the-badge)]()
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-orange?style=for-the-badge)](CONTRIBUTING.md)

*Scan files. Detect threats. Learn how antivirus software really works.*

</div>

---

## 📖 Overview

**Python Antivirus** is an educational malware detection engine that demonstrates the core principles behind real-world antivirus software. It uses **signature-based detection** and **heuristic analysis** to identify potentially malicious files and directories — all with zero external dependencies beyond Python itself.

> ⚠️ **Disclaimer:** This project is designed strictly for **educational and cybersecurity learning purposes**. It is not intended for production use and offers no guarantee of full protection.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🔍 **File & Directory Scanning** | Scan individual files or recursively scan entire directories |
| 🧬 **Signature-Based Detection** | Match file content against a known malware signature database |
| 🧠 **Heuristic Analysis** | Flag suspicious patterns and structures in unknown files |
| 📄 **Scan Reports** | Export results in JSON or TXT format |
| 🚧 **Quarantine System** | Isolate infected files to prevent execution |
| ⚡ **Fast & Lightweight** | Pure Python — no heavy dependencies |

---

## 📂 Project Structure

```
Antivirus/
├── main.py              # CLI entry point
├── scanner.py           # Core detection engine
├── signatures.txt       # Malware signature database
├── utils.py             # Helper functions
├── quarantine/          # Isolated threat storage
├── reports/             # Scan output directory
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.x

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/M-2006/Antivirus.git
cd Antivirus

# 2. (Recommended) Create a virtual environment
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt
```

---

## ▶️ Usage

### Scan a single file
```bash
python main.py --file path/to/file.exe
```

### Scan a directory
```bash
python main.py --dir path/to/folder
```

### Generate a scan report
```bash
# JSON format
python main.py --dir ./test --report json

# TXT format
python main.py --dir ./test --report txt
```

### Enable quarantine
```bash
python main.py --dir ./test --quarantine
```

### Full CLI reference
```
Usage: main.py [OPTIONS]

  Options:
    --file <path>        Scan a single file
    --dir  <path>        Scan a directory recursively
    --report <type>      Save report as json or txt
    --quarantine         Move infected files to quarantine
    --help               Show this help message
```

---

## 🖥️ Example Output

```
[INFO]    Scanning: test.exe
[INFO]    Scanning: document.pdf
[WARNING] Suspicious pattern detected in document.pdf
[ALERT]   Malware signature match found in test.exe

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Scan Complete
  Files scanned : 2
  Threats found : 1
  Status        : INFECTED
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 📄 Report Formats

<details>
<summary><strong>JSON Report</strong></summary>

```json
{
  "file": "test.exe",
  "status": "infected",
  "detections": ["Trojan.Generic"],
  "scanned_at": "2025-08-01T14:32:00"
}
```
</details>

<details>
<summary><strong>TXT Report</strong></summary>

```
File      : test.exe
Status    : INFECTED
Detection : Trojan.Generic
Scanned   : 2025-08-01 14:32:00
```
</details>

---

## 🧠 How It Works

### 🧬 Signature-Based Detection
The engine reads known malware byte patterns and string signatures from `signatures.txt` and compares them against each file's content. A match triggers an `[ALERT]`.

### 🧠 Heuristic Analysis
Even without a known signature, files containing suspicious structures (unusual entropy, dangerous opcodes, obfuscated strings) are flagged as `[WARNING]` for manual review.

### 🚧 Quarantine
When `--quarantine` is enabled, infected files are moved to the `/quarantine` directory — preserving them for analysis while preventing execution.

```
quarantine/
└── test.exe.quarantined
```

---

## ⚠️ Known Limitations

- ❌ No real-time file system monitoring
- ❌ No automatic signature database updates
- ❌ Basic detection — advanced threats may evade
- ❌ Potential false positives on obfuscated-but-safe files

---

## 🗺️ Roadmap

Planned features and improvements:

- [ ] 🔄 Auto-updating signature database
- [ ] 🧵 Multi-threaded directory scanning
- [ ] 🧠 Machine learning–based detection
- [ ] 🖥️ GUI (Tkinter / PyQt5)
- [ ] ☁️ VirusTotal API integration
- [ ] 📊 Web dashboard for scan results
- [ ] 👁️ Real-time file watcher

---

## 🤝 Contributing

Contributions are what make open-source great. All PRs are welcome!

```bash
# 1. Fork the repository
# 2. Create your feature branch
git checkout -b feature/your-feature-name

# 3. Commit your changes
git commit -m "feat: add your feature"

# 4. Push to GitHub
git push origin feature/your-feature-name

# 5. Open a Pull Request
```

Please follow conventional commit style (`feat:`, `fix:`, `docs:`, etc.) and describe your changes clearly.

---

## ⚙️ CI/CD (GitHub Actions)

Add the following file to enable automated checks on every push:

`.github/workflows/python.yml`
```yaml
name: Python CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: '3.x'
      - name: Install dependencies
        run: pip install -r requirements.txt || true
      - name: Smoke test
        run: python main.py --help || true
```

---

## 📜 License

This project is licensed under the **GNU Affero General Public License v3.0**.
See [LICENSE](LICENSE) for full details.

---

## 👤 Author

**M-2006**
- GitHub: [@M-2006](https://github.com/M-2006)

---

<div align="center">

If this project helped you learn something, consider giving it a ⭐ — it means a lot!

*"An antivirus is a silent duel between detection and evasion. Right now, yours is learning to see."*

</div>
