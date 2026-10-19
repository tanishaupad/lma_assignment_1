# Magic Comprehensive Rules RAG assignment

Open and run `Magic_RAG_Assignment.ipynb` from top to bottom with a Python 3.12 kernel. It is the project's single code file. The notebook uses the official September 25, 2026 [Comprehensive Rules PDF](https://media.wizards.com/2026/downloads/MagicCompRules%2020260925.pdf), downloading it when absent and verifying its checksum.

The notebook starts with the original PDF, extracts all pages, parses numbered rules, makes chunks that fit both retrieval models, and writes `corpus/chunks.jsonl` and `corpus/manifest.json`. It then builds a FAISS index with `BAAI/bge-base-en-v1.5`, retrieves the top 10 passages, reranks those 10 with `cross-encoder/ms-marco-MiniLM-L6-v2`, and compares the top 3 from each path. It records rank shifts and retrieval latency. Answer generation uses the same Gemini model and settings for both paths.

When the notebook reaches section 8, enter your Gemini API key in the hidden password prompt. The key stays in kernel memory and is not written into the notebook, its output, or `corpus/`. Do not paste it into a code or Markdown cell. You can obtain a key in [Google AI Studio](https://aistudio.google.com/app/apikey). Running the notebook again after a kernel restart prompts for the key again. Gemini API usage is subject to your Google project's tier, pricing, and rate limits.

The notebook includes four starter questions. Its final cell creates an answer review worksheet in `corpus/answer_audit.json`: retrieved evidence and generated answer correctness are evaluated separately. Fill in the judgments after checking Gemini's answers against the PDF, then write the assignment report in your own words. The generated `corpus/` directory is excluded from version control and will be regenerated when the notebook runs.

`REPORT_DRAFT.tex` is the editable report draft. Open it in the Codex LaTeX editor to review the PDF preview. Personalize its wording before submitting the report, as required by the assignment brief.
