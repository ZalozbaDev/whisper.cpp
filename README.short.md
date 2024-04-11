# short HOWTOs

## convert a fine-tuned model to GGML

need to install these python deps:

```bash
pip3 install torch
pip3 install numpy
pip3 install transformers
```

```bash
git clone https://github.com/openai/whisper
git clone https://github.com/ggerganov/whisper.cpp

# convert the model to ggml
python3 ./whisper.cpp/models/convert-h5-to-ggml.py ./path/to/your/fine/tuned/model/ ./whisper .
```

Examples:

```bash

python3 ./whisper.cpp/models/convert-h5-to-ggml.py ./whisper-base_hsb_2023_08_15/results-3000/ ./whisper .


git clone https://huggingface.co/openai/whisper-small

cp whisper-small/vocab.json hsb_stt_demo/hsb_whisper/
cp whisper-small/added_tokens.json hsb_stt_demo/hsb_whisper/

python3 ./whisper.cpp/models/convert-h5-to-ggml.py ./hsb_stt_demo/hsb_whisper/ ./whisper .
```

Script needs these additional files which are not part of a checkpoint, only generated with a complete run:

- vocab.json
- added_tokens.json


## quantize a model

```bash

# quantize a model with Q5_0 method
make quantize
./quantize ../ggml-model.bin ../ggml-model.q4_0.bin q4_0
./quantize ../ggml-model.bin ../ggml-model.q5_0.bin q5_0
./quantize ../ggml-model.bin ../ggml-model.q8_0.bin q8_0
```

TODO what is the best quantization for optimum performance?


