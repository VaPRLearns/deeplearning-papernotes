## [Supervised Learning of Universal Sentence Representations from Natural Language Inference Data](https://arxiv.org/abs/1705.02364)

TLDR; The authors show that supervised training on the NLI task can produce high-quality "universal" sentence embeddings which outperform other existing models, on transfer tasks. They train the sentence vectors on the SNLI corpus using 4 different sentence encoding model architectures.

### Key Points
- The SNLI corpus is a large corpus of sentence pairs that have been manually categories into 3 classes: entailment, contradiction, and neutral. The SNLI task is good for learning sentence vectors because it forces the model to learn semantic representations

- The 4 sentence encoding architectures used are:
    - LSTM/GRU: Essentially the encoder of a seq2seq model
    - BiLSTM: Bi-directional LSTM where each dim of the two (forwards and backwards) encoding are either summed or max-pooled.
    - Self-attentive network:  Weighted linear combination (Attention) over each hidden state vectors of a BiLSTM
    - Hierarchical ConvNet: The authors introduce a variation of the AdaSent model, where at each layer of the CNN, a max pool is taken over the feature maps. Each max pooled vector is concatenated to obtain the final sentence encoding.

- The BiLSTM-Max w/ 4096 dim encoding performs best out of all on the SNLI task as well as on transfer tasks.

- Some models are sensitive to over to over-specialization on the SNLI training task. This means that some models can perform better on the SNLI task but don't transfer as well compared to other models

- The trained models are used to get sentence representations and test performance on 12 different transfer tasks such as classification (eg: sentiment analysis, Subj/obj), entailment (eg: SICK dataset), caption-image retrieval and a few other tasks.

- PyTorch implementation available [here](https://github.com/facebookresearch/InferSent)

