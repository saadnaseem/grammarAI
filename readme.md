# Grammar AI: A Local Grammar & Writing Enhancer

## Why This Project?

- **Cost Savings:**  
  Tired of paying for Grammarly (~$150/year)?

- **Privacy & Data Safety:**  
  Concerned about data privacy with ChatGPT or other LLM providers?

- **Local Solution:**  
  What if you could run an LLM model locally, specifically tuned to correct the grammar of your emails and writing? This project combines tools to achieve just that.

I combined several components to run Meta's Llama 3.2 (3B)—one of the latest and lightest models—with Ollama. I applied prompt engineering to fine-tune the model specifically for grammar correction and writing enhancement tasks.

## Requirements

- **Ollama:**  
  Follow instructions on the [Ollama GitHub repository](https://github.com/ollama/ollama) to download and install Ollama.

- **Llama 3.2 (3B):**  
  The base model used in this project.

## Getting Started

1. **Fork/Clone This Repository:**  
   Start by forking or cloning this repository to your local machine.

2. **Prepare the Modelfile:**  
   Create a plain text file (e.g., `Modelfile.txt`) with the following content:

   ```text
   # Modelfile: GrammarRefine
   FROM llama3.2                          # Base model (Llama 3.2) [oai_citation_attribution:2‡github.com](https://github.com/ollama/ollama/blob/main/docs/modelfile.md#:~:text=FROM%20llama3.2%20,next%20token%20PARAMETER%20num_ctx%204096)
   PARAMETER temperature 0.7             # Lower temperature for coherent, deterministic edits
   PARAMETER num_ctx 4096                # Context length (4096 tokens for longer inputs) [oai_citation_attribution:3‡github.com](https://github.com/ollama/ollama/blob/main/docs/modelfile.md#:~:text=FROM%20llama3.2%20,next%20token%20PARAMETER%20num_ctx%204096)
   SYSTEM """You are an expert copy editor and writing assistant. Your goal is to fix any grammar or spelling errors, improve clarity and readability, and enhance the style of the user's text while preserving its original intent. Provide the corrected text first, then a brief explanation of the changes made. If needed, you may completely restructure sentences for better clarity. Be concise and maintain the author's voice."""

    ```

3. **Create the Custom Model:**  
Open your terminal, navigate to the folder containing your Modelfile.txt, and run:
```text
ollama create grammarAI -f ./Modelfile.txt
```

4.	Run the Model:
After creating the model, run it with:
```text
ollama run grammarAI
```

Now you can chat with the model and test its grammar correction, clarity improvement, and style enhancement capabilities.

Tuning the Model
	•	More Specific Responses:
If you need more precise corrections, lower the temperature value:
	•	Change temperature to 0.5 for more deterministic edits.
	•	Increase temperature to 0.8 if you want the model to significantly restructure sentences.
Save these changes in a new file (e.g., Modelfile1.txt) and create a new model:
```text
ollama create grammarAI-v2 -f ./Modelfile1.txt
```

Conclusion

This project provides a local, privacy-friendly solution for enhancing your writing without recurring subscription fees. Using Ollama and Meta’s Llama 3.2 with custom prompt engineering, you now have a powerful tool to correct grammar, improve clarity, and polish your writing—all on your local machine.







