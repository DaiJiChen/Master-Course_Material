There are 1 input.txt file and 3 python code files in this project. 
	1.inptut.txt contains URL of several webpages.
	
	2.downloadPages.py
		Input: input.txt 
		Output: a set contain names of all pages.
		Function: 
			First, download html in those webpages.
			Second, use beautifulSoup to get contents of each webpages.
			Third, store contents of every webpage as a txt file, put those txt file in a folder called pages.
		
	3.trie.py
		Input: a set contain names of all pages.
		output: a compressed trie contain all the words.
		Data structure: 
			1.Defined a class called TrieNode, it contain a set pageIDs that store ID of webpages that contain this word. It also contain a list of TrieNode as his child.
			2.Defined a class called Trie, it initially contain a single TrieNode called root. Then it create the entire trie according to steps below:
				First, traversal all documents and store all words in a set, the name of this set is called dictionary. 
				Second, add Dictionary's words into a tree one by one, thus created a normal trie, each node only contain one char. Just as mentioned in textbook chapter 23.5.4.
				Third, remove redundant nodes( nodes that only have one child), then we got a compress trie.
			3.Defined a method called findPages(word), it receive a string as input and search the trie. If the whole string is found, then return the pageIDs stored in the last node( pageIDs will be empty if not found)
			
	4.searchEngine.py
		Function: 
			1. call downloadPages.py to get contents of every webpages.  
			2. call trie.py to create a trie
			3. get input query, search this query in trie, sort pages that contain this query according to their match score, print those pages.
	
	Euclidean length was used to calculate the match score of each page. The larger the Euclidean distance between query and a webpage is, the smaller the match score will be.
	
	Source code is also available at https://github.com/DaiJiChen/Search-engine