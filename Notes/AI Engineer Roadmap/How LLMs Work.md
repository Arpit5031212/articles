

LLMs(Large language Models) are AI systems that can understand and generate human language.  
These are trained on a very large dataset of texts scraped from million of web pages and many other sources.

#### Architecture behind LLMs

LLMs use Transformer architecture.  
And Transformer architecture is a neural network architecture that is very proficient in processing sequential data from learning the pattern of the data.  
So, LLMs use this architecture and from the data they have been trained they have developed the capability of predicting the next word in the sequence.  
So, can you say that LLMs are just a very glorified text autocomplete?  
Yes, you may. But LLMs are much more than that.

Let's see each step that goes behind the LLMs to understand how the words are predicted.

Text -> Tokenization -> Embedding -> Context Window + Attention -> Predict the next words.

#### Tokenization:

The smaller units of a text sequence is called a token, and the process of breaking the text sequence into these tokens is called tokenization. There are multiple methods for tokenization, and these methods determine the length of a token.  
So, tokens can be as small as characters or as long as words or the tokens can also be created by dividing the words in two or more.  
This all depends on the use case of the LLMs.  
Tokenization is just done to represent the text in such a manner that it is meaningful to the machines but it does not loses its context.

#### Embedding:

Now after the tokenization these words are then converted to vectors. Vectors are nothing just the mathematical representation of these tokens in a geographical plane that keeps the similar meaning tokens close to each other. This mapping of tokens to vectors is called embedding.

#### Attention:

The transformer architecture core lies in this step. Transformers use attention mechanism to understand the real picture of the text, and understand it in the context of the text. For example, take these two sentences:

I deposited the money in the bank.  
We walked along the river bank.

Here the word "bank" embedding without Attention mechanism will be treated as same and the both sentences may be treated as close in vector space. But the Attention mechanism will keep the context of the sentence with the word "bank", and thus both will be treated differently.  
It does this by giving weights/score to each word based on its relevance to understand the current focus.  
This context awareness is the real difference that makes LLMs so powerful.

#### Context Window:

After the weights are assigned to the tokens using Attention mechanism, these scores are used to create a boundary around texts, such that the text belonging to similar context stick together forming a context window. This helps the LLMs to predict the next words more accurately.

This Context window act as a memory for LLMs for the current query. Now each model has their own window size, some have 1024 token while some may have million tokens in the context window. It also depends on the compute power of the system.  
But, for more accuracy the smaller the context window the better the results.

If the context window goes past its limits, then the model starts to act strange.

It will start to hallucinate and will make up the irrelevant answers.

As the contexts work in the principle of FIFO, so the previous information might get lost and the model will predict the incorrect information.

Latency will be increased.  
You can summarize the context if it is becoming too large, and start the new session with this summary.  
Or if the data is too big, you may set up a vector store and implement RAG to fetch relevant information only.

#### Temperature:

Temperature is a parameter passed to the LLMs, which defines the entropy of the model. Generally its value ranges from 0 to 2. It works by adjusting the probability distribution of the predicted words.  
Lower temperature makes the token with the high probability more likely to be selected, whereas higher temperatures increase the likelihood of selecting low probability tokens.  
So lower temperatures provide more factual and accurate results, good for research and programming. But higher temperatures are good for creative writing and for brain storming.