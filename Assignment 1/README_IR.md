# Group Members
* Navam Shrivastav 2019A7PS0092H
* Sukrit Kumar 2019AAPS0231H
* Shrikrishna Lolla 2019AAPS0345H


# Stopword removal
remove_stop_words(list of words)
removes all the words in a list which are present in the 
nltk corpus of english stopwords.
* `remove_stop_words("i own a mansion".split())` => ["mansion"]
* `remove_stop_words("to be or not to be".split())` => []
* `remove_stop_words("hello yorick".split())` => ["yorick"]
* `remove_stop_words("hamlet yorick walk down".split())` => ["hamlet", "yorick" "walk"]
* `remove_stop_words("Shakespeare is a great writer".split())` => ["Shakespeare great writer"]
* `remove_stop_words("Ghost of james lives here".split())` => ["Ghost","james","lives"]  
# Stemming 
stem_words(list) using nltk SnowballStemmer, It follows a modified version of the porter's algorithm

WordNet lemmatizer was also implemented but not used.

* `stem_words(["cared"])` => "care"  
* `stem_words(["fairly"])` => "fair"
* `stem_words(["thou"])` => "thou"
* `stem_words(["university"])` => "univers"
* `stem_words(["running"])` => "run"
* `stem_words(["eatting"])` => "eat"


# Build the index
Building Index is done using the PreProcess function, We iterate through each file and then tokenize the words, 
then remove the stopwords, perform stemming and then insert each term in the list to the inverted index
If it already exists add the doc_id to the existing list otherwise create a new term and list and add the doc_id
preProcess("Directory")

`preProcess("IR")`

# Querying 
retrieve() function is reponsible for the querying and once we call it and enter the query, we
will get the doc_id and the document names satisfying the boolean query.
## Sample test cases for querying

* brutus and caesar and not calpurnia

    ['brutus', 'and', 'caesar', 'and', 'not', 'calpurnia']
    
    Query is brutus$ and list of docs are [8, 15, 17, 19, 20, 26, 28, 34, 40]
    
    Query is caesar$ and list of docs are [3, 6, 7, 8, 10, 13, 15, 19, 20, 21, 23, 26, 29, 30, 33, 34, 35, 36, 42]
    
    Query is calphurnia$ and list of docs are [26]
    
    Found in doc no 8  : hamlet_TXT_FolgerShakespeare.txt
    
    Found in doc no 15  : henry-vi-part-2_TXT_FolgerShakespeare.txt
    
    Found in doc no 19  : henry-v_TXT_FolgerShakespeare.txt
    
    Found in doc no 20  : antony-and-cleopatra_TXT_FolgerShakespeare.txt
    
    Found in doc no 34  : titus-andronicus_TXT_FolgerShakespeare.txt
    
    [[8, 15, 19, 20, 34]]
* brut*

    ['brut*']
    
    Words returned for wildcard query $brut* is ['brutish$', 'brutus$', 'brute$', 'brutusnoth$']
    
    Query is $brut* and list of docs are [34, 3, 5, 8, 40, 10, 15, 17, 19, 20, 26, 27, 28]
    
    Found in doc no 34  : titus-andronicus_TXT_FolgerShakespeare.txt
    
    Found in doc no 3  : richard-iii_TXT_FolgerShakespeare.txt
    
    Found in doc no 5  : the-tempest_TXT_FolgerShakespeare.txt
    
    Found in doc no 8  : hamlet_TXT_FolgerShakespeare.txt
    
    Found in doc no 40  : coriolanus_TXT_FolgerShakespeare.txt
    
    Found in doc no 10  : as-you-like-it_TXT_FolgerShakespeare.txt
    
    Found in doc no 15  : henry-vi-part-2_TXT_FolgerShakespeare.txt
    
    Found in doc no 17  : the-merchant-of-venice_TXT_FolgerShakespeare.txt
    
    Found in doc no 19  : henry-v_TXT_FolgerShakespeare.txt
    
    Found in doc no 20  : antony-and-cleopatra_TXT_FolgerShakespeare.txt
    
    Found in doc no 26  : julius-caesar_TXT_FolgerShakespeare.txt
    
    Found in doc no 27  : king-lear_TXT_FolgerShakespeare.txt
    
    Found in doc no 28  : lucrece_TXT_FolgerShakespeare.txt
    
    [[34, 3, 5, 8, 40, 10, 15, 17, 19, 20, 26, 27, 28]]
* ham*et
    
    ['ham*et']
    
    Words returned for wildcard query et$ham* is ['hamlet$']
    
    Query is et$ham* and list of docs are [8]
    
    Found in doc no 8  : hamlet_TXT_FolgerShakespeare.txt
    
    [[8]]
* not ham*et
    
    not ham*et
    
    ['not', 'ham*et']
    
    Words returned for wildcard query et$ham* is ['hamlet$']
    
    Query is et$ham* and list of docs are [8]
    
    Found in doc no 1  : king-john_TXT_FolgerShakespeare.txt
    
    Found in doc no 2  : romeo-and-juliet_TXT_FolgerShakespeare.txt
    
    Found in doc no 3  : richard-iii_TXT_FolgerShakespeare.txt
    
    Found in doc no 4  : pericles_TXT_FolgerShakespeare.txt
    
    Found in doc no 5  : the-tempest_TXT_FolgerShakespeare.txt
    
    Found in doc no 6  : richard-ii_TXT_FolgerShakespeare.txt
    
    Found in doc no 7  : macbeth_TXT_FolgerShakespeare.txt
    
    Found in doc no 9  : henry-viii_TXT_FolgerShakespeare.txt
    
    Found in doc no 10  : as-you-like-it_TXT_FolgerShakespeare.txt
    ... truncated output
* cal*nia
    
    ['cal*nia']
    
    Words returned for wildcard query nia$cal* is ['calphurnia$']
    
    Query is nia$cal* and list of docs are [26]
    
    Found in doc no 26  : julius-caesar_TXT_FolgerShakespeare.txt
    
    [[26]]
* romeo or juliet or julius or hamlet or yorick

    ['romeo', 'or', 'juliet', 'or', 'julius', 'or', 'hamlet', 'or', 'yorick']
    
    Query is romeo$ and list of docs are [2]
    
    Query is juliet$ and list of docs are [2, 21]
    
    Query is julius$ and list of docs are [3, 6, 8, 15, 20, 26, 29, 42]
    
    Query is hamlet$ and list of docs are [8]
    
    Query is yorick$ and list of docs are [8]
    
    Found in doc no 2  : 
    romeo-and-juliet_TXT_FolgerShakespeare.txt
    
    Found in doc no 21  : measure-for-measure_TXT_FolgerShakespeare.txt
    
    Found in doc no 3  : richard-iii_TXT_FolgerShakespeare.txt
    
    Found in doc no 6  : richard-ii_TXT_FolgerShakespeare.txt
    
    Found in doc no 8  : hamlet_TXT_FolgerShakespeare.txt
    
    Found in doc no 15  : henry-vi-part-2_TXT_FolgerShakespeare.txt
    
    Found in doc no 20  : antony-and-cleopatra_TXT_FolgerShakespeare.txt
    
    Found in doc no 26  : julius-caesar_TXT_FolgerShakespeare.txt
    
    Found in doc no 29  : henry-vi-part-1_TXT_FolgerShakespeare.txt
    
    Found in doc no 42  : cymbeline_TXT_FolgerShakespeare.txt
    
    [[2, 21, 3, 6, 8, 15, 20, 26, 29, 42]]
