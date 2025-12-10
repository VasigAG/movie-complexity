# Symbolic Movie Compression: Dune

This project explores the concept of **Symbolic Movie Compression** using Large Language Models (LLMs). The goal is to distill complex narrative structures into a compact, symbolic representation using a predefined set of axiomatic symbols (Characters, Actions, Objects, Emotions, Relations).

The system processes the story in fragments, iteratively refining the compression and defining new "derived symbols" based on the axiomatic ones to handle increasing complexity efficiently.

The current implementation uses **Llama 3.1** (via [Ollama](https://ollama.com/)) to compress the plot of Frank Herbert's *Dune*.

## 🚀 How It Works

1.  **Axiomatic Symbols**: The system starts with a base vocabulary of symbols:
    *   **CHARACTERS**: A, B, C, etc.
    *   **ACTIONS**: LOVE, KILL, FIGHT, RULE, etc.
    *   **OBJECTS**: THRONE, PLANET, SPICE, etc.
    *   **RELATIONS**: FATHER, MOTHER, ENEMY, etc.
2.  **Fragment Processing**: The story is split into text fragments (synopses).
3.  **Iterative Compression**: For each fragment, the LLM is prompted to:
    *   Represent the text using the available symbols.
    *   Define **new derived symbols** composed of existing ones (e.g., `BETRAYAL := KILL (LOVER / ENEMY)`).
4.  **Convergence**: The process repeats until the compression stabilizes.
5.  **Unified Output**: The final compressed fragments are combined into a single symbolic narrative string.

## 🛠️ Prerequisites

*   **Python 3.8+**
*   **[Ollama](https://ollama.com/)**: Must be installed and running locally.
*   **Llama 3.1 Model**: You need to pull the `llama3.1` model.

## 📦 Installation

1.  **Install Python Dependencies**:
    ```bash
    pip install ollama
    ```

2.  **Setup Ollama**:
    *   Install Ollama from [ollama.com](https://ollama.com/).
    *   Start the Ollama server (usually runs in the background or in a separate terminal):
        ```bash
        ollama serve
        ```
    *   Pull the Llama 3.1 model:
        ```bash
        ollama pull llama3.1
        ```

## ▶️ Usage

1.  Open `DerivedMovieComplexity.ipynb` in Jupyter Notebook or VS Code.
2.  Run all cells.
3.  The notebook will output the step-by-step compression for each fragment, followed by the **Final Derived Symbols** and the **Unified Story Compression**.

## 📝 Example Output

**Fragment**:
> "A is the son of B. B is the ruler of planet Arrakis. B is betrayed and killed by C."

**Compressed Output**:
```text
COMPRESSED: [SON = FATHER (B) AND RULER = NAME (OBJECT :: PLANET) CAUSES BETRAYAL = KILL (LOVER / ENEMY:: C)]

NEW SYMBOLS:
- RULER := NAME (OBJECT ::= PLANET)
- BETRAYAL := KILL (LOVER / ENEMY ::)
```

**Unified Story Compression**:
```text
[A = SON (B)] AND [B = RULER (PLANET) CAUSES KILL (B, C)] → ... → RULER (A, PLANET ::= Arrakis)
```
