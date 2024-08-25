# AI-assisted search

Demonstrates use of generative technology in both steps of a typical RAG pattern: data retrieval and prompt response.

For data retrieval, the LLM is instructed to generate a search query that is optimized to retrun only the data needed by the user prompt and use available features
of the index, e.g. filters, sort options and response count (top). The returned data is then provided to a separate LLM completion request to answer the user's prompt.

The objective for using AI to generate the search API is to ensure that only data relevant to the user prompt is retrieved for presentation to the completion request.
That should improve the quality of the eventual response and its cost.

Based on this [repo](https://github.com/Azure/azure-search-vector-samples/blob/main/demo-python/code/indexers/csv.ipynb).

### Setup
1. Clone to local or open in Codespace
2. Copy env-sample to .env
3. Update .env with your settings (blob storage, GPT and embedding model)
3. Create your index using create-index notebook
4. Execute queries using the ai-search notebook


**Note** that .env is .gitignor'ed to protect your secrets.