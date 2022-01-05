# Vocabuliwala 

Takes a book in English, finds the words that are "rare" (by the measure IDF >= 15 or -ln(frequency) > 14) and lists the definition in a dictionary and the places it occurs in the original text. 

Some examples output demonstrating some of the key features of Vocabuliwala:
 - Dictionary lookup
 - Secondary dictionary lookup: looking up dictionary meanings which themselves need explanation
 - Difficulty rating
 - Show appearances in the input book 
 
<img width="838" alt="vocabuliwala" src="https://user-images.githubusercontent.com/1846373/148235043-3687129e-7315-432a-96f1-71a9c7ecc419.png">

<img width="847" alt="Screen Shot 2022-01-05 at 8 09 23 PM" src="https://user-images.githubusercontent.com/1846373/148235754-6d0c0783-95e6-41e0-bd0b-a5b9e4804672.png">


# Who is this for?

 - A casual reader of a book
 - A teacher trying to teach a book
 - Students trying to learn vocabulary for a standardized test

# Features

 - Tokenizes the text and words with NLTK to deal with punctuation
 - Removes proper nouns and character names 
 - Has a lot of custom-built lemmatization (WordNetLemmatizer proved insufficient) to get the root word in order to correctly evaluate rarity AND look up the correct root word in the dictionary
 - Can easily sort the result by order it appears in the book or overall frequency of the word in the book.
 - Often dictionary definitions have words that are also hard, so we do a secondary extraction of word meanings in the dictionary definition to make it easy to understand.

# Numbers
 - Merriam Webster dictionary has 100k words (102,217)
 - Word frequency list (en_full) has 1.5m words (1560428) with a total count of ~710m (709588976)
 - Word frequency list (enwiki) has 1.8m words (1857808) (min count 3) with a totl count of 1.9B (1926212329)
 - Anecdotally, around 10-15% of unique words of a book will be a vocab word if 15 threshold, 5-10% if 16 threshold.
 - Anecdotally, around 70% of vocab words have definitions but this number will vary widely. 
 
 
# TODO 

  - Doesn't do much for words transliterated from other languages - marks them as vocab words with no dictionary definition.
  - Lemmatize before doing secondary lookup of dictionary definition words e.g. "tergiversates"
  - Make sure non dict words are written to the vocab   
  - Aggregate words which lemmatize to the same word
  - Make plugin definition collapsible
