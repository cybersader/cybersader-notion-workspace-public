# Chapter 1 - Cryptography

# Readings

- WIkipedia Cryptography

# Goals of Cryptography

- Secure comms
    - Confidentiality
    - Authenticity
        - generated by the alleged sender
- Insecure comms
    - adversary has:
        - control
        - visibility

# Secure Communication

- Steganography
    - Hide the message
    - Obfuscation
    - “Covered writing”
- Cryptography
    - hide the meaning of the message
    - “hidden writing”
    - **depends on the secrecy of the key**

# 3 concepts

- cryptography
    - algorithms
    - protocols
- cryptanalysis
    - breaking cryptography
- cryptology
    - less common
    - a little bit of both cryptography & cryptanalysis

# History

- 2500+ years old
- Codemakers vs Codebreakers
- Directly driven and challenged by communication & computation technology
- Alan Turing

# Framing for data

- data in motion
- data in transit
- data in rest

# **Ciphers**

- Keyspace is important
- Keysize is important
- Encryption and decryption ease of use is important

## Shift (”Caesar”) Cipher

- Represent the characters as numbers
    - The “shift” is adding to those numbers, then using the resulting character represented by their new numbers
- Easy to break
    - Change the ciphertext 25 times
    - Frequency Analysis
        - Look at the occurences of certain letters, look at signature of that data, then shift to match
        - Use NLP to do the above better
- Use 3 for “caesar” cipher
- Keys are same for both ways
    - symettric key

## Substitution Cipher

- Use a key at any length to encrypt the text
    - you could use a string to encrypt the plaintext and use the key letters to represent numbers to shift it by
- Good for short…bad for long
- Patterns are straightforward to detect

## Frequency Analysis

![Untitled](Chapter%201%20-%20Cryptography/Untitled.png)

### Basic

- Replace some obvious outliers
    - highest
    - lowest
- Keep replacing outliers until some words start to stand out
- Look for letters like I or a or and…common words

### Advanced

- Use NLP algorithms to do the same as above but automated

## Polyalphabetic Ciphers

- Vigenere
    - Use word as a key and keep repeating it over the plaintext
    - Add the key to the plaintext - modulus 26
- Modulus is VERY important to modern cryptography
- Just a fancy shift cipher
- **Breaking Vigenere Cipher**
    - **Like breaking any normal password but a little more intensive**
    - **You are limited by key size**
    - **If the Key creator uses a word larger than 9 letters, then you are pretty much screwed**
    - **Smaller key is more crackable**
    - **The larger the ratio of the plaintext to the ciphertext, the easier it is to crack**
    - **Plaintext should be large**
    - **SOLUTION: for every possible length of key group together the letters from the ciphertext.**
        - **For a key length of 5, group together every 5 letters**
        - **Run frequency analysis on the groups till you arrive at a place where every group has the normal distribution of the alphabet or till more patterns start to show**
        - Kasiski Test for Finding Keyword Length
            - Assume a keylength
            - Start doing some shift gradients across those subtexts that are divided up by the keylength
            - Keep going until text comes out
            - how to find the keyword lenght of the vigenere cipher
                - If you find two identical strings in the ciphertext, then the distance from two matching letters in those strings will give you the possible key lengths
                - it will be a multiple of that number
                - use the most common multiple based on common word lengths for keys
            - Repeated words in plaintext create an issue here…then we can guess keylength
- The perfect cryptographic algorithm
    - The key
        - generates hash that can generate a function which can generate an infinite length key for substituting values like the dictionary cipher
    - Algorithm
        - dictionary cipher
    - Somehow don’t immediately involve the same plaintext and ciphertext set
- Set
    - consists of all of the numbers used
- Irrational Numbers still wouldn’t work because they are well known
    - You need a truly random integer

# Adversarial Models for Ciphers

- Language of the plaintext and the nature of the cipher are assumed to be known to the adversary
    - If you know the language, then you can get frequency features
- 4 models:
    - ciphertext only
        - DIFFICULT
    - known plaintext attack
        - reverse engineer from pairs of plain and cipher text
    - chosen plaintext
        - You can choose some plaintext and get ciphertext
        - you can adjust plaintext and observe the changes
        - The goal is to get key
    - chosen ciphertext
        - you can choose ciphertext and get the plaintext

# 🔒Security Principles

- Kerckhoffs’s Principle
    - a cryptosystem should be secure if everything except the key is public
- Shannon’s maxim
    - The enemy knows the system
    - Security through Obscurity is stupid

# The perfect crypto algorithm

- The key will include a combination of keys and steps to be used in the algorithm correctly
    - The key that is shared with someone should be the library location of some book with shelf number, etc.  OR it is some book that you have shared for selling on Amazon so you can track key access
    - You will use a specific lighting setting with ink in the book which will only show if a certain light in shined on it
        - the type of light used will rotate based on some day length which is also a key
    - The text in the book is then put into one line to be used as the key
- The algorithm
    - Stream cipher
    - One time pad