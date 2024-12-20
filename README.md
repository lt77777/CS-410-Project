# CS-410-Project

We can run ```make all``` to generate the queries and indexInput followed by the main script. Subsequent runs when the queries are generated can be done through ```make run```. We have also provided a ```make clean``` to clean those files. 

The original datasets were not in a JSON format, so a small bash script was used to convert these documents to JSON for ingestion into the pyserini indexer
   -> data/inaugural_speeches/convert.bash : extracts the contents of the files from the data/original folder, converts them to JSON, and outputs that to file in data/inaugural_speeches/converted

To index the data in its current folder configuration:
   ```python -m pyserini.index.lucene -collection JsonCollection -input ./data/inaugural_speeches/converted/  -index ./indexes/inaugural_speeches/ -generator DefaultLuceneDocumentGenerator```
This produces an index for main.py to use. You can also change the index via main.py, but this is not necessary for grading purposes. In a full-production test, different indexes would be used to generate multivariate data, but we for grading simplicity we are showcasing just the custom dataset we produced.

To generate the queries, you can use the generate_queries.py file by calling ```python3 generateQueries.py```. NOTE THAT THIS TAKES A LONG TIME. 
   -> There is a sample file already generated (data/inaugaral_speeches/inaugaral_speeches-queries.txt)

# First, build the index as mentioned in README
```python -m pyserini.index.lucene -collection JsonCollection -input ./data/inaugural_speeches/converted/ -index ./indexes/inaugural_speeches/ -generator DefaultLuceneDocumentGenerator```

# Second, run main.py to evaluate the search
```python main.py```
