# Install Steps

```bash
sudo pacman -S ollama
```

# Infrastructure

```bash
ollama serve
```

# Model Setup Steps

```bash
yay -S git-lfs

git clone https://huggingface.co/NousResearch/Nous-Hermes-2-SOLAR-10.7B
cd Nous-Hermes-2-SOLAR-10.7B
# Download actual files
git lfs pull
# Or one-by-one as bandwidth allows:
# git lfs pull --include model-00001-of-00005.safetensors

# See docs at https://github.com/ollama/ollama/blob/main/docs/import.md#Importing-a-model-from-Safetensors-weights
cat > Modelfile <<< 'FROM .'

# "Nous-Hermes-2-SOLAR-10.7B" may be any identifier
ollama create Nous-Hermes-2-SOLAR-10.7B
# To optimize weights (super expensive 1-time step) pass --quantize w/ the packed size
#ollama create --quantize q4_K_M Nous-Hermes-2-SOLAR-10.7B

ollama run Nous-Hermes-2-SOLAR-10.7B

```

Other models tested
```bash
ollama run qwen2     # 7b
ollama run solar-pro # 22b
ollama run phi3:14b  # 24b

```
