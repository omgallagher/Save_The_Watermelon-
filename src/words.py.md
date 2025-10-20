```python
from pathlib import Path
def load_words():
    """Load words from data/words.txt if it exists, else fallback list."""
    fallback = ["python", "watermelon", "function", "testing"]
    data_file = Path(__file__).resolve().parents[1] / "data" / "words.txt"
    if data_file.exists():
        with open(data_file, "r", encoding="utf-8") as f:
            words = [line.strip().lower() for line in f if line.strip() and line.isalpha()]
        return words
    return fallback
```
