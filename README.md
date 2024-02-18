# Text2SPARQL: Grammar Pre-training for Text-to-QDMR Semantic Parsers from Intermediate Question Decompositions

## Dependencies
Create conda env  and many other packages upgraded: [env-torch1.9.yaml](env-torch1.9.yaml):
```bash
conda env create -n env-torch1.9 -f env-torch1.9.yaml
conda activate env-torch1.9
```


**To reproduce our annotation procedure see [qdmr2sparql/README.md](qdmr2sparql/README.md).**

For testing qdmr2sparql translator run [qdmr2sparql/test_qdmr2sparql.py](qdmr2sparql/test_qdmr2sparql.py)

## Experiments
Every experiment has its own config file in `text2qdmr/configs/experiments`.
``` bash
python run_text2qdmr.py preprocess experiment_config_file  # preprocess the data
python run_text2qdmr.py train experiment_config_file       # train a model
python run_text2qdmr.py eval experiment_config_file        # evaluate the results
```

Note that preprocessing and evaluation use execution and take some time. **To speed up the evaluation, you can install Virtuoso server (see [qdmr2sparql/README_Virtuoso.md](qdmr2sparql/README_Virtuoso.md)).**

## Samples

The dev and test examples of model output are in [model_samples/](model_samples/).

Checkpoints of our best models:

| Model | Dev | Test | Config |
| :---------: | :---------: | :---------: | :---------: |
| grappa-aug        | **83.6**   | **65.2** | [text2qdmr/configs/eval-checkpoints/grappa_qdmr_aug.jsonnet](text2qdmr/configs/eval-checkpoints/grappa_full_break_aug.jsonnet) |

## Acknowledgements

qdmr2sparql module is based on [sparqling-queries-code](https://github.com/yandex-research/sparqling-queries/tree/master), the paper [SPARQLing Database Queries from Intermediate Question Decompositions](https://arxiv.org/abs/2109.06162v2) was proposed by Irina Saparina and Anton Osokin In proceedings of EMNLP'21.

Text2qdmr module is based on [RAT-SQL code](https://github.com/microsoft/rat-sql), the implementation of ACL'20 paper ["RAT-SQL: Relation-Aware Schema Encoding and Linking for Text-to-SQL Parsers"](https://arxiv.org/abs/1911.04942v5) by Wang et al.

[Spider dataset](https://yale-lily.github.io/spider) was proposed by Yi et al. in EMNLP'18 paper ["Spider: A Large-Scale Human-Labeled Dataset for Complex and Cross-Domain Semantic Parsing and Text-to-SQL Task"](https://arxiv.org/abs/1809.08887v5).

[Break dataset](https://allenai.github.io/Break/) was proposed by Wolfson et al. in TACL paper ["Break It Down: A Question Understanding Benchmark"](https://arxiv.org/abs/2001.11770v1).
