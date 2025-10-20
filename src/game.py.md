```python
from . import logic, words
def render_state(secret, guessed, slices):
    print("\n=== Save the Watermelon ===")
    print("Word:   ", logic.mask_word(secret, guessed))
    print("Guessed:", " ".join(sorted(guessed)) or "(none)")
    print("Slices:", slices)
def play_once():
    secret = logic.select_secret_word(words.load_words())
    guessed = set()
    slices = logic.MAX_SLICES
    while slices > 0 and not logic.is_win(secret, guessed):
        render_state(secret, guessed, slices)
        raw = input("Guess a letter: ")
        ok, val = logic.validate_guess(raw, guessed)
        if not ok:
            print("[!]")
            continue
        hit = logic.apply_guess(secret, guessed, val)
        if hit:
            print("Nice!")
        else:
            slices -= 1
            print(f" Sliced! Remaining: {slices}")
    render_state(secret, guessed, slices)
    if logic.is_win(secret, guessed):
        print("You saved the watermelon!")
    else:
        print("Sorry, the watermelon was sliced. The word was {secret}',")
def main():
    print("Welcome to Save the Watermelon!")
    while True:
        play_once()
        again = input("Play again? (y/n): ").strip().lower()
        if again not in {"y", "yes"}:
            print("Goodbye!")
            break
if__name__ == "__main__":
    main()
```
