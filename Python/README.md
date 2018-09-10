SEAL -- learning from Subgraphs, Embeddings, and Attributes for Link prediction
===============================================================================

About
-----

Python version of SEAL (learning from Subgraphs, Embeddings, and Attributes for Link prediction).

Usages
------

Please download our [\[pytorch_DGCNN software\]](https://github.com/muhanzhang/pytorch_DGCNN) to the same level as the root SEAL folder (not this Python folder). DGCNN is the default graph neural network in SEAL.

Install pytorch_DGCNN according to its instruction.

Type "python Main.py" to have a try of SEAL on the USAir network.

Type:

    python Main.py --data-name NS --test-ratio 0.5 --hop 'auto' --use-embedding

to run SEAL on the NS network with 50% observed links randomly removed as testing links, hop number set automatically from {1, 2}, and node2vec embeddings included.

Type:

    python Main.py --train-name PB_train.txt --test-name PB_test.txt --hop 1

to run SEAL on a custom splitting of train and test links, where each row of "PB_train.txt" is an observed training link, each row of "PB_test.txt" is an unobserved testing link. Note that links in "PB_train.txt" will be used to construct the observed network, yet it is not necessary to train SEAL on all links in "PB_train.txt" especially when the number of observed links is huge. To set a maximum number of links to train on, append "--max-train-num 10000" for example.

Sometimes even extracting 1-hop enclosing subgraphs for some links leads to unaffordable number of nodes in the enclosing subgraphs, especially in Twitter-type networks where a hub node can have millions of followers. To deal with this case, append "--max-nodes-per-hop 100" for example to restrict the number of nodes in each hop to be less than 100 using random sampling. SEAL will still have excellent performance.


Requirements
------------

Tested with Python 2.7, Pytorch 4.0.

All python libraries required by pytorch_DGCNN such as networkx, tqdm, sklearn etc. are required.

Python libraries gensim and scipy are required.

A network embedding software node2vec has been included in "software/". If it does not work, you may need to reinstall it from source.


Reference
---------

If you find the code useful, please cite our paper:

    @article{zhang2018link,
      title={Link Prediction Based on Graph Neural Networks},
      author={Zhang, Muhan and Chen, Yixin},
      journal={arXiv preprint arXiv:1802.09691},
      year={2018}
    }

Muhan Zhang, Washington University in St. Louis
muhan@wustl.edu
2/10/2018