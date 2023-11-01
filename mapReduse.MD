### EXP - 6

```
'from collections import Counter

Text = """MapReduce is a processing technique and a program model for distributed computing based on java. The MapReduce algorithm contains two important tasks, namely Map and Reduce. Map takes a set of data and converts it into another set of data, where individual elements are broken down into tuples (key/value pairs). Secondly, reduce task, which takes the output from a map as an input and combines those data tuples into a smaller set of tuples. As the sequence of the name MapReduce implies, the reduce task is always performed after the map job.
Map stage − The map or mapper’s job is to process the input data. Generally the input data is in the form of file or directory and is stored in the Hadoop file system (HDFS). The input file is passed to the mapper function line by line. The mapper processes the data and creates several small chunks of data.
Reduce stage − This stage is the combination of the Shuffle stage and the Reduce stage. The Reducer’s job is to process the data that comes from the mapper. After processing, it produces a new set of output, which will be stored in the HDFS.
"""

# Cleaning text and lowercasing all words
for char in '-.,\n':
    Text = Text.replace(char, ' ')
Text = Text.lower()

# Tokenize the text into words
word_list = Text.split()

# Count the frequency of each word
word_freq = Counter(word_list)

# Convert word frequencies to an array format
word_freq_array = [[word, freq] for word, freq in word_freq.items()]

# Sort the word frequencies by frequency in descending order
word_freq_array.sort(key=lambda x: x[1], reverse=True)

# Calculate and add the total word count as the first element in the array
total_words = sum(word_freq.values())
word_freq_array.insert(0, ['Total Words', total_words])

# Print the word frequencies in a single line as an array
print(word_freq_array)
'
```
