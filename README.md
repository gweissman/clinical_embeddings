# Clinical Word Embeddings

By Zachary Flamholz, [Lyle Ungar](http://www.cis.upenn.edu/~ungar/), [Gary Weissman](http://pair.upenn.edu/people/core-faculty/gary-weissman)

## Description
Pre-trained word embeddings using the text of published clinical case reports. See the [pre-preprint](https://github.com/gweissman/clinical_embeddings/blob/master/pre_preprint_flamholz_embeddings_2019.pdf) for a detailed description of the methods used to build and test the word embeddings.

## Download

| Model | Dimension | Open Access Case Reports | Open Access All Manuscripts |
| ---- | --------- | ------------------------- | -------------------------- |
| word2vec | 100 | [Download - 269 MB](https://upenn.box.com/s/6sqzqvcunar39324adgy8qncm7yam6hu) | [Download - 2.7 GB](https://upenn.box.com/s/gkyqs962i3i2rw55a821n62ex410bi4a)|
|          | 300 | [Download - 716 MB](https://upenn.box.com/s/s52hsf65c51e3ro0ssx79e6l25qykt0m) | [Download - 7.8 GB](https://upenn.box.com/s/9djgjigsve09a7f9vz6ubtsovqwb40xa)
|          | 600 | [Download - 1.4 GB](https://upenn.box.com/s/3y4h8iwg1dg2y3dqdwufspsl61usc0xv)| |
| fastText | 100 | [Download - 798 MB](https://upenn.box.com/s/03tlndnc00zs9glxqmi0n3bbp5aio4gr)| [Download - 4.7 GB](https://upenn.box.com/s/dsj1att1n0dvz6detp1bde1cxw1o6n84)|
|          | 300 | [Download - 2.3 GB ](https://upenn.box.com/s/aewen67hn672l3zloq9j8d27r88wob69)| [Download - 13.8 GB](https://upenn.box.com/s/zb1i8v6a58xuoiu09b77ofqr1s779lbj)|
|          | 600 | [Download - 4.6 GB](https://upenn.box.com/s/1m2ruy0rj0o7j38w6yzgk6hiqxqusifu)| |
| GloVe | 100 | [Download - 157 MB](https://upenn.box.com/s/7vwz09w0ox4jnhrwxcqhlv1169tl4yqo) | [Download - 1.3 GB](https://upenn.box.com/s/v7f5vu2xfmn0sfj3i3ipvb0gdkqkk0ls) |
|       | 300 | [Download - 445 MB](https://upenn.box.com/s/j8fgpq4pswibu5vl2y2cyeostsonwc6l) | [Download - 3.8 GB](https://upenn.box.com/s/988pkhix1wvnfwujrbtdw9pzpl1j25u9)|
|       | 600 | [Download - 862 MB](https://upenn.box.com/s/ckwl0k9sa7vdu2cmty3e87tcbcrf7uzk)| [Download - 7.4 GB](https://upenn.box.com/s/x2o6y78qqnnfguaj3oou8no3gzep4bp8)|


## Details

Word embeddings are compatible with the [`gensim` Python package](https://radimrehurek.com/gensim/) format.

## Quick start

First download and extract the files from each archive.

```bash
tar -xvf w2v_100d_oa_all.tar.gz
```

Then load the embeddings into Python.

```python
from gensim.models import FastText, Word2Vec, KeyedVectors # KeyedVectors are used to load the GloVe models

# Load the model
model = Word2Vec.load('w2v_oa_all_100d.bin')

# Return 100-dimensional vector representations of each word
model.wv.word_vec('diabetes')
model.wv.word_vec('cardiac_arrest')
model.wv.word_vec('lymphangioleiomyomatosis')

# Try out cosine similarity
model.wv.similarity('copd', 'chronic_obstructive_pulmonary_disease')
model.wv.similarity('myocardial_infarction', 'heart_attack')
model.wv.similarity('lymphangioleiomyomatosis', 'lam')
```

