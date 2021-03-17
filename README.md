# Model_Param_Act_Count

For CV models (For now only support Imagenet classification!)
```
export CUDA_VISIBLE_DEVICES=0; python cv_main.py -a {resnet50} -b {64} --image-size {224}
```

For NLP Finetuning Task
```
TASK_NAME=mnli
export CUDA_VISIBLE_DEVICES=0; python nlp_finetuning_main.py \
  --model_name_or_path bert-base-cased \
  --task_name $TASK_NAME \
  --max_length 512 \
  --per_device_train_batch_size 2
```
Note the the "--pad_to_max_length" is usually not used in the training since it pads all sentence to the longest length. This makes the dataloader extremely large. Therefore, in the code, I mannually create a batch to satisfy our "--max_length" requirement (around line 410).