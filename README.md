Sure! Here’s a clean, professional README template for your project **"Gemini and Ollama LangExtract Test"**:

---

# Gemini and Ollama LangExtract Test

This project demonstrates how to use **LangExtract**, a powerful tool for extracting structured data from unstructured text, with two different large language model backends: **Google Gemini** and **Ollama's Gemma 3**. It showcases entity extraction on Persian medical texts, highlighting practical applications and performance comparisons.

---

## Features

* Use of LangExtract for entity and relationship extraction from Persian medical notes.
* Integration with Google Gemini (gemini-2.5-pro model).
* Integration with Ollama’s Gemma 3 local LLM.
* Few-shot learning examples for improved extraction accuracy.
* Example scripts and notebooks for easy experimentation.
* Visualization of extraction results with HTML reports.

---

## Installation

```bash
pip install langextract
# For Ollama usage, follow their installation instructions: https://ollama.com/docs
```

---

## Usage

1. Prepare your prompt and few-shot examples defining entities like patients, diseases, medications, dosages, etc.
2. Use LangExtract API with your chosen model backend (Gemini or Ollama).
3. Extract entities from your input medical texts.
4. Visualize results with the built-in HTML visualizer.

---

## Example

```python
import textwrap
import langextract as lx

prompt = textwrap.dedent(\"\"\"\
    Extract medical entities such as patient names, diseases, medications, dosages, and treatment relationships.
    Use the exact original text for extraction. Do not paraphrase or summarize.
    For each entity, add relevant attributes and a brief explanation.
\"\"\")

examples = [
    lx.data.ExampleData(
        text="بیمار آقای رضا محمدی با سابقه فشار خون بالا، به مدت یک ماه داروی آتنولول 50 میلی‌گرم را روزانه مصرف کرده است.",
        extractions=[
            lx.data.Extraction("Patient", "آقای رضا محمدی", {"role": "بیمار"}),
            lx.data.Extraction("Disease", "فشار خون بالا", {"type": "مزمن"}),
            lx.data.Extraction("Medication", "آتنولول", {"dose": "50 میلی‌گرم", "duration": "یک ماه", "frequency": "روزانه"}),
        ],
    ),
    # More examples...
]

input_text = \"\"\"بیمار آقای علی رضایی، ۵۵ ساله، با سابقه بیماری قلبی و فشار خون بالا به کلینیک مراجعه کرده است.
وی به مدت ۶ ماه داروی آملودیپین 10 میلی‌گرم روزانه و آتورواستاتین 20 میلی‌گرم شبانه مصرف می‌کند.
همچنین، اخیراً دچار علائم دیابت نوع ۲ شده و انسولین 15 واحد صبح‌ها و 20 واحد شب‌ها تجویز شده است.\"\"\"

result = lx.extract(
    text_or_documents=input_text,
    prompt_description=prompt,
    examples=examples,
    model_id="gemini-2.5-pro",  # or use Ollama's model
    api_key="YOUR_API_KEY"
)

print(result)
```

---

## License

MIT License

---

## Acknowledgments

* LangExtract by Google (community-driven project)
* Ollama for local LLM support
* Google Gemini LLM

---

If you want me to customize it further or add sections like Contributing or FAQ, just let me know!
