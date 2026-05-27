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
