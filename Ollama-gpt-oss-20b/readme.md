install ollama:   
curl -fsSL https://ollama.com/install.sh | sh
￼
```bash
ollama
Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information

Use "ollama [command] --help" for more information about a command.
```

Step 2: Create a Modelfile for your Local GGUF
Create a new, plain text file in the same directory as your .gguf file. Name it Modelfile (no extension).
Put this single line inside the Modelfile:
`FROM /home/neaj/Downloads/gpt-oss-20b-Q4_K_S.gguf`


**Step 3: Create the model from your `Modelfile`**

Navigate your terminal to the directory where you saved your `Modelfile` and run:

```bash
ollama create gpt-oss-20b-local -f Modelfile
```

You will see some output like "transferring model data" as Ollama imports your 11.6 GB GGUF file into its own managed storage. This will take a minute or two but only needs to be done once.


Now, you are ready to use it!


Step 4: Run the Model
Now you can run the model anytime, from any directory, using the name you just gave it.
```bash
ollama run gpt-oss-20b-local
```

### How to Use Your Model

#### Method 1: Interactive Chat in Your Terminal

This is the most direct way to start a conversation.

**Run the model:**
```bash
ollama run gpt-oss-20b-local
```

**What to expect:**
*   The first time, you'll see a message like "loading model" which might take 30-60 seconds as it loads the 12+ GB of data into your RAM.
*   Once it's loaded, you will see a prompt appear, ready for your input:
    ```
    >>> Send a message (/? for help)
    ```

**How to interact:**
*   **Ask a question:** Just type your prompt and press Enter. For example: `What are the key principles of MLOps?`
*   **Be patient:** Remember our discussion about CPU performance. It might take 15-30 seconds to generate a full paragraph. You will see the words appear one by one.
*   **Multi-line input:** To paste a large block of text, type `"""` first, press Enter, paste your text, then type `"""` again and press Enter.
*   **Exit the chat:** Type `/bye` and press Enter.

#### Method 2: The API (For Programmatic Use)

This is the most powerful method. When you installed Ollama, it automatically started a background server. You can send API requests to this server from your code, scripts, or tools like `curl`.

The server runs at `http://localhost:11434`.

**Example using `curl` from your terminal:**

Open a **new terminal** (leave the interactive chat running if you want, or exit it). You can use this command to send a prompt and get a JSON response back.

```bash
curl http://localhost:11434/api/generate -d '{
  "model": "gpt-oss-20b-local",
  "prompt": "Why is Kubernetes popular for MLOps?",
  "stream": false
}'
```

**What to expect:**
*   The command will "hang" for a bit while the model generates the full response.
*   You will then get a single JSON object containing the entire answer, which is great for applications.
    ```json
    {
      "model": "gpt-oss-20b-local",
      "created_at": "...",
      "response": "Kubernetes is popular for MLOps for several key reasons that revolve around scalability, portability, and reproducibility...",
      "done": true,
      "total_duration": 25123456789,
      ...
    }
    ```

This API is what allows you to build applications, scripts, and automation on top of your local model. You can call it from Python, JavaScript, or any language that can make an HTTP request.

**You are all set. Run the `ollama create` command, then `ollama run`, and start experimenting!**