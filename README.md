#  HKNMT

 Hindi to Kurukh language translator using OpenNMT-py.

# Installation

Create a new environment in anaconda

Install [pytorch](https://opennmt.net/OpenNMT-py/main.html#installation) in environment 

```bash
conda install pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```

# Usage

```python
pip install --upgrade pip

pip install OpenNMT-py

onmt_build_vocab -config Data/config.yaml -n_sample 1000

onmt_train -config Data/config.yaml
```
## After building a vocab
```python
onmt_translate -model Data/run/model_step_1000.pt -src Data/src-test.txt -output Data/pred_1000.txt -gpu 0 -verbose
```
## Create a Yml file

File name [config.yaml]

## Where the samples will be written
```
save_data: Data/run/example
```
## Where the vocab(s) will be written
```
src_vocab: Data/run/example.vocab.src

tgt_vocab: Data/run/example.vocab.tgt
```
## Prevent overwriting existing files in the folder
```
overwrite: False
```
## Corpus Output
```
Corpus opts:
data:
    corpus_1:
        path_src: Data/src-train.txt
        path_tgt: Data/tgt-train.txt
    valid:
        path_src: Data/src-val.txt
        path_tgt: Data/tgt-val.txt
```
## Vocabulary files that were just created
```
src_vocab: Data/run/example.vocab.src

tgt_vocab: Data/run/example.vocab.tgt
```
## Train on a single GPU
```
world_size: 1
gpu_ranks: [0]
```
## Where to save the checkpoints
```
save_model: Data/run/model
save_checkpoint_steps: 500
train_steps: 1000
valid_steps: 500
```
For more details read [documentation](https://opennmt.net/OpenNMT-py/quickstart.html).

## License

[MIT](https://choosealicense.com/licenses/mit/)
