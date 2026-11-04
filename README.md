# Smart Creative Idea Generator — Version 3

A beginner-friendly Google Colab homework notebook that creates three numbered, different practical ideas for an everyday object.

## Run in Google Colab

1. Download [creative_ideas.ipynb](creative_ideas.ipynb), open [Google Colab](https://colab.research.google.com/), and use **File → Upload notebook**.
2. Connect to a Python runtime and run the cells from top to bottom. The install cell upgrades the OpenAI Python SDK.
3. Run the generator cell and enter your API key in the hidden `getpass` prompt, once per session.
4. Enter an everyday object. Choose **1 Environment**, **2 Business**, **3 Home**, or **4 Technology**.
5. Read ideas **1–3**, each with a brief explanation, a creativity score out of 10, and a practicality score out of 10. Each score has a short explanation. Scores are AI estimates, not guarantees.
6. Choose favorite **1, 2, or 3** to expand it into materials, numbered steps, and difficulty (Easy, Medium, or Hard, with a reason). Choose **4** to skip expansion.
7. Choose **1 Try another object** or **2 Exit**. You can also type `exit` at the object prompt. Invalid menu choices and blank objects are requested again.

You need an internet connection, API billing/credits, and access to the configured model. Generating three ideas uses one API request; expanding a favorite uses a second. Every new object makes a new request. Your object, category, and selected idea are sent to OpenAI.

## Model availability and API compatibility

Checked against official OpenAI documentation on November 4, 2026:

- The exact configured model ID is `gpt-5.4-mini`. Its [official model page](https://developers.openai.com/api/docs/models/gpt-5.4-mini) lists Responses API support and pricing of $0.75 input / $4.50 output per million tokens.
- The homework's `gpt-6-luna` is also a documented Responses API model, according to its [official model page](https://developers.openai.com/api/docs/models/gpt-6-luna). Version 3 retains the previous version's `gpt-5.4-mini` alternative; it does not claim that Luna is invalid or unsupported.
- The notebook uses `client.responses.create(model=..., instructions=..., input=...)` and `response.output_text`, following the [official text generation guide](https://developers.openai.com/api/docs/guides/text). For JSON mode it uses the Responses-specific `text={"format": {"type": "json_object"}}`, as documented in the [structured output guide](https://developers.openai.com/api/docs/guides/structured-outputs). It checks the resulting dictionaries because JSON mode alone does not enforce a schema.

The previous real request failed, but its exact error and account settings are unavailable here. Documentation confirms API compatibility; it does not prove your account has access or available credits. The notebook keeps separate, safe explanations for invalid keys, insufficient quota/credits, unavailable models, denied access, rate limits, timeouts, connection errors, and server errors. There is no automatic model fallback or repeated paid request.

## Key privacy and errors

The API key stays in runtime memory inside the generator function and client. It is never written to disk or printed. Hidden-input fallback is disabled: if `getpass` cannot hide input, the app stops. Never put a key in code, Markdown, or output. Error output shows the SDK exception type and a fixed helpful explanation, never raw exception messages, response bodies, requests, or authorization headers. Invalid, empty, refused, or incomplete answers show a safe response error and return to the repeat-or-exit menu.

Before sharing a notebook you ran, use **Edit → Clear all outputs** to remove objects and answers. Use **Runtime → Disconnect and delete runtime** to release runtime memory when finished. The repository notebook has no saved outputs or execution counts.

## Validation

Syntax and notebook structure are checked locally. Mocked Responses API tests cover all four categories, three numbered ideas and score bounds, favorites 1–3 and expansion context, skip/exit/repeat menus, invalid input, malformed/incomplete answers, and safe API errors. No successful live API test is claimed; mocked tests do not verify billing, account access, network availability, or real model output quality.
