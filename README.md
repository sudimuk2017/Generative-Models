Foundations for Diffusion & Generative Models

0.1 Probability & Information Theory (Absolutely Required)

Concepts you must know
	•	Random variables & distributions
	•	Expectation, variance
	•	KL divergence
	•	Entropy & cross-entropy
	•	Change of variables (Jacobian)
	•	Gaussian distributions (very important)

Why this matters
	•	Diffusion training minimizes KL terms
	•	Noise addition & removal is Gaussian
	•	ELBO relies on information theory

Best resources

Kevin Murphy – Probabilistic Machine Learning: An Introduction
→ Chapters 2, 3, 4, 6
 https://probml.github.io/pml-book/book1.html

Bishop – Pattern Recognition and Machine Learning
→ Chapter 2 (Probability Distributions), Chapter 10 (Variational Inference)

Statistical Learning (Stanford – CS229 review)
 https://cs229.stanford.edu/section/cs229-prob.pdf

⸻

0.2 Variational Inference & Latent Variable Models (Critical)

Concepts
	•	Latent variables
	•	Marginal likelihood
	•	Evidence Lower Bound (ELBO)
	•	Approximate posteriors
	•	Reparameterization trick

Why this matters
	•	Diffusion can be derived as variational inference
	•	Latent Diffusion depends on VAEs
	•	Noise prediction loss = ELBO simplification

Best resources

Auto-Encoding Variational Bayes – Kingma & Welling
 https://arxiv.org/abs/1312.6114

Variational Inference – David Blei (Columbia)
 https://www.youtube.com/watch?v=DJWn6s6Yc1g

Murphy – Probabilistic ML (Advanced)
→ Chapter 21 (Variational Inference)

⸻

0.3 Stochastic Processes & Markov Chains (Required for Diffusion)

Concepts
	•	Markov chains
	•	Transition kernels
	•	Forward vs reverse processes
	•	Stationary distributions
	•	Time-reversal of stochastic processes

Why this matters
	•	Diffusion = Markov chain of noise
	•	Reverse diffusion is learned
	•	Sampling is reversing a stochastic process

Best resources

Introduction to Probability Models – Sheldon Ross
→ Markov Chains chapters

MIT 6.262 – Discrete Stochastic Processes
 https://ocw.mit.edu/courses/6-262-discrete-stochastic-processes-fall-2011/

Understanding Diffusion Models: A Unified Perspective
 https://arxiv.org/abs/2208.11970

⸻

0.4 Stochastic Differential Equations (SDEs) (Advanced but Important)

Concepts
	•	Brownian motion
	•	Wiener process
	•	Langevin dynamics
	•	Forward SDE
	•	Reverse-time SDE

Why this matters
	•	Modern diffusion is continuous-time
	•	Score-based models use SDEs
	•	Predictor–corrector samplers

Best resources

Stochastic Differential Equations – Bernt Øksendal
→ Chapters 1–5

Score-Based Generative Modeling (Yang Song lectures)
 https://www.youtube.com/watch?v=ZUZFqKoAI6Y

Score-Based Generative Modeling through SDEs
 https://arxiv.org/abs/2011.13456

⸻

0.5 Optimization & Neural Networks (Assumed but Important)

Concepts
	•	Backpropagation
	•	SGD, Adam
	•	Loss landscapes
	•	Overparameterization
	•	U-Nets

Why this matters
	•	Diffusion models are deep CNNs / Transformers
	•	Noise prediction = regression problem

Best resources

Deep Learning – Goodfellow, Bengio, Courville
→ Chapters 6–9

CS231n – Convolutional Neural Networks
https://cs231n.stanford.edu/

⸻

0.6 Linear Algebra (Quietly Crucial)

Concepts
	•	Eigenvalues & eigenvectors
	•	Matrix factorization
	•	Covariance matrices
	•	PCA (related to latent spaces)

Why this matters
	•	Gaussian noise covariance
	•	Latent compression
	•	Score estimation

Best resources

Linear Algebra and Learning from Data – Gilbert Strang
MIT 18.06 – Linear Algebra

⸻

Minimal “Foundation Track” (If You Want Efficiency)

If you want just enough to understand Stable Diffusion deeply:

Read / Watch in this order
	1.	Murphy (Prob ML) Chapters 2–4, 6
	2.	Kingma & Welling (VAE)
	3.	Blei – Variational Inference lecture
	4.	MIT Markov Chains notes
	5.	Yang Song SDE lecture
## Table 1: Depth Metrics Definition

| Metric | Full Name | Formula | Range | Better | Interpretation |
|--------|-----------|---------|-------|--------|----------------|
| **AbsRel** | Absolute Relative Error | $\frac{1}{N}\sum\frac{\|d_{pred}-d_{gt}\|}{d_{gt}}$ | [0, ∞) | ↓ Lower | Average relative error per pixel |
| **SqRel** | Squared Relative Error | $\frac{1}{N}\sum\frac{(d_{pred}-d_{gt})^2}{d_{gt}}$ | [0, ∞) | ↓ Lower | Penalizes large errors more |
| **RMSE** | Root Mean Squared Error | $\sqrt{\frac{1}{N}\sum(d_{pred}-d_{gt})^2}$ | [0, ∞) | ↓ Lower | Overall depth accuracy in absolute units |
| **RMSElog** | RMSE in log space | $\sqrt{\frac{1}{N}\sum(\log d_{pred}-\log d_{gt})^2}$ | [0, ∞) | ↓ Lower | Balances near/far error sensitivity |
| **SILog** | Scale-Invariant Log Error | $\sqrt{Var(\log d_{pred}-\log d_{gt})}$ | [0, ∞) | ↓ Lower | Scale-invariant accuracy metric |
| **δ < 1.25** | Threshold Accuracy 1 | $\%(\max(\frac{d_{pred}}{d_{gt}},\frac{d_{gt}}{d_{pred}}) < 1.25)$ | [0, 1] | ↑ Higher | % pixels within 25% error |
| **δ < 1.25²** | Threshold Accuracy 2 | $\%(\max(\frac{d_{pred}}{d_{gt}},\frac{d_{gt}}{d_{pred}}) < 1.5625)$ | [0, 1] | ↑ Higher | % pixels within 56% error |
| **δ < 1.25³** | Threshold Accuracy 3 | $\%(\max(\frac{d_{pred}}{d_{gt}},\frac{d_{gt}}{d_{pred}}) < 1.953)$ | [0, 1] | ↑ Higher | % pixels within 95% error |

