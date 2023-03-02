# Neural Magic's DeepSparse MLPerf Submission

This is the repository of Neural Magic's DeepSparse submission for [MLPerf Inference Benchmark v3.0](https://www.mlperf.org/inference-overview/).

## BERT Results

In this submission, we show two different methods of optimizing BERT-Large by combining various methods of compression covering: unstructured gradual pruning, quantization-aware training, and structural distillation. 

Maintaining >= 99% of the original BERT-Large F1 score and using the [DeepSparse Engine](https://github.com/neuralmagic/deepsparse), we show it is possible to:
- Compress the FP32 dense weights by orders of magnitude from 1.3 GB to 90-10 MB.
- Improve throughput performance from 5 samples/sec to 5000 samples/sec

Our MLPerf Inference v3.0 submission contains the following results for the BERT-Large SQuAD v1.1 question answering task:

| Benchmark      | Engine  | Precision | Compressed File Size | SQuAD v1.1 F1 Score (R=X% of Base Accuracy) |  Offline Throughput [samples/sec]  |
|:----------------:|:-----------:|-----------:|:-----------:|:------:|:-------:|:--------:|
| [BERT-Large Baseline](https://zenodo.org/record/3733910) | ONNXRuntime | FP32 | 1.3 GB   | 90.874 (R=100.00%)	| 4.60     |
| [oBERT-Large 99%](obert_large.md)                        | DeepSparse  | INT8 | 38.2 MB  | 90.03 (R=99.07%)	  | 1367.14  |
| [oBERT-MobileBERT 99.9%](obert_mobilebert.md)            | DeepSparse  | INT8 | 19.45 MB | 90.80 (R=99.92%)	  | 3275.62  |
| [oBERT-MobileBERT 99%](obert_mobilebert.md)              | DeepSparse  | INT8 | 9.56 MB  | 90.41 (R=99.49%)	  | 5578.73  |

The benchmark implementation and models are stored in the [code/bert](code/bert) directory which contains a `README.md` detailing instructions on how to set up the benchmark. An example of the commands used to generate this submission is stored in [submission.md](submission.md).

The benchmarks were evaluated using a server with two 4th Gen AMD EPYC 9654 (Genoa) CPUs with 96 cores each.

## Model Methods

[oBERT-Large - The Optimal BERT Surgeon applied to the BERT-Large model](obert_large.md)

[oBERT-MobileBERT - The Optimal BERT Surgeon applied to the MobileBERT model](obert_mobilebert.md)

[ResNet50 - AC/DC: Alternating Compressed/DeCompressed Training of Deep Neural Networks](resnet50.md)

## Citation info
If you find our models useful, please consider citing our work:
```bibtex
@misc{https://doi.org/10.48550/arxiv.2203.07259,
  doi = {10.48550/ARXIV.2203.07259},
  url = {https://arxiv.org/abs/2203.07259},
  author = {Kurtic, Eldar and Campos, Daniel and Nguyen, Tuan and Frantar, Elias and Kurtz, Mark and Fineran, Benjamin and Goin, Michael and Alistarh, Dan},
  title = {The Optimal BERT Surgeon: Scalable and Accurate Second-Order Pruning for Large Language Models},
  publisher = {arXiv},
  year = {2022},
  copyright = {Creative Commons Attribution 4.0 International}
}
```

```bibtex
@misc{https://doi.org/10.48550/arxiv.2106.12379,
  doi = {10.48550/ARXIV.2106.12379},
  url = {https://arxiv.org/abs/2106.12379},
  author = {Peste, Alexandra and Iofinova, Eugenia and Vladu, Adrian and Alistarh, Dan},
  title = {AC/DC: Alternating Compressed/DeCompressed Training of Deep Neural Networks},
  publisher = {arXiv},
  year = {2021},
  copyright = {arXiv.org perpetual, non-exclusive license}
}
```
