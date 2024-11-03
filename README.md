# Minder Rules and Profiles Model Fine-tuning

This repository contains a Jupyter notebook for fine-tuning CodeLlama-7b to generate Minder rules and profiles. The model is trained to understand and generate YAML configurations following the Minder specification format.

## Requirements

- Python 3.8+
- PyTorch
- Transformers
- PEFT
- Datasets
- PyYAML
- Wandb (for tracking)
- CUDA-capable GPU with at least 16GB VRAM

## Setup

1. Install dependencies:
```bash
pip install transformers datasets peft torch pyyaml tqdm wandb
```

2. Clone the Minder rules repository:
```bash
git clone https://github.com/mindersec/minder-rules-and-profiles.git
```

3. Open and run the Jupyter notebook:
```bash
jupyter notebook fine_tune_minder.ipynb
```

## Model Architecture

The fine-tuning process uses:
- Base model: CodeLlama-7b
- Training method: LoRA (Low-Rank Adaptation)
- Quantization: 8-bit for efficiency
- Format: Alpaca instruction format

## Data Processing

The notebook handles:
1. YAML parsing of rules and profiles
2. Conversion to instruction format
3. Multiple instruction templates per example
4. Proper YAML structure preservation

## Training Process

The training includes:
- Proper prompt formatting
- Train/validation split
- Evaluation metrics
- Checkpointing
- WandB integration for monitoring

## Usage

After training, you can use the model to generate new rules or profiles:

```python
instruction = "Create a Minder rule for checking if repository has branch protection enabled"
generated_config = generate_minder_config(instruction, model, tokenizer)
print(generated_config)
```

## Model Capabilities

The fine-tuned model can:
1. Generate new Minder rules
2. Create Minder profiles
3. Understand security requirements
4. Output valid YAML configurations

## Performance Considerations

- Uses 8-bit quantization for reduced memory usage
- LoRA for efficient fine-tuning
- Batch size and gradient accumulation optimized for 16GB VRAM
- Evaluation steps for monitoring training progress

## License

This project is licensed under the same terms as the original Minder rules repository.
