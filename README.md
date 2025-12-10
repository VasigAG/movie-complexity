# Symbolic Movie Compression: Star Wars

This project explores the concept of **Symbolic Movie Compression** using Large Language Models (LLMs) to estimate the **Kolmogorov Complexity** of a movie narrative. The goal is to distill complex narrative structures into a compact, symbolic representation using a predefined set of axiomatic symbols (Roles, Actions, Objects, Relations, Logic).

The system uses a **SymbolicCompressor** to process the story in fragments, iteratively refining the compression to minimize the total description length (Complexity Score).

The current implementation uses **Llama 3.1** (via [Ollama](https://ollama.com/)) to compress the plot of *Star Wars: A New Hope*.

## 🚀 How It Works

1.  **Axiomatic Symbols**: The system starts with a base vocabulary of symbols:
    *   **ROLES**: HERO, VILLAIN, MENTOR, PRINCESS, etc.
    *   **ACTIONS**: FIGHT, KILL, RESCUE, ESCAPE, CAPTURE, etc.
    *   **OBJECTS**: WEAPON, SHIP, PLANET, PLANS, FORCE, etc.
    *   **RELATIONS**: FATHER, SON, MASTER, FRIEND, etc.
2.  **Complexity Metric**: We define complexity as:
    $$ C = |Narrative| + |Dictionary| $$
    Where $|Narrative|$ is the length of the compressed story string, and $|Dictionary|$ is the length of all new derived symbol definitions.
3.  **Iterative Optimization**: For each fragment, the LLM is prompted to:
    *   Represent the text using available symbols.
    *   Define **new derived symbols** only if they reduce the total complexity score.
4.  **JSON Output**: The model outputs structured JSON containing the compressed form and new definitions.

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
    *   Start the Ollama server:
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
3.  The notebook will initialize the `SymbolicCompressor`, run the compression loop on the Star Wars fragments, and output the final complexity score and symbolic dictionary.

## 📝 Example Output

**Fragment**:
> "The Galactic Empire captures Princess Leia's ship. She hides the Death Star plans inside the droid R2-D2..."

**Compressed Output (JSON)**:
```json
{
  "compressed_text": "CAPTURE(VILLAIN, PRINCESS_SHIP) -> HIDE(PRINCESS, PLANS, DROID)",
  "new_definitions": {
     "PRINCESS_SHIP": "SHIP(OWNER=PRINCESS)"
  }
}
```

**Final Complexity Score**: `1240` (Example value)
