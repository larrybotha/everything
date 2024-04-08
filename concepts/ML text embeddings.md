The numerical representation, as an array of decimal values, of text that represents what the text means

![[1-text-gen-rep.png]]

*Text representation* is what querying the text embeddings is called

The unit of an embedding is called a *feature*

- The length of the array is the number of dimensions the text has
- larger models result in more dimensions
- each dimension holds one additional piece of information about the text
- the more dimensions, the more representational information there is
- [Principles Component Analysis (PCA)](https://en.wikipedia.org/wiki/Principal_component_analysis) allows for reducing the number of dimensions, which can make the data easier to work with, while retaining as much information as possible
- using PCA to reduce embeddings to 2 or 3 dimensions will sacrifice data, but can be useful for visualising approximations of where a query lies relative to a dataset

## links and resources

- https://txt.cohere.com/text-embeddings/