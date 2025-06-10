GAN Image Generation Experiment: Reflection Report - Karina Shah
Introduction
What is a GAN and How Does It Work?
A Generative Adversarial Network (GAN) is a revolutionary deep learning architecture introduced by Ian Goodfellow in 2014. GANs consist of two neural networks competing against each other in a game-theoretic framework:
Generator (G): Creates fake data from random noise, attempting to fool the discriminator
Discriminator (D): Distinguishes between real and fake data, acting as a critic
The training process involves an adversarial game where the generator tries to create increasingly realistic fake data. The discriminator becomes better at detecting fake data. Through this competition, both networks improve until the generator produces highly realistic outputs. The mathematical foundation can be expressed as a minimax game: min_G max_D V(D,G) = E_x[log D(x)] + E_z[log(1 - D(G(z)))] where the generator minimizes loss while the discriminator maximizes it, leading to a point where generated samples become indistinguishable from real data.

Experiment Summary
For this experiment, I implemented a simplified GAN generator architecture using PyTorch, designed to demonstrate the core concepts of image generation from noise. While the assignment suggested using BigGAN, I created a unique generator to understand the underlying mechanics better: Input: 100-dimensional latent vector (random noise), Output: 64×64 RGB images, Architecture: Linear layer followed by transposed convolutions with batch normalization and LeakyReLU activations, and Final Activation: Tanh function to normalize outputs to [-1, 1] range. The generation process follows these steps: Noise Sampling: Generate some random vectors from a standard normal distribution, Feature Mapping: Transform the latent vector through my generator network, Upsampling: Use transposed convolutions to increase spatial resolution, and Normalization: Convert outputs for visualization.

Observations
Image 1-2 (Initial Generation):
The generated images show abstract patterns and color combinations. Visible noise patterns suggest the model is learning to transform random input into structured output. Color distribution appears relatively balanced across RGB channels. Spatial coherence varies, with some regions showing more organized patterns than others
Image 3-4 (Different Random Seeds):
Each unique random seed produces distinctly different visual outputs. Demonstrates the stochastic nature of the generation process. Some images show more coherent structures while others remain more abstract. Color palettes vary significantly between different seed values
Image 5 (Scaled Latent Vectors):
Scaling the latent vector by different factors (0.5x, 1.0x, 1.5x, 2.0x) produces noticeable changes in image intensity and contrast. Higher scaling factors tend to produce more saturated colors and pronounced features. Lower scaling factors result in more subdued, muted outputs. The relationship between scaling and output characteristics appears non-linear
Impact of Latent Vector Modifications
Smooth interpolation between two latent vectors creates a gradual transition between generated images
This demonstrates the continuous nature of the learned latent space
Intermediate images maintain visual coherence while showing progressive changes
Suggests the generator has learned meaningful representations in the latent space
Pixel values are properly normalized to [0, 1] range
Mean pixel values around 0.5 indicate balanced brightness
Standard deviation values suggest appropriate contrast levels
RGB channels show relatively balanced distributions

Reflection
Key Learnings About GAN Image Generation
This experiment provided several important insights into how GANs generate images. Deterministic Generation: Given the same latent vector, the generator produces identical outputs, demonstrating the deterministic nature of the forward pass while maintaining stochastic diversity through different input vectors, Feature Hierarchy: The upsampling architecture allows the generator to build images from coarse to fine details, similar to how human artists might approach image creation, Random Noise as Creative Input: The transformation of pure random noise into structured visual content illustrates the remarkable capability of neural networks to learn complex mappings.


Limitations and Challenges Observed
Technical Limitations:
Model Simplicity: The simplified architecture used in this experiment generates abstract patterns rather than photorealistic images
Training Requirements: Achieving high-quality results requires extensive training on large datasets with powerful hardware
Mode Collapse Risk: While not observed in this experiment, GANs are susceptible to generating limited varieties of outputs
Practical Challenges:
Computational Resources: Running larger, more sophisticated models like BigGAN requires significant GPU memory and processing power
Evaluation Metrics: Assessing the quality of generated images remains subjective without formal metrics like FID or IS scores
Hyperparameter Sensitivity: The quality of generated images heavily depends on proper hyperparameter tuning
Potential Improvements
Evaluation Methods:
Integrate quantitative metrics for objective quality assessment
Conduct user studies for perceptual quality evaluation
Implement diversity measurements to ensure a more varied generation

