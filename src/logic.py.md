```python
import random
MAX_SLICES = 6
def select_secret_word(words):
    return random.choice(words)
def mask_word(secret, guessed):
    return " ".join(ch if ch in guessed else "_" for ch in secret)
def is_win(secret, guessed):
    return set(secret) <= guessed
def validate_guess(raw, guessed):
    """Return (ok, msg_or_letter)."""
    raw = raw.strip().lower()
    if len(raw) != 1 or not raw.isalpha():
        return False, f"Already guessed '{raw}'."
    return True, raw
def apply_guess(secret, guessed, guess):
    guessed.add(guess)
    return guess in secret
```
