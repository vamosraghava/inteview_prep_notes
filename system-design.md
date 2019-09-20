## System Design Questions

### Find the first non-repeating word in file

**Problem:  Given a text file of size say 100 GB? Task is to find first non repeating word in this file?  
*constraints*: You can traverse the file only once.**


 - We would store every word in a map using key-value pairs <word, firstIndex>. 
 - We fill the map as we traverse the file. If we are adding a word that already has an entry, we set firstIndex to a NULL value. 
 - After traversing the file, we go over each inserted word and find the smallest firstIndex that is not NULL. 
 - This is a space complexity of O(k) where k is the number of unique words in the file, and a time complexity of O(n) where n is the file size.  
 - If they are English words, which are easily below a million, our space complexity will be below 10 megabytes, assuming 10 characters per word.

### Find top 10 errors by count in distributed logs ( about 100GB or more i.e. can't fit in one machine)
Assume log format for each entry is
"timestamp, app-name, http status code, error message etc..."

### Design short-term website/app which is used for 3 days, and is meant to accept donations from millions of volunteers across country for a charity. Assume 3rd party vendor does actual payment processing.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbODY4MzM4NjU2LC01NjY1OTEwMjVdfQ==
-->