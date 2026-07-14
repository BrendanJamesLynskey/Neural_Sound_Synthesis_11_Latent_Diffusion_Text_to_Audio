# Neural Sound Synthesis · Part 11 — Latent Diffusion: Text-to-Audio

Part eleven of the [Neural Sound Synthesis](https://github.com/BrendanJamesLynskey/Neural_Sound_Synthesis) series. Runs the diffusion process not on raw audio but inside a compressed, learned VAE latent — the trick behind Riffusion, AudioLDM, and Stable Audio — and shows how a shared text–audio embedding (CLAP) plus classifier-free guidance turns a plain prompt into sound.

### [Launch App](https://brendanjameslynskey.github.io/Neural_Sound_Synthesis_11_Latent_Diffusion_Text_to_Audio/)

Part of the [DSP & Music](https://github.com/BrendanJamesLynskey/DSP_and_Music) collection.

---

## What's inside

| Section | Content |
|---------|---------|
| **The Idea** | Why move diffusion off the waveform — two-stage VAE + latent-diffusion, the latent-space objective, cross-attention conditioning, cost and quality trade-offs |
| **Spectrogram Diffusion** | Riffusion's image-domain trick, Griffin–Lim inversion, the reverse step derived — with a **live target-vs-noisy denoiser you can invert and play** |
| **The VAE Latent** | Why the latent is compact and smooth, why interpolation works — with a **live latent-walk morphing a decoded spectrogram between two codes** |
| **Text Conditioning** | CLAP contrastive pretraining (InfoNCE), the "language of audio", classifier-free guidance maths — with a **live joint-embedding map and a guidance slider** |
| **The Systems** | Riffusion · AudioLDM · AudioLDM 2 · Make-An-Audio · Tango · MusicLDM · Stable Audio (waveform latent, DiT, timing conditioning) |
| **Diffusion vs LM** | Non-AR latent diffusion vs the token-LM route of Part 10 — texture vs long structure, and the blurring line between them |
| **Timeline** | Latent diffusion for audio, 2022 → 2024 |

## Live demos (all synthesised in-browser, no audio files)

1. **Spectrogram-diffusion denoiser** — corrupts the spectrogram of a generated clip to noise, then runs a convergent oracle reverse-diffusion trajectory that clarifies it step by step; inverts the result with oracle phase and plays it. A steps slider trades quality for speed.
2. **CLAP text↔audio embedding map** — a 2-D joint space with four text/audio prompt pairs; pick a prompt and watch a generated sample get pulled toward it, with a classifier-free-guidance strength slider that drives the overshoot, plus a crude representative sound per prompt.
3. **Latent walk** — interpolates between two latent codes and decodes the spectrogram live along the path; scrub or auto-walk, and play either endpoint or the current point to hear the morph.

## Technology

Single-file HTML/CSS/JS · Web Audio API · HTML5 Canvas · KaTeX · Palatino + Lucida Console · No external dependencies · No build step
