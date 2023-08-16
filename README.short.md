# short HOWTOs

## convert a fine-tuned model to GGML

```bash
git clone https://github.com/openai/whisper
git clone https://github.com/ggerganov/whisper.cpp

# convert the model to ggml
python3 ./whisper.cpp/models/convert-h5-to-ggml.py ./path/to/your/fine/tuned/model/ ./whisper .
```

Example:

```bash

python3 ./whisper.cpp/models/convert-h5-to-ggml.py ./whisper-base_hsb_2023_08_15/results-3000/ ./whisper .
```

## quantize a model

```bash

# quantize a model with Q5_0 method
make quantize
./quantize ../ggml-model.bin ../ggml-model.q5_0.bin q5_0
```

TODO what is the best quantization for optimum performance?


