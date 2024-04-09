a [[semantic search]] method that uses a text embedding to find the semantically closest answers to a query

This is done by:

- finding the vector of the embedding of the search query in the LLM
- finding the corresponding embedding vectors for the correlated responses
- returning the response vectors that are closest (K-neighbour algorithm) to the query

## related

- [[ML text embeddings]]


## links and resources

- https://txt.cohere.com/using-llms-for-search/
- https://docs.cohere.com/docs/dense-retrieval