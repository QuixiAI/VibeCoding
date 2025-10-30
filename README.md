# 🪩 VibeCoding Dataset Project

**Collecting the vibes of coding — one log at a time.**

---

## 📢 Call for Volunteers

We’re building an open dataset to capture *real-world coding interactions* between developers and AI coding assistants — and **we need your help**!

This dataset will help researchers and developers better understand *how humans and code models interact* across different tools, and improve the future of AI-assisted software development.

---

## 🎯 Project Overview

The **VibeCoding Dataset** aims to collect anonymized **client ↔ server message logs** from popular AI coding tools and interfaces.
These logs will form the basis of an open dataset hosted on Hugging Face and GitHub.

* **Hugging Face:** [https://huggingface.co/datasets/QuixiAI/VibeCoding](https://huggingface.co/datasets/QuixiAI/VibeCoding)
* **GitHub:** [https://github.com/QuixiAI/vibecoding](https://github.com/QuixiAI/vibecoding)

---

## 🧰 Tools We’re Targeting

We’re collecting interaction logs from the following coding assistants and CLIs:

* Claude Code
* OpenAI Codex
* Gemini CLI
* Open-Code
* Cline
* Roo Code
* Continue.dev
* Cursor
* Windsurf
* Goose
* OpenHands
* Aider
* Factory Droid CLI

If you regularly use any of these — you’re exactly who we need!

---

## 🧩 What You’ll Do

1. **Set up a logging proxy**
   Use a lightweight tool like [LiteLLM](https://github.com/BerriAI/litellm) or [Dolphin Logger](https://github.com/QuixiAI/dolphin-logger) to capture your coding assistant’s request/response data.

2. **Record your sessions**
   As you use your AI coding tool normally, your proxy will record the message logs between your client and the model API.

3. **Anonymize and submit**
   Before submission, make sure your logs contain no private or sensitive information.
   See our [Data Cleaning Guide](docs/data-cleaning.md) (coming soon).

4. **Contribute your data**
   Submit your anonymized logs via:

   * Pull request to this repo, or
   * Upload through the [Hugging Face dataset page](https://huggingface.co/datasets/QuixiAI/VibeCoding)

---

## 🤝 Contributing

Here’s how to get started capturing logs safely and easily.

### Option 1 — Using LiteLLM

LiteLLM is a drop-in proxy for OpenAI-compatible APIs.

#### **1️⃣ Install LiteLLM**

```bash
pip install litellm
```

#### **2️⃣ Run a local proxy**

```bash
litellm --port 4000 --log --log_file logs/vibecoding.jsonl
```

#### **3️⃣ Configure your tool**

Change your AI coding tool or CLI to point to:

```
OPENAI_API_BASE=http://localhost:4000
```

Keep your normal API key set as usual.

#### **4️⃣ Use your tool normally**

LiteLLM will log all incoming/outgoing messages in `logs/vibecoding.jsonl`.

---

### Option 2 — Using Dolphin Logger

Dolphin Logger provides an intercepting proxy that records JSON message streams.

#### **1️⃣ Install**

```bash
git clone https://github.com/yoheinakajima/dolphin-logger.git
cd dolphin-logger
npm install
```

#### **2️⃣ Start the logger**

```bash
npm start
```

By default, this runs on `http://localhost:3000`.

#### **3️⃣ Set your proxy**

Point your coding assistant’s API endpoint or environment variable to:

```
HTTP_PROXY=http://localhost:3000
```

#### **4️⃣ Collect logs**

Your logs will appear in the `logs/` directory as JSON files.

---

### 🧼 Clean Your Logs

Before submission, **please remove or redact**:

* Any personal identifiers (e.g., email, usernames)
* Proprietary or confidential code
* Project names or unique file paths

You can anonymize text manually or use our upcoming `sanitize_logs.py` script.

---

### 📨 Submit Your Data

When your logs are ready:

1. Fork this repository
2. Create a folder under `submissions/<your_handle>/`
3. Add your cleaned `.json` or `.jsonl` logs
4. Open a pull request

Alternatively, you can upload them directly to our [Hugging Face dataset](https://huggingface.co/datasets/QuixiAI/VibeCoding).

---

## 🫶 Credits & Acknowledgements

All volunteers who contribute cleaned and usable logs will be **credited by name or handle** in:

* The **dataset release notes**
* The **model card**
* The **GitHub contributors section**

We appreciate your help in making open-source AI more transparent and human-centered!

---

## 💬 Get Involved

Join the discussion in our dedicated channel:
👉 **`#vibecoding-dataset-project`**

Ask questions, share your setup, or get help with proxy configuration.

---

## ⚖️ License & Ethics

This project follows the principles of **open, ethical data collection**:

* No private or proprietary data
* No identifying information
* Only voluntary, informed contributions

Dataset licensed under **CC BY-SA 4.0**.

---

## 🚀 Quick Links

* 🧠 Dataset: [Hugging Face – QuixiAI/VibeCoding](https://huggingface.co/datasets/QuixiAI/VibeCoding)
* 💻 Code & Instructions: [GitHub – QuixiAI/vibecoding](https://github.com/QuixiAI/vibecoding)
* 💬 Discussion: `#vibecoding-dataset-project`

---

*Help us capture the rhythm of coding — one conversation at a time.*

---

Would you like me to add a **`sanitize_logs.py`** example script next (with regex-based anonymization and safe field filtering)? That would make the setup fully reproducible for contributors.
