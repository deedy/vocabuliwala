# Vocabuliwala 

Takes a book in English, finds the words that are "rare" (by the measure IDF >= 15 or -ln(frequency) > 14) and lists the definition in a dictionary and the places it occurs in the original text. The final output is a static HTML file. You can view a live demo for a subset of words from a book here: https://deedy.github.io/vocabuliwala/

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

# Usage Instructions

This is definitely not easy to use for non-technical people (and even technical people). It was a quick and dirty project.  
 - Clone the repo and fire up `jupyter` / `ipython notebook` in the directory and open up `Vocabulary Extractor.ipynb`. 
 - Create a directory and put your book txt in it (e.g. `book/book.txt`)
 - Change the name of the `BOOK` variable up top to `book/book.txt`
 - Manually run all the parts of the notebook. You may need to download the Python deps. It takes ~20-30s for a large book and isn't fully optimized. 
 - The output in `html` with 3 sort orders - by order of most rare, by order of most used in the book, and by order of appearance in the book - will be saved as static `html` files in `book/` such as `book/book_vocab_sortby_most_common_first.html`.

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

  - Make it a runnable script instead of a notebook and add options for IDF threshold, etc. 
  - Doesn't do much for words transliterated from other languages - marks them as vocab words with no dictionary definition.
  - Lemmatize before doing secondary lookup of dictionary definition words e.g. "tergiversates"
  - Make sure non dict words are written to the vocab   
  - Aggregate words which lemmatize to the same word
  - Make plugin definition collapsible
