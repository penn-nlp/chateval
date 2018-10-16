# ChatEval Evaluation
A Python package for running automated evaluations on generated natural language responses. Used
in production by the [ChatEval platform](https://chateval.org).

## Dependencies
- `python3`
- `numpy`
- `nltk`

## Usage
1. Run `pip install chateval` to install the package.
2. Import the package using `from chateval.metrics import utils`.
3. Use the method as described (e.g. `utils.distinct1(responses)`).

Some evaluation methods that required pre-trained word embeddings take an object as input that
implements `__getitem__` and `__contains__`. An example is given below:

```python
class Embedding:
    def __init__(self, vectors):
        self.vectors = vectors
        self.layer1_size = self.vectors.dim
    
    def __getitem__(self, word):
        return self.vectors.query(word)
    
    def __contains__(self, word):
        return word in self.vectors
    
    def dim(self):
return self.vectors.dim
```

## License
MIT
