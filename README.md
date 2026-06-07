# AI Agent

A coding agent powered by Google's Gemini API. It can explore a codebase, read and write files, and run Python scripts to help debug and build software.

## Prerequisites

- Python 3.13+
- [uv](https://docs.astral.sh/uv/getting-started/installation/) (Python package manager)

## Installation

1. Clone the repository:

```
git clone <your-repo-url>
cd ai-agent
```

2. Install dependencies with uv:

```
uv sync
```

## API Key Setup

This project uses the Google Gemini API. You'll need an API key to run it.

1. Go to [Google AI Studio](https://aistudio.google.com/).
2. Sign in with your Google account.
3. Click "Create API Key" (or find it under the API keys section).
4. Copy the generated key.
5. Create a `.env` file in the project root:

```
GEMINI_API_KEY='your_api_key_here'
```

The `.env` file is already in `.gitignore` — never commit your API key to version control.

## Usage

Run the agent with a prompt:

```
uv run main.py "your prompt here"
```

Use the `--verbose` flag to see token usage and function call details:

```
uv run main.py "list the files in the project" --verbose
```

### Examples

```
# Ask the agent to explore the codebase
uv run main.py "what files are in the pkg directory?"

# Ask it to read a file
uv run main.py "read the contents of main.py"

# Ask it to debug something
uv run main.py "Fix the bug: 3 + 7 * 2 shouldn't be 20"

# Ask it to run tests
uv run main.py "run tests.py and tell me if they pass"
```

## Calculator App

The project includes a sample calculator app in the `calculator/` directory that the agent can work with:

```
uv run python calculator/main.py "3 + 5"
uv run python calculator/tests.py
```

## Project Structure

```
ai-agent/
├── main.py                  # Agent entry point
├── prompts.py               # System prompt for the LLM
├── call_function.py         # Function dispatch and tool declarations
├── functions/
│   ├── get_files_info.py    # List directory contents
│   ├── get_file_content.py  # Read file contents
│   ├── write_file.py        # Write/overwrite files
│   └── run_python_file.py   # Execute Python scripts
├── calculator/              # Sample project the agent operates on
│   ├── main.py
│   ├── tests.py
│   └── pkg/
│       ├── calculator.py
│       └── render.py
├── pyproject.toml
└── .env                     # Your API key (not committed)
```
