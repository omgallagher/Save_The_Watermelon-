## psuedocode
FUNCTION main
  PRINT "Save the Watermelon"
  DO
  CALL play_once
  again INPUT "Play again? (y/n): "
WHILE again IN {"y", "yes"}
PRINT "Goodbye!"
END FUNCTION

FUNCTION play_once
  secret ~ secret_secret_word()
  guessed ~ 0
  slices ~ MAX_SLICES

  WHILE slices > 0 AND NOT is_win(secret, guessed)
    DISPLAY render_state(secret, guessed, slices)

    raw ~ INPUT "Guess a letter: "
    (ok, guess) ~ validate_guess(raw, guessed)

    IF NOT ok THEN
      DISPLAY error message
      CONTINUE
    ENDIF

    ADD guess TO guessed
    (status, hit) ~ apply_guess(secret, guessed, guess)

    IF hit THEN
      DISPLAY "Nice!"
    ELSE
      slices ~ slices -1
      DISPLAY "Sliced! Remaining: " + slices
    ENDIF
  END WHILE

  DISPLAY render_state(secret, guessed, slices)

  IF is_win(secret, guessed) THEN
    DISPLAY "You saved the watermelon!"
  ELSE
    DISPLAY ", the watermelon was sliced. The word was: " + secret
  ENDIF
END FUNCTION

FUNCTION select_secret_word
  LOAD words from list or file
  RETURN random choice
END FUNCTION

FUNCTION mask_word(secret, guessed)
  FOR each letter IN secret
    IF letter IN guessed THEN show letter
    ELSE show "_"
  RETURN masked word
END FUNCTION

FUNCTION validate_guess(raw, guessed)
  If raw is not a single letter THEN return (False, "Enter one letter only")
  IF raw is not alphabetic THEN return (False, "Letters only")
  IF raw already IN guessed THEN return (False, "Already guessed")
  RETURN (True, lowercase(raw))
END FUNCTION

FUNCTION apply_guess(secret, guessed, guess)
  ADD guess to guessed
  IF guess IN secret THEN return ("hit", True)
  ELSE return ("miss", False)
END FUNCTION
