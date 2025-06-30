# CodeAlpha_Hangman-Game
 Creating a simple text-based Hangman game where the player guesses a word one letter at a time.
import random
word_list = ["apple", "tiger", "house", "plant", "chair"]
chosen_word =random.choice(word_list)

word_display = ["_" for _ in chosen_word]
guessed_letters = []
tries = 5
print("🎮 Welcome to Hangman!")
print("Guess the word, one letter at a time.")
print("You have",tries,"incorrect guesses allowed.")
print(" ".join(word_display))
while tries > 0 and "_" in word_display:
    guess = input("\nEnter a letter: ").lower()

    if not guess.isalpha() or len(guess) != 1:
        print("❌ Please enter a single valid letter.")
        continue

    if guess in guessed_letters:
        print("⚠️ You already guessed that letter. Try another one.")
        continue

    guessed_letters.append(guess)

    if guess in chosen_word:
        print("✅ Good guess!")
        for i in range(len(chosen_word)):
            if chosen_word[i] == guess:
                word_display[i] = guess
    else:
        tries -= 1
        print(f"❌ Incorrect! You have {tries} tries left.")

    print("Word:", " ".join(word_display))
    print("Guessed letters:", ", ".join(guessed_letters))

if "_" not in word_display:
    print("\n🎉 Congratulations! You guessed the word:", chosen_word)
else:
    print("\n💀 Game Over! The word was:", chosen_word)
