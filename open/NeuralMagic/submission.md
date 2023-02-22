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