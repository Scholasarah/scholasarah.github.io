---
Title: Hangman Code
categories:
  - python
tags:
  - python
  - computer science
  - Hangman
---



# Hangman Code

```python
import random
from words import words
import string

def get_valid_word(words):
    word = random.choice(words) # randomly chooses sth from the list
    while '-' in word or ' ' in word:
        word = random.choice(words)
    return word.upper()  # we're going to uppercase all the letters
# print(get_valid_word(words))

def hangman():
    word = get_valid_word(words)
    word_letters = set(word)  # letters in the word
    alphabet = set(string.ascii_uppercase)
    used_letters = set()      # what the user has guessed

    # getting user input
    while len(word_letters) > 0:
        # letters used
        # ' '.join(['a', 'b', 'cd']) --> 'a b cd'
        print('You have used these letters: ', ' '.join(used_letters))

        # what current word is (ie. W - R D)
        word_list = [letter if letter in used_letters else '-' for letter in word]
        print('Current word: ', ' '.join(word_list))

        user_letter = input('Guess a letter: ').upper()
        if user_letter in alphabet - used_letters:
            used_letters.add(user_letter)
            if user_letter in word_letters:
                word_letters.remove(user_letter)
        elif user_letter in used_letters:
            print('You have already used that character. Please try again.')
        else:
            print('Invalid character. Please try again.')
    # gets here when len(words_letters) == 0
    print('You guessed the word', word, '!!')

hangman()
```






* [12 Beginner Python Project - Coding Course](https://youtu.be/8ext9G7xspg)
  * 초급 Python 프로젝트-코딩 과정

-끝-

