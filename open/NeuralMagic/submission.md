
# ResNet

## ResNet 85% Pruned Quant Offline

```
cm run script --tags=run,mlperf,inference,generate-run-cmds,_all-modes,_submission,_full  \
   --adr.python.name=mlperf \
   --adr.python.version_min=3.8 \
   --adr.compiler.tags=gcc \
   --submitter=NeuralMagic \
   --implementation=reference \
   --compliance=no \
   --model=resnet50 \
   --precision=int8 \
   --backend=deepsparse \
   --hw_name=default \
   --device=cpu \
   --scenario=Offline \
   --mode=performance \
   --execution_mode=valid \
   --adr.imagenet-preprocessed.tags=_pytorch \
   --adr.mlperf-inference-implementation.dataset=imagenet_pytorch \
   --adr.mlperf-inference-implementation.model=zoo:cv/classification/resnet_v1-50/pytorch/sparseml/imagenet/pruned85_quant-none-vnni \
   --adr.mlperf-inference-implementation.max_batchsize=16 \
   --adr.mlperf-inference-implementation.num_threads=48 \
   --env.NM_BIND_THREADS_TO_CORES=1 \
   --target_qps=20480 \
   --offline_target_qps=20480
```

# BERT

## oBERT-Large 95% Pruned Quant Offline
```
cm run script --tags=run,mlperf,inference,generate-run-cmds,_submission,_all-modes,_full  \
   --adr.python.name=mlperf \
   --adr.python.version_min=3.8 \
   --adr.compiler.tags=gcc \
   --submitter=NeuralMagic \
   --implementation=reference \
   --compliance=no \
   --model=bert-99 \
   --precision=int8 \
   --backend=deepsparse \
   --hw_name=default \
   --device=cpu \
   --scenario=Offline \
   --mode=performance \
   --execution_mode=valid \
   --adr.mlperf-inference-implementation.max_batchsize=384 --target_qps=1280 --offline_target_qps=1280 \
   --adr.mlperf-inference-implementation.model=zoo:nlp/question_answering/obert-large/pytorch/huggingface/squad/pruned95_quant-none-vnni --env.NM_BIND_THREADS_TO_CORES=1
```

## MobileBERT SingleStream

```
cm run script --tags=run,mlperf,inference,generate-run-cmds,_submission,_all-modes,_full  \ 
   --adr.python.name=mlperf \
   --adr.python.version_min=3.8 \
   --adr.compiler.tags=gcc \
   --submitter=NeuralMagic \
   --implementation=reference \
   --compliance=no \
   --model=bert-99 \
   --precision=int8 \
   --backend=deepsparse \
   --hw_name=default \
   --device=cpu \
   --scenario=SingleStream \
   --mode=performance \
   --execution_mode=valid \
   --adr.mlperf-inference-implementation.max_batchsize=1 \
   --adr.mlperf-inference-implementation.model=/home/neuralmagic/models/mobilebert_latest.onnx --env.NM_BIND_THREADS_TO_CORES=1  --env.WAND_OPT_FLAGS=default,~pyramids --clean
```

## MobileBERT Offline

```
cm run script --tags=run,mlperf,inference,generate-run-cmds,_submission,_all-modes,_full  \
   --adr.python.name=mlperf \
   --adr.python.version_min=3.8 \
   --adr.compiler.tags=gcc \
   --submitter=NeuralMagic \
   --implementation=reference \
   --compliance=no \
   --model=bert-99 \
   --precision=int8 \
   --backend=deepsparse \
   --hw_name=default \
   --device=cpu \
   --scenario=Offline \
   --mode=performance \
   --execution_mode=valid \
   --adr.mlperf-inference-implementation.max_batchsize=384 --target_qps=5120 --offline_target_qps=5120 \
   --adr.mlperf-inference-implementation.model=/home/neuralmagic/models/mobilebert_latest.onnx --env.NM_BIND_THREADS_TO_CORES=1 --clean
```