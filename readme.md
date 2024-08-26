# AI-assisted search

Code based on this [repo](https://github.com/Azure/azure-search-vector-samples/blob/main/demo-python/code/indexers/csv.ipynb).
Another example [here](https://github.com/azure-way/rag/blob/main/app/backend/approaches/chatreadretrieveread.py).

Demonstrates use of generative technology in **both steps** of a typical RAG pattern: data retrieval and prompt response.

For data retrieval, the LLM is instructed to generate a search query that is optimized to return only the data needed by the user prompt and use all available features
of the index to do so, e.g. filters, sort options and response count (top). The returned data is then provided to a separate LLM completion request to answer the user's prompt.

The objective for using AI to generate the search API is to ensure that all data relevant to the user prompt is retrieved for presentation to the completion request. For example,
if the user prompt is requesting highest or lowest values for some component of the data, the generated query should include a sort statement. Otherwise, the subsequent
prompt completion will not have the data it needs to respond to the user prompt.

Optimizing search criteria for each user prompts will increase the quality of the eventual response (since the prompt completion will have the relavant data),
reduce cost of the completion (since only relevant data will be passed to it) and improve completion latency due to smaller data payload size.

In order to optimize the search API, the index schema needs to be designed to support the required operations, e.g. have the filter fields
that are likely to be needed to find data appropriate for user prompts. Further enhencement in Azure Search include use of :

1. Vector search and semantic scoring. 
2. [Scoring profiles](https://farzzy.hashnode.dev/enhance-azure-ai-search-document-boosting) to increase significance of hits of specific fields.
2. Synonyms to provide alternative ways for specifying text values

### Setup
1. Clone to local or open in Codespace
2. Copy env-sample to .env
3. Update .env with your settings (blob storage, GPT and embedding model)
3. Create your index using create-index notebook
4. Execute queries using the ai-search notebook


**Note** that .env is .gitignor'ed to protect your secrets.