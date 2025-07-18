# n8n-projects

This repository contains several n8n workflow JSON files for automating tasks involving audio transcription, translation, Wikipedia queries, and a Telegram-based vector QA chatbot. These workflows leverage integrations with Google Drive, OpenAI, Qdrant, Telegram, and Wikipedia.

---

## Workflow Summaries

### 1. AudioTranscribe_Translate.json
- **Purpose:** Downloads an audio file from Google Drive, transcribes it using OpenAI, summarizes the content, translates it to Telugu, generates audio from the translation, and uploads the result back to Google Drive.
- **Integrations:** Google Drive, OpenAI (for transcription, summarization, translation, and audio generation).
- **Credentials Needed:** Google Drive OAuth2, OpenAI API.

### 2. Simple_wikipedia.json
- **Purpose:** Provides a chat interface (triggered by chat messages) that uses an AI agent to answer questions using Wikipedia and OpenAI, with memory for context.
- **Integrations:** OpenAI (for chat), Wikipedia, n8n chat trigger.
- **Credentials Needed:** OpenAI API.

### 3. Telegram_Vector_QA_chatbot.json
- **Purpose:** Telegram chatbot that can answer questions based on documents stored in a Qdrant vector database. It downloads files from Google Drive, processes them (PDF loader, text splitter, embeddings), stores vectors in Qdrant, and uses OpenAI for QA.
- **Integrations:** Telegram, Google Drive, Qdrant, OpenAI.
- **Credentials Needed:** Telegram API, Google Drive OAuth2, Qdrant API, OpenAI API.

### 4. TranscribeGoogleTrigger.json
- **Purpose:** Watches a specific Google Drive folder for new audio files, downloads them, transcribes using OpenAI, summarizes, translates to Hindi, generates audio, and uploads the result back to Google Drive.
- **Integrations:** Google Drive (trigger, download, upload), OpenAI (transcription, summarization, translation, audio generation).
- **Credentials Needed:** Google Drive OAuth2, OpenAI API.

---

## How to Run Locally

### Prerequisites

- **n8n**: Install n8n (see [n8n documentation](https://docs.n8n.io/)).
- **Node.js**: Ensure Node.js is installed.
- **Accounts & API Keys**: You’ll need credentials for Google Drive, OpenAI, Telegram, and Qdrant as required by each workflow.

### Steps

1. **Clone the Repository**
   ```bash
   git clone <repo-url>
   cd n8n-projects
   ```

2. **Start n8n**
   ```bash
   npx n8n
   ```
   Or, if installed globally:
   ```bash
   n8n
   ```

3. **Import Workflows**
   - Open the n8n editor at [http://localhost:5678](http://localhost:5678).
   - For each `.json` file:
     - Click “Import” in the n8n UI.
     - Select the workflow JSON file to import.

4. **Configure Credentials**
   - In the n8n UI, go to “Credentials.”
   - Add and configure:
     - **Google Drive OAuth2** (for Google Drive nodes)
     - **OpenAI API** (for OpenAI nodes)
     - **Telegram API** (for Telegram nodes)
     - **Qdrant API** (for vector store nodes)
   - Assign these credentials to the respective nodes in each workflow.

5. **Set Environment Variables (if needed)**
   - Some integrations may require environment variables (e.g., for API keys). Set these in your `.env` file or via the n8n UI.

6. **Activate and Run Workflows**
   - Manually trigger or activate workflows as needed.
   - For trigger-based workflows (e.g., Google Drive or Telegram), ensure the triggers are properly configured and credentials are valid.

---

## What Each Workflow Does

- **AudioTranscribe_Translate.json**: Automates audio file transcription, summarization, translation (to Telugu), and audio generation.
- **Simple_wikipedia.json**: AI-powered chat agent that answers questions using Wikipedia and OpenAI.
- **Telegram_Vector_QA_chatbot.json**: Telegram bot for document-based Q&A using vector search and OpenAI.
- **TranscribeGoogleTrigger.json**: Watches a Google Drive folder for new audio files, transcribes, summarizes, translates (to Hindi), and generates audio.

---

## Configuration Details

- **Google Drive:** Requires OAuth2 credentials. Set up in n8n and link to the relevant nodes.
- **OpenAI:** Requires API key. Set up in n8n and link to the relevant nodes.
- **Telegram:** Requires a bot token. Set up in n8n and link to the Telegram nodes.
- **Qdrant:** Requires API endpoint and key. Set up in n8n and link to the vector store nodes.

---

## Example .env (if needed)

```env
OPENAI_API_KEY=your_openai_key
GOOGLE_DRIVE_CLIENT_ID=your_client_id
GOOGLE_DRIVE_CLIENT_SECRET=your_client_secret
TELEGRAM_BOT_TOKEN=your_telegram_token
QDRANT_API_KEY=your_qdrant_key
QDRANT_API_URL=https://your-qdrant-instance.com
```

---

## References

- [n8n Documentation](https://docs.n8n.io/)
- [OpenAI API](https://platform.openai.com/docs/)
- [Google Drive API](https://developers.google.com/drive)
- [Telegram Bot API](https://core.telegram.org/bots/api)
- [Qdrant Documentation](https://qdrant.tech/documentation/)