# LyS-FASTPARSE at CoNLL2017 UD Shared Task

## BIST-Covington: A non-projective greedy dependency parser with bidirectional LSTMs

A bidirectional LSTM implementation of the Covington (2001) algorithm with dynamic oracle for non-projective transition-based dependency parsing.

BIST-covington is a non-projective parser based on [BIST-parsers](https://github.com/elikip/bist-parser) (Kiperwasser and Goldberg, 2016)

For segmentation and part-of-speech tagging the current system relies on the output provided by [UDpipe](https://github.com/ufal/udpipe) (Straka et al., 2016)



## Required software

Python 2.7 interpreter

[Dynet python module](http://dynet.readthedocs.io/en/latest/python.html)

[Gensim](https://radimrehurek.com/gensim/)

[tarjan](https://pypi.python.org/pypi/tarjan/)

[pyyaml](https://pypi.python.org/pypi/PyYAML)


## Usage

### How to train a parser

The basic command to train a BIST-covington is pretty similar to the one use to train a BIST-parser:

	python train.py \
	--dynet-seed 123456789 \
	--dynet-mem $DYNET_MEM \
	--epochs 30 \
	--model $NAME_OUTPUT_MODEL \
	--conf $PATH_TO_configuration.yml \
	--outdir $OUTDIR \
	--train $PATH_TO_TRAIN_CONLLU_FILE \
	--dev $PATH_TO_DEV_CONLLU_FILE \
	--k1 $K1 \
	--kb $KB \
	--lstmdims $LSTMDIMS \
	--wembedding $WEMBEDDING \
	--userl \
	--usehead \

For a description of all available options (external embeddings, scope of the windows, ...) type:

	python train.py --help 
	
## How to run a parser

To run a trained model:

	python run_model.py \
	-p $PATH_PARAMS \
	-m $PATH_MODEL \ 
	-o $PATH_OUTPUT
	-epe $PATH_POS_EMBEDDINGS \
	-efe $PATH_FEATS_EMMBEDDINGS \
	-ewe $PATH_EMBEDDINGS \
    -r [raw|conllu] \
    -i $PATH_INPUT \
    --dynet-mem $DYNET_MEM \
    -udpipe_bin $PAHT_UDPIPE_BIN \
    -udpipe_model $PATH_UDPIPE_MODEL



## Citation

	@InProceedings{vilares-gomezrodriguez:2017:K17-3,
	  author    = {Vilares, David  and  G\'{o}mez-Rodr\'{i}guez, Carlos},
	  title     = {A non-projective greedy dependency parser with bidirectional LSTMs},
	  booktitle = {Proceedings of the CoNLL 2017 Shared Task: Multilingual Parsing from Raw Text to Universal Dependencies},
	  month     = {August},
	  year      = {2017},
	  address   = {Vancouver, Canada},
	  publisher = {Association for Computational Linguistics},
	  pages     = {152--162},
	  abstract  = {The LyS-FASTPARSE team present BIST-COVINGTON, a neural implementation of the
		Covington (2001) algorithm for non-projective dependency parsing. The 
		bidirectional LSTM approach by Kiperwasser and Goldberg (2016) is used to train
		a greedy parser with a dynamic oracle to mitigate error propagation. The model
		participated in the CoNLL 2017 UD Shared Task. In spite of not using any
		ensemble methods and using the baseline segmentation and PoS tagging, the
		parser obtained good results on both macro-average LAS and UAS in the big
		treebanks category (55 languages), ranking 7th out of 33 teams. In the all
		treebanks category (LAS and UAS) we ranked 16th and 12th. The gap between the
		all and big categories is mainly due to the poor performance on four parallel
		PUD treebanks, suggesting that some 'suffixed' treebanks (e.g. Spanish-AnCora)
		perform poorly on cross-treebank settings, which does not occur with the
		corresponding 'unsuffixed' treebank  (e.g. Spanish). By changing that, we
		obtain the 11th best LAS among all runs (official and unofficial). The code is
		made available at https://github.com/CoNLL-UD-2017/LyS-FASTPARSE},
	  url       = {http://www.aclweb.org/anthology/K/K17/K17-3016.pdf}
	}



## License

This software is released under the terms of the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).

## References

Kiperwasser, E., & Goldberg, Y. (2016). Simple and accurate dependency parsing using bidirectional LSTM feature representations. arXiv preprint arXiv:1603.04351.

Straka, M., Hajic, J., & Straková, J. (2016). UD-Pipe: Trainable pipeline for processing CoNLL-U files performing tokenization, morphological analysis, POS tagging and parsing. In Proceedings of the Tenth International Conference on Language Resources and Evaluation (LREC 2016).

Gómez-Rodríguez, C., & Fernández-González, D. (2015). An efficient dynamic oracle for unrestricted non-projective parsing. Volume 2: Short Papers, 256.

Nivre, J. (2008). Algorithms for deterministic incremental dependency parsing. Computational Linguistics, 34(4), 513-553.

Covington, M. A. (2001). A fundamental algorithm for dependency parsing. In Proceedings of the 39th annual ACM southeast conference (pp. 95-102).



