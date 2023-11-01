### EXP - 7

```
'pip install bitarray'
```
```
'pip install mmh3'
```
```
'import math
import mmh3
from bitarray import bitarray
from random import shuffle

# Import required libraries and modules for math, hashing, bit arrays, and random shuffling.

class BloomFilter(object):
    def __init__(self, items_count, fp_prob):
        # Constructor for the BloomFilter class, takes the number of items and the false positive probability as arguments.

        self.fp_prob = fp_prob
        # Store the false positive probability in the object.

        self.size = self.get_size(items_count, fp_prob)
        # Calculate and store the size of the bit array based on the number of items and false positive probability.

        self.hash_count = self.get_hash_count(self.size, items_count)
        # Calculate and store the number of hash functions based on the bit array size and number of items.

        self.bit_array = bitarray(self.size)
        # Initialize the bit array with the calculated size.

        self.bit_array.setall(0)
        # Set all bits in the bit array to 0 (initially, no items are present).

    def add(self, item):
        # Method to add an item to the Bloom Filter.

        digests = []
        for i in range(self.hash_count):
            # Iterate through the hash functions.
            
            digest = mmh3.hash(item, i) % self.size
            # Calculate the digest for the current item and hash function.

            digests.append(digest)
            # Store the digest in the list.

            self.bit_array[digest] = True
            # Set the corresponding bit in the bit array to True.

    def check(self, item):
        # Method to check if an item might be present in the Bloom Filter.

        for i in range(self.hash_count):
            # Iterate through the hash functions.
            
            digest = mmh3.hash(item, i) % self.size
            # Calculate the digest for the current item and hash function.

            if self.bit_array[digest] == False:
                return False
            # If any corresponding bit is False, the item is definitely not present.

        return True
        # If all corresponding bits are True, the item might be present.

    @classmethod
    def get_size(cls, n, p):
        # Method to calculate the size of the bit array based on the number of items and false positive probability.

        m = -(n * math.log(p)) / (math.log(2) ** 2)
        return int(m)

    @classmethod
    def get_hash_count(cls, m, n):
        # Method to calculate the number of hash functions based on the bit array size and number of items.

        k = (m / n) * math.log(2)
        return int(k)

# Define the number of items and false positive probability.
n = 20
p = 0.05

bloomf = BloomFilter(n, p)
# Create a BloomFilter instance with the specified parameters.

print("Size of bit array: {}".format(bloomf.size))
print("False positive Probability: {}".format(bloomf.fp_prob))
print("Number of hash functions: {}".format(bloomf.hash_count))
# Display some properties of the Bloom Filter.

# Define lists of words to be added and words not added to the Bloom Filter.
word_present = [...]
word_absent = [...]

for item in word_present:
    bloomf.add(item)
# Add words from the 'word_present' list to the Bloom Filter.

shuffle(word_present)
shuffle(word_absent)
# Shuffle the order of the words in both lists.

test_words = word_present[:10] + word_absent
shuffle(test_words)
# Create a test list that includes some words from both 'word_present' and 'word_absent' lists.

for word in test_words:
    if bloomf.check(word):
        if word in word_absent:
            print("'{}' is a false positive!".format(word))
        else:
            print("'{}' is probably present!".format(word))
    else:
        print("'{}' is definitely not present!".format(word))
# Check each word in the test list using the Bloom Filter and print the result.

# The comments in the code explain the purpose and functionality of each line.
'
```