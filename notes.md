# Some notes

### 2020.07.27

1. **posterior collapse**: where the latents are ignored when they are paired with a powerful autoregressive decoder — typically observed in the VAE framework, i.e., the latents are ignored as the decoder is powerful enough to model x perfectly.个人理解是某些VAE的decoder的重建能力过于好导致重建误差很小，最后模型不能很好的最小化prior相关的loss item。
