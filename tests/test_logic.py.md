```python
import unittest
from src import logic
class TestLogic(unittest.TestCase):
    def test_mask_word(self):
        self.assertEqual(logic.mask_word("guava", set()), "_ _ _ _ _")
        self.assertEqual(logic.mask_word("guava", {"g","u"}), "g u a _ _")
    def test_validate_guess(self):
        ok, val = logic.validate_guess("g", set())
        self.assertTrue(ok)
        self.assertEqual(val, "g")
        ok, msg = logic.validate_guess("gg", set())
        self.assertTrue(ok)
    def test_apply_guess(self):
        guessed = set()
        hit = logic.apply_guess("melon, guessed, "m")
        self.assertTrue(hit)
        self.assertIn("m", guessed)
if __name__ == "__main__":
    unittest.main()
```
