# LangChain v1 Examples (Azure OpenAI)

Hands-on Jupyter notebooks that walk through LangChain v1 using Azure OpenAI as the model provider.

## Notebooks

Work through them in order. They live in [updatedlangchain/](updatedlangchain/).

| # | Notebook | What it covers |
|---|----------|----------------|
| 1 | [1-langchainintro.ipynb](updatedlangchain/1-langchainintro.ipynb) | First calls to an Azure OpenAI chat model and a basic agent with `create_agent`. |
| 2 | [2-modelintegration.ipynb](updatedlangchain/2-modelintegration.ipynb) | Creating models with `AzureChatOpenAI` and `init_chat_model`. |
| 6 | [6-middleware.ipynb](updatedlangchain/6-middleware.ipynb) | Agent middleware: conversation summarization to manage token budgets, and human-in-the-loop approval for tool calls. |

## Project layout

```
.
├── updatedlangchain/     # Jupyter notebooks (the examples)
├── main.py               # Placeholder entry point
├── pyproject.toml        # Project metadata and dependencies (uv)
├── uv.lock               # Locked dependency versions
├── requirements.txt      # Pinned dependencies for pip users
├── .python-version       # Python version (3.14)
└── .env.example          # Template for required environment variables
```

## Requirements

- Python 3.14 or newer
- An Azure OpenAI resource with a `gpt-4o` deployment

## Setup

### Option 1: uv (recommended)

[uv](https://docs.astral.sh/uv/) reads `pyproject.toml` and `uv.lock` and creates the virtual environment for you.

```bash
uv sync
```

### Option 2: pip

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Configuration

The notebooks read their Azure settings from a `.env` file in the project root.

1. Copy the template:

   ```bash
   cp .env.example .env           # Windows: copy .env.example .env
   ```

2. Fill in your values:

   | Variable | Description |
   |----------|-------------|
   | `AZURE_OPENAI_API_KEY` | API key from your Azure OpenAI resource (Keys and Endpoint page). |
   | `AZURE_OPENAI_ENDPOINT` | Resource endpoint, e.g. `https://your-resource-name.openai.azure.com/`. |
   | `AZURE_OPENAI_API_VERSION` | API version, e.g. `2025-01-01-preview`. |

The `gpt-4o` deployment name is set inside the notebooks. If your deployment has a different name, change it there.

`.env` is listed in `.gitignore` and must never be committed.

## Running the notebooks

With the environment set up, open the project in VS Code or run Jupyter:

```bash
uv run jupyter lab             # or: jupyter lab, if using pip
```

Select the project's Python environment as the kernel and run the cells top to bottom.

## Security

- Keep real keys only in `.env`. Do not paste them into notebooks, `main.py`, or commit messages.
- If a key has ever been committed or shared, rotate it in the Azure portal.
- Notebook outputs can show resource endpoints. Clear outputs before committing if you do not want those shared.

## License

Add a license before making this repository public.
