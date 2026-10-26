# OAuth Setup Guides

A small Streamlit app that helps developers understand the work involved in preparing an app's OAuth integration. Browse three saved examples (Google Calendar, GitHub OAuth App, and Atlassian Jira Cloud OAuth 2.0 (3LO)), or enter another app name or website to research a guide live. Guides can be downloaded as Markdown files.

## What the labels mean

- **Official documentation** — a provider fact supported by a linked official source.
- **Estimate** — a reasoned estimate, not a provider commitment or measured setup time.
- **Unknown** — the available information does not establish the answer; no timeline or requirement is guessed.
- **Not tested** — no provider OAuth app, consent flow, or approval request was created or tried for that guide.

Saved examples are documentation-based and not tested. Live-generated guides are researched by AI using OpenAI's Responses API and built-in web search. They are labeled **Live-generated · Not tested**. The AI-generated content and citations are not independently verified, so review the official provider links before relying on the guide.

## Run locally

Requires Python 3.10 or newer. From the project folder, create an isolated environment, install dependencies, and start Streamlit:

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m streamlit run app.py
```

Open the local address printed by Streamlit, usually `http://localhost:8501`.

Live research needs an OpenAI API key with API access. Add it locally to `.streamlit/secrets.toml` in this format:

```toml
OPENAI_API_KEY = "your-key-here"
```

Replace the placeholder on your machine. Do not paste a real key into source code or commit it. **No API keys are stored in this repository.** `.gitignore` excludes `.streamlit/secrets.toml`.

## Using the app

- **Saved guides** contains the three bundled examples and any live guides saved locally. Select a guide and use **Download as Markdown** to save a shareable `.md` file.
- **Generate new guide** accepts an app name or website. The AI searches for official OAuth or integration documentation and creates a source-linked guide. It does not create a provider app or run an OAuth flow.
- Generated guides first live in the current Streamlit session. Click **Save guide** to persist a guide locally; it then appears in **Saved guides** and can be downloaded there. A saved guide with the same name is updated.
- **Developer tools** contains a small API connection check. It is separate from guide generation.

Live guide requests use model `gpt-6-luna`, low search context, at most 3 built-in tool calls, up to 3000 output tokens, and at most 1 SDK retry. An API response marked incomplete is rejected rather than shown or saved as a complete guide. These limits reduce request size; they do not guarantee a particular API cost.

## Local files and sharing limits

- `app.py` contains the interface and the three bundled guide examples.
- `saved_live_guides.json` is created when you save a generated guide. It stores the guide text, source links, label, and save time on this machine. It is ignored by Git as local generated/test data.
- `requirements.txt` lists Streamlit and the OpenAI SDK.
- `.streamlit/secrets.toml` is local configuration and is ignored by Git.

Markdown downloads can be shared as files. Saved guides otherwise remain on this machine: there is no hosted database, authentication, deployment, or public per-guide URL in this demo.
