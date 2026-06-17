## 16/06/26 - Sofia

- Embedding: we are using Harrier and Qwen3 in the same way. We should check for the number of max tokens, the padding side, quantization.<br>We should also write better the task and the queries.
- Retrieval: eplore more the k values and print the cosine similarity
- Generation: created a new (useful) function. We should try with/without thinking and the other params in general. Also here we should check for the max number of tokens.<br>Also here we should check the padding and the other params that we chose before, maybe they are not the best here.<br>Also the system_prompt can be written better.
- Evaluation: not sure if just selecting passages (pages) randomly is enough. Also, for each passage would be better to produce a couple of q&a instead of only one pair.<br>A more powerful generator can be tried using cloudveneto.<br>Created the judge-score-part but not tested yet. We need to decide which kind of score we want.


## 04/06/26 - Sofia

Used Google Colab to not have problems. Added some notes (to rewrite) about Qwen3 Model Architecture to better understand the code and how the model works (i have a cute picture about the model architecture but failed to insert it in the markdown, rip).

Tried the 0.6B model but there is still the RAM problem. I'm using the code given ini the Qwen3 huggingface page modifying the task and the queries. I'm not sure about the use of chunk text instead of the whole page text because the model has a limit of 8192 tokens.

The problem is the constraint on the overlap chunk that we have: this forces us to use LangChain but we have to think it as a pure text-splitter.

I don't know hot to keep trace of the metadata, honestly i didn't even try but for sure we can. 

Forget to clean the cells below.


## 03/06/26 - Sofia

Chunk division using LangChain, because at the end the embedding models are using (mainly) the text instead of tokens.

Found out that Bert should not be used as embedder so i tried to use Harrier first (harrier-oss-v1-270m) but didn't work, then i tried also with Qwen3 (Qwen3-Embedding-0.6B) but failed againi.

"Please send help" someone would say.

Btw i think we should use Qwen3 because works better for english than Harrier (chinese).

If we solve this problem then we can proceed with the vector database using faiss-cpu

## 30/05/26 - Giovanni

Created a "new dataset" removing empty documents and merging pages of same documents together. Started working on possible tokenization method: perhaps it is possible to tokenize everything with the AutoTokenizer (raise `max_length` limit) then rearrange the tokens and the dataset to our needs.

I did sort of a retrieval with Bert, I think there is definitely a better way than for cycles to tokenize and to stuff. Batch things.

## 27/05/26 - Sofia

Removed the Musk-v-Aktman-case and cleaned the notebook in general.

Did a dumb test to see if there are almost-empty pages (threshold of 20 characters). We'll see if we'll need to fix this problem of empty-pages by removing them or just creating a single-huge-text with all the pages.

We'll keep you updated, bitches.

xoxo, gossip girl


## 26/05/26 - Sofia

Created the conda env using `create_env.yml`, then added to the `.gitignore` file. 

Introduced in the `dataset.ipynb` some (kind of useful) methods such as `get_dataset_split_names` and `get_dataset_config_names` to better inspect the dataset (useful before downloading it). 

Printed some examples of the text that should be our dataset. Not sure that we can use it as it is, i think we will need to pre-process it (see later why).

If we'll choose the Musk-v-Altman-case dataset i think we should use all the possible 'types' (not only the emails) and filtering for the 'body_markdown' feature.

Here, we can have a problem: I tested the tokenization on the first 'body_markdown' document and i got an error "too many tokens". This is why we'll need some pre-processing or try with another model that has a larger maximum-sequence-length.

Printed also an example for the UFO dataset and seems to be clearer. 

I didn't understand the "Check some documents by id" part.

Also i'm wondering if we need to keep trace of some metadata related to the text (i think so).

I suggest to not work directly on the main but we'll merge the dataset branch once we'll finish with it.




## 26/05/26 - Giovanni

Created a conda env, not sure whether to upload the final created conda env or the original list of packages to be installed. I git pushed the actual `environment.yml` so just `conda env create -f environment.yml` to create the same env called 'nlp'.

I also started to look a little to the possible datasets. In the Musk v Altman case there is more than just mails, we should decide whether to keep all the files or work only on the mails.

The UFO one also contains photos and stuff. Little more preprocessing might be required.

Also I didn't know if we wanted to directly work on the main or not.
