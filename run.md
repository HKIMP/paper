yes/no
```shell
export SAVE_DIR=./output
export DATA_DIR=../datasets/QA/BioASQ
export OFFICIAL_DIR=./scripts/bioasq_eval

export BATCH_SIZE=12
export LEARNING_RATE=8e-6
export NUM_EPOCHS=3
export MAX_LENGTH=384
export SEED=0

# Train
python run_yesno.py \
    --model_type bert \
    --model_name_or_path dmis-lab/biobert-base-cased-v1.1 \
    --do_train \
    --train_file ${DATA_DIR}/BioASQ-train-yesno-7b.json \
    --per_gpu_train_batch_size ${BATCH_SIZE} \
    --learning_rate ${LEARNING_RATE} \
    --num_train_epochs ${NUM_EPOCHS} \
    --max_seq_length ${MAX_LENGTH} \
    --seed ${SEED} \
    --output_dir ${SAVE_DIR}

# Evaluation
python run_yesno.py \
    --model_type bert \
    --model_name_or_path ${SAVE_DIR} \
    --do_eval \
    --predict_file ${DATA_DIR}/BioASQ-test-yesno-7b.json \
    --golden_file ${DATA_DIR}/7B_golden.json \
    --per_gpu_train_batch_size ${BATCH_SIZE} \
    --official_eval_dir ${OFFICIAL_DIR} \
    --output_dir ${SAVE_DIR}
```

Factoid
```shell
export SAVE_DIR=./output
export DATA_DIR=../datasets/QA/BioASQ
export OFFICIAL_DIR=./scripts/bioasq_eval

export BATCH_SIZE=12
export LEARNING_RATE=8e-6
export NUM_EPOCHS=3
export MAX_LENGTH=384
export SEED=0

# Train
python run_factoid.py \
    --model_type bert \
    --model_name_or_path dmis-lab/biobert-base-cased-v1.1 \
    --do_train \
    --train_file ${DATA_DIR}/BioASQ-train-factoid-7b.json \
    --per_gpu_train_batch_size ${BATCH_SIZE} \
    --learning_rate ${LEARNING_RATE} \
    --num_train_epochs ${NUM_EPOCHS} \
    --max_seq_length ${MAX_LENGTH} \
    --seed ${SEED} \
    --output_dir ${SAVE_DIR}

# Evaluation
python run_factoid.py \
    --model_type bert \
    --model_name_or_path ${SAVE_DIR} \
    --do_eval \
    --predict_file ${DATA_DIR}/BioASQ-test-factoid-7b.json \
    --golden_file ${DATA_DIR}/7B_golden.json \
    --per_gpu_eval_batch_size ${BATCH_SIZE} \
    --max_seq_length ${MAX_LENGTH} \
    --seed ${SEED} \
    --official_eval_dir ${OFFICIAL_DIR} \
    --output_dir ${SAVE_DIR}
```