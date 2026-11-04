# Creative Idea Generator

Version 2 of my AI Agents homework: a beginner-friendly Google Colab notebook that asks for an everyday object and generates **three different creative, practical ideas** for it.

## Run in Google Colab

1. Download [creative_ideas.ipynb](creative_ideas.ipynb).
2. Open [Google Colab](https://colab.research.google.com/), choose **File → Upload notebook**, and upload the file.
3. Connect to a Python runtime and run the cells from top to bottom.
4. The first code cell installs the OpenAI Python SDK.
5. Enter an everyday object when prompted.
6. Enter your OpenAI API key in the hidden `getpass` prompt. Three ideas appear below the final code cell, numbered 1–3, each with a short title and a brief explanation.

You need an internet connection, an OpenAI API key with API billing available, and access to `gpt-5.4-mini`. API usage may cost money; a ChatGPT subscription does not include API usage.

## How it works

The notebook uses `client.responses.create()` with model `gpt-5.4-mini`, asks for exactly three distinct ideas numbered 1–3 with a brief explanation of each, and displays `response.output_text`. Simple comments and Markdown cells explain each step. Version 2 generates all three ideas in one API request and has no repeat loop.

## API key privacy

Enter the API key only at runtime through `getpass`, which hides your typing. Never paste it into a code cell, Markdown cell, README, or output. The notebook uses it in memory to authenticate with OpenAI and does not print it or write it to disk. API errors show a generic message without exception details. Disconnect and delete the Colab runtime when finished.

The notebook is saved with no outputs or execution counts. Before sharing a notebook you have run, use **Edit → Clear all outputs** if you want to remove your object and generated answer.
