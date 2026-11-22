
# Mental Wellness Journal Companion

A Generative AI-powered journaling application that helps users reflect on their daily experiences and emotions through supportive, context-aware responses. The application also provides optional local journal storage and basic distress-keyword detection.

## Features

- **AI-Powered Responses:** Generates supportive responses using a Large Language Model (LLM).
- **Prompt Engineering:** Uses a structured system prompt to acknowledge feelings, suggest one practical step and ask a reflection question.
- **Sample Inputs:** Includes five predefined journal entries covering different emotional situations.
- **Custom Journal Entries:** Allows users to enter their own daily experiences.
- **Distress Detection:** Uses Python regular expressions to identify selected distress-related keywords and display a predefined safety response.
- **Mental Health Support:** Displays India's Tele-MANAS helpline information (14416).
- **Local Journal Storage:** Optionally saves journal entries in a local SQLite database.
- **JSON Validation:** Validates generated responses before displaying them.

## Technologies Used

- Python 3.12
- Streamlit
- Ollama
- Qwen2.5:1.5B
- Requests
- SQLite
- JSON
- Regular Expressions

## Project Structure

```text
Mental-Wellness-Journal-Companion/
│
├── app.py
│   └── Main Streamlit application
│
├── project.json
│   └── Project configuration, system prompt and sample inputs
│
├── requirements.txt
│   └── Python dependencies
│
├── README.md
│   └── Project documentation
│
└── journal.sqlite3
    └── Locally stored journal entries (created when used)
```

## Installation and Setup

### 1. Install Python

Install Python 3.12 and ensure it is available from your terminal.

### 2. Install Ollama

Download and install Ollama from:

https://ollama.com/

### 3. Download the Language Model

Open a terminal and execute:

```bash
ollama pull qwen2.5:1.5b
```

Keep the Ollama service running while using the application.

### 4. Install Dependencies

Navigate to the project directory and execute:

```bash
python -m pip install -r requirements.txt
```

### 5. Run the Application

Execute:

```bash
python -m streamlit run app.py
```

Open the local Streamlit URL displayed in the terminal.

## Model Configuration

The application uses an OpenAI-compatible chat completions endpoint.

Default configuration:

- Model URL: `http://127.0.0.1:11434/v1/chat/completions`
- Model Name: `qwen2.5:1.5b`

For an alternative compatible model server, configure the following environment variables:

**MODEL_URL:** API endpoint of the model server.

**MODEL_NAME:** Name or alias of the served model.

For llama.cpp, an example configuration is:

```text
MODEL_URL=http://127.0.0.1:8080/v1/chat/completions
MODEL_NAME=<served-model-alias>
```

## Prompt Design

The system prompt instructs the model to:

1. Respond warmly to the journal entry.
2. Acknowledge the user's feelings.
3. Suggest one small practical step.
4. Ask one gentle reflection question.
5. Avoid diagnosis, treatment and claims of professional care.
6. Return a structured JSON response.

The prompt and five synthetic sample entries are maintained in `project.json`.

## Safety Handling

The application uses predefined regular-expression patterns to detect selected distress-related expressions.

When a matching expression is detected, the application displays a predefined supportive response instead of sending that journal entry to the LLM.

The application also provides Tele-MANAS support information (14416) for users in India.

**Important:** This is a general reflection and support application, not a medical or mental health diagnostic tool. Keyword-based detection has limitations and cannot replace professional assessment or emergency assistance.

## Local Data Storage and Privacy

Users can enable the local storage option before generating a response.

When enabled, journal entries are stored in a SQLite database named `journal.sqlite3` in the project directory.

- Storage is optional.
- Entries are stored locally on the device.
- The database is not encrypted by the application.
- Journal text is sent to the configured model endpoint for normal AI processing.
- A local model endpoint can be used to keep journal processing on the local machine.

Avoid entering highly sensitive personal information.

## Sample Testing Scenarios

| Sample | Scenario |
|---|---|
| Sample 1 | Feeling calmer after a walk |
| Sample 2 | Nervousness about an upcoming presentation |
| Sample 3 | Loneliness after moving to a new hostel |
| Sample 4 | Feeling overwhelmed and hopeless about exams |
| Sample 5 | Completing an assignment and needing rest |

These samples demonstrate normal response generation, distress detection and optional local storage.

## Project Objective

The objective of this project is to demonstrate how Generative AI and Large Language Models can be integrated into a practical application using prompt engineering, structured output validation and conventional Python programming.

The project highlights the importance of responsible AI usage, input validation, privacy considerations and basic safety handling.
