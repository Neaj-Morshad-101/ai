opencode cli instead of claude code and their free models like MiMo V2 Pro Free. These are very good and free and there is no limits.

Perfect! ✅ You now have a working OpenCode CLI setup with **MiMo V2 Pro Free**. Here’s a **full, clear guide** you can save for future reference — from scratch to running models.

---

# **OpenCode CLI + Free Models Setup Guide**

---

## **1️⃣ Install OpenCode CLI**

**Option A (npm)** – Recommended:

```bash
npm install -g opencode-ai
```

**Option B (curl script):**

```bash
curl -fsSL https://opencode.ai/install.sh | sh
```

Check installation:

```bash
opencode --version
```

---

## **2️⃣ Add your API key (credential)**

Run:

```bash
opencode auth login
```

1. Select **provider** → choose the appropriate one (e.g., `Other` if using a custom key).
2. Enter **provider ID** → any identifier for your API key.
3. Enter **API key** → the actual key from your provider.
4. Finish setup.

Your key is now stored at:

```
~/.local/share/opencode/auth.json
```

---

## **3️⃣ Refresh and list available models**

```bash
opencode models --refresh
```

You’ll see a list like:

```
opencode/big-pickle
opencode/gpt-5-nano
opencode/mimo-v2-omni-free
opencode/mimo-v2-pro-free
opencode/minimax-m2.5-free
opencode/nemotron-3-super-free
amazon-bedrock/amazon.nova-2-lite-v1:0
amazon-bedrock/amazon.nova-lite-v1:0
```

> ⚠ Use the **exact model name** shown here for commands or config.

---

## **4️⃣ Configure default model**

Open or create:

```bash
nano ~/.opencode/opencode.json
```

Minimal config:

```json
{
  "$schema": "https://opencode.ai/config.json",
  "model": "opencode/mimo-v2-pro-free"
}
```

* `"model"` → the **exact ID** of the model you want as default.
* Do **not** include old keys like `providers` or `default_provider`.

---

## **5️⃣ Test the setup**

Run a simple command:

```bash
opencode run "Write a Go function to reverse a slice"
```

✅ You should get a response using **MiMo V2 Pro Free**.

---

## **6️⃣ Using other models (optional)**

Temporary override:

```bash
opencode run --model opencode/mimo-v2-omni-free "Write a Python script to read CSV"
```

Interactive session:

```bash
opencode
/models  # pick any available model
```

---

## **7️⃣ Optional: shell alias for convenience**

Add to `~/.bashrc` or `~/.zshrc`:

```bash
alias oc='opencode run --model opencode/mimo-v2-pro-free'
```

Then you can just run:

```bash
oc "Generate a Kubernetes YAML template for a StatefulSet"
```

---

## **8️⃣ Tips / Best Practices**

* Always use `opencode models --refresh` before switching providers or models.
* Keep multiple API keys in `~/.local/share/opencode/auth.json` for different providers.
* Pick free models (`*-free`) to avoid hitting rate limits or costs.
* Use shell aliases for your most-used models for faster workflow.
* Interactive mode (`opencode`) is useful for experimentation.

---

✅ **Your setup summary**

* Installed OpenCode CLI
* Logged in with your API key
* Refreshed models → picked `opencode/mimo-v2-pro-free`
* Configured default model in `opencode.json`
* Tested by generating a Go function

Now you can run **any code-generation or AI-assistant command** with OpenCode CLI without touching the JSON again.

---

If you want, I can also make a **ready-made config + alias file** that includes **all the best free OpenCode models** for coding, so you can just drop it in and switch between them instantly.

Do you want me to do that?
