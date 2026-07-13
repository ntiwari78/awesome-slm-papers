# Awesome SLM Papers 🐜⚡

> **Small Language Models are eating the edge.** A hand-curated, battle-tested reading list of 140+ papers on Small Language Models: pre-training, fine-tuning, distillation, quantization, on-device deployment, and the Indic language revolution. Organized by year so you can watch the field grow up in real time.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![License: CC0](https://img.shields.io/badge/License-CC0-blue.svg)](LICENSE)
![Papers](https://img.shields.io/badge/papers-140%2B-orange)
![Last Updated](https://img.shields.io/badge/updated-July%202026-purple)

**Why this list exists:** GPT-4 needs a data center. A 3B model needs a $150 phone. If you believe the next billion AI users will run models locally, in their own language, on hardware they already own, this list is your map. Every paper here was read, verified, and placed on the timeline where it actually landed.

**Who this is for:** researchers shipping on-device AI, engineers quantizing models for edge hardware, founders building for low-resource languages, and students who want the full SLM story from n-grams to Gemma 4.

---

## Contents

- [⭐ Start Here: The 10 Papers That Define SLMs](#-start-here-the-10-papers-that-define-slms)
- [🏛️ Pre-2022: The Foundations](#%EF%B8%8F-pre-2022-the-foundations)
- [📅 2022: Scaling Laws Change Everything](#-2022-scaling-laws-change-everything)
- [📅 2023: Small Gets Serious](#-2023-small-gets-serious)
- [📅 2024: On-Device Goes Mainstream](#-2024-on-device-goes-mainstream)
- [📅 2025: The Rise of Small Reasoners](#-2025-the-rise-of-small-reasoners)
- [📅 2026: The Edge Era](#-2026-the-edge-era)
- [🇮🇳 The Indic SLM Index](#-the-indic-slm-index)
- [🤝 Contributing](#-contributing)
- [📖 Citation](#-citation)

**Legend:** `model` new model release · `peft` parameter-efficient fine-tuning · `distill` distillation and reasoning transfer · `quant` quantization and inference · `data` datasets and benchmarks · `domain` vertical/domain-specific · `indic` Indian languages · `survey` surveys and guides

---

## ⭐ Start Here: The 10 Papers That Define SLMs

If you read nothing else, read these. They are the load-bearing walls of the field.

| # | Paper | Why it matters |
|---|-------|----------------|
| 1 | [Distilling the Knowledge in a Neural Network](https://arxiv.org/abs/1503.02531) (2015) | Hinton's original distillation paper. Everything small starts here. |
| 2 | [LoRA: Low-Rank Adaptation](https://arxiv.org/abs/2106.09685) (2021) | Made fine-tuning affordable. Arguably the most deployed idea in applied LLMs. |
| 3 | [Training Compute-Optimal LLMs (Chinchilla)](https://arxiv.org/abs/2203.15556) (2022) | Proved smaller models trained longer beat bigger models trained less. The SLM thesis in one paper. |
| 4 | [Textbooks Are All You Need (Phi-1)](https://arxiv.org/abs/2306.11644) (2023) | Data quality beats parameter count. Kicked off the entire Phi lineage. |
| 5 | [QLoRA](https://arxiv.org/abs/2305.14314) (2023) | Fine-tune a quantized model on a single GPU. Democratized the whole game. |
| 6 | [Mistral 7B](https://arxiv.org/abs/2310.06825) (2023) | The moment a 7B model embarrassed 13B and 34B models in production. |
| 7 | [Phi-3: A Capable LM Locally on Your Phone](https://arxiv.org/abs/2404.14219) (2024) | GPT-3.5-class quality running natively on a smartphone. |
| 8 | [MobileLLM](https://arxiv.org/abs/2402.14905) (2024) | Meta's blueprint for sub-billion-parameter architecture design. |
| 9 | [DeepSeek-R1](https://doi.org/10.1038/s41586-025-09422-z) (2025, Nature) | RL-incentivized reasoning, and the distilled small variants that shocked everyone. |
| 10 | [LIMO: Less Is More for Reasoning](https://arxiv.org/abs/2502.03387) (2025) | 817 curated examples unlock complex reasoning. Curation is the new scale. |

---

## 🏛️ Pre-2022: The Foundations

*Before "SLM" was a term, decades of work on compact language modeling made it inevitable.*

### Statistical and Neural Roots
- **[Estimation of Probabilities from Sparse Data (Katz Smoothing)](https://ieeexplore.ieee.org/document/479394)** - Katz, IEEE TASSP 1987 · `data`
- **[Improved Backing-Off for M-gram Language Modeling (Kneser-Ney)](https://ieeexplore.ieee.org/document/479394)** - Kneser & Ney, ICASSP 1995 · `data`
- **[Long Short-Term Memory](https://doi.org/10.1162/neco.1997.9.8.1735)** - Hochreiter & Schmidhuber, Neural Computation 1997 · `model`
- **[Recurrent Neural Network Based Language Model](https://www.isca-archive.org/interspeech_2010/mikolov10_interspeech.html)** - Mikolov et al., Interspeech 2010 · `model`

### Compression and Tokenization
- **[Distilling the Knowledge in a Neural Network](https://arxiv.org/abs/1503.02531)** - Hinton, Vinyals & Dean, 2015 · `distill` ⭐
- **[Neural MT of Rare Words with Subword Units (BPE)](https://aclanthology.org/P16-1162/)** - Sennrich et al., ACL 2016 · `data`
- **[Google's Neural Machine Translation System](https://arxiv.org/abs/1609.08144)** - Wu et al., 2016 · `model`
- **[Using the Output Embedding to Improve Language Models](https://aclanthology.org/E17-2025/)** - Press & Wolf, EACL 2017 · `peft`
- **[Tying Word Vectors and Word Classifiers](https://arxiv.org/abs/1611.01462)** - Inan et al., ICLR 2017 · `peft`
- **[SentencePiece](https://aclanthology.org/D18-2012/)** - Kudo & Richardson, EMNLP 2018 · `data`

### The Transformer Generation
- **[BERT](https://aclanthology.org/N19-1423/)** - Devlin et al., NAACL 2019 · `model`
- **[GPT-2: Language Models are Unsupervised Multitask Learners](https://cdn.openai.com/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)** - Radford et al., OpenAI 2019 · `model`
- **[DistilBERT](https://arxiv.org/abs/1910.01108)** - Sanh et al., 2019 · `distill` — 40% smaller, 97% of BERT's performance. The proof of concept.
- **[ALBERT: A Lite BERT](https://arxiv.org/abs/1909.11942)** - Lan et al., ICLR 2020 · `model`
- **[TinyBERT](https://aclanthology.org/2020.findings-emnlp.372/)** - Jiao et al., Findings of EMNLP 2020 · `distill`
- **[MobileBERT](https://aclanthology.org/2020.acl-main.195/)** - Sun et al., ACL 2020 · `model` — compact BERT for resource-limited devices, years ahead of its time.
- **[GPT-3: Language Models are Few-Shot Learners](https://arxiv.org/abs/2005.14165)** - Brown et al., 2020 · `model`
- **[GPT-J-6B](https://github.com/kingoflolz/mesh-transformer-jax)** - Wang & Komatsuzaki, 2021 · `model`
- **[MuRIL: Multilingual Representations for Indian Languages](https://arxiv.org/abs/2103.10730)** - Khanuja et al., 2021 · `indic`
- **[LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685)** - Hu et al., 2021 · `peft` ⭐

---

## 📅 2022: Scaling Laws Change Everything

*Chinchilla flipped the script: compute-optimal means smaller and longer-trained. Meanwhile instruction tuning and PEFT quietly built the toolkit SLMs would need.*

### The Turning Point
- **[Training Compute-Optimal Large Language Models (Chinchilla)](https://arxiv.org/abs/2203.15556)** - Hoffmann et al., DeepMind · `model` ⭐
- **[On the Opportunities and Risks of Foundation Models](https://arxiv.org/abs/2108.07258)** - Bommasani et al., Stanford · `survey`

### Open Models
- **[OPT: Open Pre-trained Transformer Language Models](https://arxiv.org/abs/2205.01068)** - Zhang et al., Meta · `model`
- **[BLOOM: A 176B Open-Access Multilingual LM](https://arxiv.org/abs/2211.05100)** - BigScience Workshop · `model`
- **[GPT-NeoX-20B](https://arxiv.org/abs/2204.06745)** - Black et al., EleutherAI · `model`
- **[PaLM: Scaling Language Modeling with Pathways](http://jmlr.org/papers/v24/22-1144.html)** - Chowdhery et al., Google (JMLR 2023) · `model`
- **[Galactica: A Large Language Model for Science](https://arxiv.org/abs/2211.09085)** - Taylor et al., Meta · `domain`

### Instruction Tuning Arrives
- **[Training LMs to Follow Instructions with Human Feedback (InstructGPT)](https://proceedings.neurips.cc/paper_files/paper/2022/file/b1efde53be364a73914f58805a001731-Paper-Conference.pdf)** - Ouyang et al., NeurIPS · `model`
- **[Scaling Instruction-Finetuned Language Models (Flan-T5)](https://arxiv.org/abs/2210.11416)** - Chung et al., Google · `model`
- **[Super-NaturalInstructions: 1600+ NLP Tasks](https://arxiv.org/abs/2204.07705)** - Wang et al. · `data`

### PEFT and Infrastructure
- **[BitFit: Bias-Only Fine-tuning](https://arxiv.org/abs/2106.10199)** - Ben-Zaken et al. · `peft`
- **[P-Tuning v2](https://arxiv.org/abs/2110.07602)** - Liu et al. · `peft`
- **[FlashAttention](https://arxiv.org/abs/2205.14135)** - Dao et al. · `quant`
- **[TRL: Transformer Reinforcement Learning](https://github.com/huggingface/trl)** - von Werra et al., Hugging Face · `peft`
- **[Fine-Tuning LMs via Epistemic Neural Networks](https://arxiv.org/abs/2211.01568)** - Osband et al. · `peft`
- **[Large Language Models Are Reasoning Teachers (Fine-tune-CoT)](https://arxiv.org/abs/2212.10071)** - Ho et al. · `distill`

### Early Indic Encoders
- **[IndicBERT](https://huggingface.co/ai4bharat/indic-bert)** - Kakwani et al., AI4Bharat · `indic`
- **[IndicBART](https://aclanthology.org/2022.findings-acl.145)** - Dabre et al., AI4Bharat · `indic`

---

## 📅 2023: Small Gets Serious

*The explosion. Phi proved data quality beats size, QLoRA put fine-tuning on consumer GPUs, Mistral 7B beat models 5x its size, and reasoning distillation became a research industry.*

### The Phi Revolution and Compact Models
- **[Textbooks Are All You Need (Phi-1)](https://arxiv.org/abs/2306.11644)** - Gunasekar et al., Microsoft · `model` ⭐
- **[Textbooks Are All You Need II (Phi-1.5)](https://arxiv.org/abs/2309.05463)** - Li et al., Microsoft · `model`
- **[Phi-2: The Surprising Power of Small Language Models](https://www.microsoft.com/en-us/research/blog/phi-2-the-surprising-power-of-small-language-models/)** - Javaheripi et al., Microsoft · `model`
- **[Mistral 7B](https://arxiv.org/abs/2310.06825)** - Jiang et al., Mistral AI · `model` ⭐
- **[Llama 2: Open Foundation and Fine-Tuned Chat Models](https://arxiv.org/abs/2307.09288)** - Touvron et al., Meta · `model`
- **[Pythia: Analyzing LLMs Across Training and Scaling](https://arxiv.org/abs/2304.01373)** - Biderman et al., EleutherAI · `model`
- **[MindLLM: Pre-training Lightweight LLMs from Scratch](https://arxiv.org/abs/2310.15777)** - Yang et al. · `model`
- **[Baby Llama: KD from an Ensemble of Teachers](https://arxiv.org/abs/2308.02019)** - Timiryasov & Tastet · `distill`
- **[Exploring the Limits of Small Language Models](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2023/EECS-2023-141.pdf)** - Lee et al., UC Berkeley · `survey`
- **[GPT-4 Technical Report](https://arxiv.org/abs/2303.08774)** - OpenAI · `model` — the giant everyone wanted to distill.
- **[Mamba: Linear-Time Sequence Modeling](https://arxiv.org/abs/2312.00752)** - Gu & Dao · `model` — the strongest post-transformer candidate for edge inference.

### Instruction Tuning Goes Open
- **[Stanford Alpaca](https://crfm.stanford.edu/2023/03/13/alpaca.html)** - Taori et al. · `data`
- **[Vicuna](https://lmsys.org/blog/2023-03-30-vicuna/)** - Chiang et al., LMSYS · `model`
- **[LIMA: Less Is More for Alignment](https://arxiv.org/abs/2305.11206)** - Zhou et al., Meta · `data`
- **[Zephyr: Direct Distillation of LM Alignment](https://arxiv.org/abs/2310.16944)** - Tunstall et al., Hugging Face · `distill`
- **[WizardLM: Evol-Instruct](https://arxiv.org/abs/2304.12244)** - Xu et al. · `data`
- **[WizardMath: Reinforced Evol-Instruct](https://arxiv.org/abs/2308.09583)** - Luo et al. · `distill`
- **[MetaMath: Bootstrap Your Own Math Questions](https://arxiv.org/abs/2309.12284)** - Yu et al. · `data`
- **[How Far Can Camels Go? (Tülu)](https://arxiv.org/abs/2306.04751)** - Wang et al., AI2 · `data`
- **[Platypus: Quick, Cheap, and Powerful Refinement](https://arxiv.org/abs/2308.07317)** - Lee et al. · `peft`
- **[ToolLLM: Mastering 16000+ Real-World APIs](https://arxiv.org/abs/2307.16789)** - Qin et al. · `data`
- **[Direct Preference Optimization (DPO)](https://arxiv.org/abs/2305.18290)** - Rafailov et al., Stanford · `peft` — killed the reward model, saved the GPU bill.

### Teaching Small Models to Reason
- **[Distilling Step-by-Step!](https://arxiv.org/abs/2305.02301)** - Hsieh et al., Google · `distill`
- **[Specializing Smaller LMs towards Multi-Step Reasoning](https://arxiv.org/abs/2301.12726)** - Fu et al. · `distill`
- **[Teaching Small Language Models to Reason](https://aclanthology.org/2023.acl-short.151)** - Magister et al., ACL · `distill`
- **[SCOTT: Self-Consistent Chain-of-Thought Distillation](https://aclanthology.org/2023.acl-long.304)** - Wang et al., ACL · `distill`
- **[Symbolic Chain-of-Thought Distillation (SCoTD)](https://arxiv.org/abs/2306.14050)** - Li et al. · `distill`
- **[Orca: Learning from Complex Explanation Traces of GPT-4](https://arxiv.org/abs/2306.02707)** - Mukherjee et al., Microsoft · `distill`
- **[Orca 2: Teaching Small LMs How to Reason](https://arxiv.org/abs/2311.11045)** - Mitra et al., Microsoft · `distill`
- **[Small LMs Fine-tuned to Coordinate Larger LMs (DaSLaM)](https://arxiv.org/abs/2310.18338)** - Juneja et al. · `distill`

### Fine-tuning and Inference Machinery
- **[QLoRA: Efficient Finetuning of Quantized LLMs](https://arxiv.org/abs/2305.14314)** - Dettmers et al. · `peft` `quant` ⭐
- **[LongLoRA: Long-Context Fine-tuning](https://arxiv.org/abs/2309.12307)** - Chen et al. · `peft`
- **[GPTQ: Accurate Post-Training Quantization](https://arxiv.org/abs/2210.17323)** - Frantar et al. · `quant`
- **[AWQ: Activation-aware Weight Quantization](https://arxiv.org/abs/2306.00978)** - Lin et al., MIT · `quant`
- **[PagedAttention (vLLM)](https://arxiv.org/abs/2309.06180)** - Kwon et al., UC Berkeley · `quant`
- **[Speculative Decoding](https://arxiv.org/abs/2211.17192)** - Leviathan et al., Google · `quant`

### Domain Verticals Emerge
- **[PMC-LLaMA: Open-Source LMs for Medicine](https://arxiv.org/abs/2304.14454)** - Wu et al. · `domain`
- **[MedAlpaca: Medical Conversational AI](https://arxiv.org/abs/2304.08247)** - Han et al. · `domain`
- **[Lawyer LLaMA](https://arxiv.org/abs/2305.15062)** - Huang et al. · `domain`
- **[DISC-LawLLM: Intelligent Legal Services](https://arxiv.org/abs/2309.11325)** - Yue et al. · `domain`

### Indic Firsts
- **[OpenHathi-Hi-v0.1: First Open Hindi Foundation Model](https://huggingface.co/sarvamai/OpenHathi-7B-Hi-v0.1-Base)** - Sarvam AI & AI4Bharat · `indic` `model`
- **[Tamil-Llama](https://arxiv.org/abs/2311.05845)** - Balachandran · `indic` `model`

---

## 📅 2024: On-Device Goes Mainstream

*Phones became first-class inference targets. Every major lab shipped a sub-4B model, PEFT matured beyond LoRA, and the Indic ecosystem went from two models to twenty.*

### Flagship Small Models
- **[Phi-3: A Highly Capable LM Locally on Your Phone](https://arxiv.org/abs/2404.14219)** - Abdin et al., Microsoft · `model` ⭐
- **[Phi-4 Technical Report](https://arxiv.org/abs/2412.08905)** - Abdin et al., Microsoft · `model`
- **[MobileLLM: Optimizing Sub-Billion Parameter Models](https://arxiv.org/abs/2402.14905)** - Liu et al., Meta · `model` ⭐
- **[TinyLlama: An Open-Source Small Language Model](https://arxiv.org/abs/2401.02385)** - Zhang et al. · `model`
- **[Gemma 2: Open Models at a Practical Size](https://arxiv.org/abs/2408.00118)** - Gemma Team, Google · `model`
- **[Llama 3.2: Lightweight and Multimodal (1B/3B)](https://ai.meta.com/blog/llama-3-2-connect-2024/)** - Meta AI · `model`
- **[Qwen2 Technical Report](https://arxiv.org/abs/2407.10671)** - Yang et al., Alibaba · `model`
- **[Qwen2.5 Technical Report](https://arxiv.org/abs/2412.15115)** - Qwen Team, Alibaba · `model`
- **[MiniCPM: Scalable Training Strategies for SLMs](https://arxiv.org/abs/2404.06395)** - Hu et al., OpenBMB · `model`
- **[OpenELM: Efficient LM Family with Open Training](https://arxiv.org/abs/2404.14619)** - Mehta et al., Apple · `model`
- **[Stable LM 2 1.6B](https://arxiv.org/abs/2402.17834)** - Bellagente et al., Stability AI · `model`

### PEFT Levels Up
- **[DoRA: Weight-Decomposed Low-Rank Adaptation](https://arxiv.org/abs/2402.09353)** - Liu et al., NVIDIA · `peft`
- **[ReFT: Representation Finetuning](https://arxiv.org/abs/2404.03592)** - Wu et al., Stanford · `peft`
- **[MiLoRA: Minor Singular Components for PEFT](https://arxiv.org/abs/2406.09044)** - Wang et al. · `peft`
- **[Semantic Knowledge Tuning](https://doi.org/10.1038/s41598-024-75599-4)** - Prottasha et al., Scientific Reports · `peft`
- **[Fine-tuning LLMs with Limited Data: A Practical Guide](https://arxiv.org/abs/2411.09539)** - Szep et al. · `survey`

### Reasoning, Reliability, Applications
- **[Self-Refine Instruction-Tuning](https://aclanthology.org/2024.emnlp-main.139)** - Ranaldi & Freitas, EMNLP · `distill`
- **[Solution Guidance Fine-Tuning (SGFT)](https://arxiv.org/abs/2412.09906)** - Bi et al. · `distill`
- **[Honest AI: Fine-Tuning SLMs to Say "I Don't Know"](https://arxiv.org/abs/2410.09699)** - Chen et al. · `domain`
- **[Tiny Titans: SLMs for Meeting Summarization](https://arxiv.org/abs/2402.00841)** - Fu et al. · `domain`
- **[Fine-tuning SLMs for Financial Document QA](https://arxiv.org/abs/2408.12337)** - Phogat et al. · `domain`
- **[Birbal: Efficient 7B Instruct with Curated Data](https://arxiv.org/abs/2403.02247)** - Jindal et al. · `data` — NeurIPS LLM Efficiency Challenge winner, built in India.
- **[The Effect of Fine-tuning on LM Toxicity](https://arxiv.org/abs/2410.15821)** - Hawkins et al., Oxford · `survey` — a warning: fine-tuning can silently undo safety training.

### Indic Ecosystem Explosion
- **[Airavata: Hindi Instruction-tuned LLM](https://arxiv.org/abs/2401.15006)** - Gala et al., AI4Bharat · `indic`
- **[Sarvam-2B](https://www.marktechpost.com/2024/08/14/sarvamai-releases-samvaad-hi-v1-dataset-and-sarvam-2b-a-2-billion-parameter-language-model-with-4-trillion-tokens-focused-on-10-indic-languages-for-enhanced-nlp/)** and **[Sarvam-1](https://huggingface.co/sarvamai/sarvam-1)** - Sarvam AI · `indic` `model`
- **[Nemotron-4-Mini-Hindi-4B / Indus 2.0](https://blogs.nvidia.com/blog/nemotron-mini-hindi-tech-mahindra/)** - NVIDIA & Tech Mahindra · `indic`
- **[Navarasa 2.0: Gemma Fine-tuned on 15 Indian Languages](https://huggingface.co/Telugu-LLM-Labs/Indic-gemma-2b-finetuned-sft-Navarasa-2.0)** - Telugu-LLM-Labs · `indic`
- **[SUTRA: Dual-Transformer Multilingual Family](https://www.two.ai/sutra)** - TWO AI · `indic` `model`
- **[BharatGen / e-vikrAI](https://bharatgen.com/)** - IIT Bombay-led consortium · `indic`
- **[IndicLLMSuite: Blueprint for Indic Pre-training and Fine-tuning Data](http://dx.doi.org/10.18653/v1/2024.acl-long.843)** - Khan et al., ACL · `indic` `data`
- **[IndicGenBench](https://arxiv.org/abs/2404.16816)** - Singh et al., Google · `indic` `data`
- **[Gajendra-v0.1](https://huggingface.co/BhabhaAI/Gajendra-v0.1)** · **[Open Aditi v4](https://huggingface.co/manishiitg/open-aditi-hi-v4)** · **[Tamil-LLaMA v0.2 + Telugu + Malayalam](https://abhinand05.medium.com/breaking-language-barriers-introducing-tamil-llama-v0-2-and-its-expansion-to-telugu-and-malayalam-deb5d23e9264)** · **[MahaMarathi-7B](https://huggingface.co/marathi-llm/MahaMarathi-7B-v24.01-Base)** · **[OdiaGenAI](https://www.odiagenai.org/)** · **[Kan-LLaMA](https://huggingface.co/Tensoic/Kan-Llama-7B)** - community fine-tunes · `indic`
- **[IndicVarna-100K](https://huggingface.co/datasets/dynopii/IndicVarna-100k)** · **[IndicDialogue](https://www.sciencedirect.com/science/article/pii/S2352340924006577)** - instruction and dialogue datasets · `indic` `data`
- **[OpenHathi Fine-Tuning via QLoRA on Colab](https://xcelore.com/blog/openhathi-fine-tuning-hindi-llm-with-qlora-on-google-colab/)** - Xcelore · `indic` `peft`

### Surveys
- **[A Survey of Small Language Models](https://arxiv.org/abs/2410.20011)** - Nguyen et al. · `survey`
- **[Small Language Models: Survey, Measurements, and Insights](https://arxiv.org/abs/2409.15790)** - Lu et al. · `survey`

---

## 📅 2025: The Rise of Small Reasoners

*R1 changed the question from "how big" to "how trained." Reasoning distillation hit sub-4B models, quantization-aware pipelines matured, and Indic models got RLVR.*

### Reasoning Breaks Open
- **[DeepSeek-R1: RL-Incentivized Reasoning](https://doi.org/10.1038/s41586-025-09422-z)** - Guo et al., Nature · `model` `distill` ⭐
- **[LIMO: Less Is More for Reasoning](https://arxiv.org/abs/2502.03387)** - Ye et al. · `data` ⭐
- **[Phi-4-Reasoning](https://arxiv.org/abs/2504.21318)** and **[Phi-4-Mini-Reasoning](https://arxiv.org/abs/2504.21233)** - Microsoft · `model` `distill`
- **[Distill Not Only Data but Also Rewards](https://arxiv.org/abs/2502.19557)** - Zhang et al. · `distill`
- **[Neural-Symbolic Collaborative Distillation](https://ojs.aaai.org/index.php/AAAI/article/view/34636/36791)** - Liao et al., AAAI · `distill`
- **[Reasoning Scaffolding: Distilling the Flow of Thought](https://arxiv.org/abs/2509.23619)** - Wen et al. · `distill`
- **[Unveiling the Secret Recipe: SFT for Small LLMs](https://openreview.net/forum?id=eENHKMTOfW)** - Pareja et al., ICLR · `peft` — the empirical playbook for fine-tuning 3B-7B models.
- **[PiFi: Plug-in and Fine-tuning](https://aclanthology.org/2025.acl-long.271)** - Kim et al., ACL · `peft`

### Model Releases
- **[Gemma 3 Technical Report](https://arxiv.org/abs/2503.19786)** - Google DeepMind · `model`
- **[Qwen3 Technical Report](https://arxiv.org/abs/2505.09388)** - Alibaba · `model`
- **[Phi-4-Mini: Mixture-of-LoRAs Multimodal](https://arxiv.org/abs/2503.01743)** - Microsoft · `model`
- **[Llama 4 Herd: Scout and Maverick](https://ai.meta.com/blog/llama-4-multimodal-intelligence/)** - Meta AI · `model`
- **[SHAKTI: 2.5B SLM for Edge AI and Low-Resource Environments](https://arxiv.org/abs/2410.11331)** - Shakhadri et al. · `model` — built in India for edge-first deployment.
- **[HY-MT1.5 Technical Report](https://arxiv.org/abs/2512.24092)** - Zheng et al., Tencent · `model`

### Edge Deployment and Evaluation
- **[Fine-Tuning SLMs for Domain-Specific AI: An Edge AI Perspective](https://arxiv.org/abs/2503.01933)** - Aralimatti et al. · `domain`
- **[TinyLLM: Evaluating SLMs for Agentic Tasks on Edge Devices](https://arxiv.org/abs/2511.22138)** - Haque et al. · `data`
- **[SLM-Bench: Benchmarking SLMs on Environmental Impact](https://arxiv.org/abs/2508.15478)** - Pham et al. · `data`
- **[SLMs for Efficient Agentic Tool Calling](https://arxiv.org/abs/2512.15943)** - Jhandi et al., AWS · `distill` — targeted fine-tunes beating much larger generalists.

### Medical and Applied Verticals
- **[MedGemma Technical Report](https://arxiv.org/abs/2507.05201)** - Sellergren et al., Google · `domain` `model`
- **[Meerkat: SLMs Learn Reasoning from Medical Textbooks](https://doi.org/10.1038/s41746-025-01653-8)** - Kim et al., npj Digital Medicine · `domain`
- **[Me-LLaMA: Medical Foundation LLMs](https://doi.org/10.1038/s41746-025-01533-1)** - Xie et al., npj Digital Medicine · `domain`
- **[Fine-Tuning MedGemma for Clinical Captioning (Malaysia CPGs)](https://arxiv.org/abs/2510.15418)** - Lee et al. · `domain`
- **[The Economics of Accuracy for Medical Reasoning](https://www.medrxiv.org/content/early/2025/12/26/2025.12.22.25342804)** - Bhattacharyya, medRxiv · `domain` — when is the small model actually cheaper per correct answer?
- **[Fine-Tuned SLM for Private CWE Detection in Python](http://dx.doi.org/10.1109/ICCIT68739.2025.11491733)** - Bappy et al., IEEE ICCIT · `domain`
- **[Fine-Tuning LLMs for Specialized Use Cases](https://doi.org/10.1016/j.mcpdig.2024.11.005)** - Anisuzzaman et al., Mayo Clinic Proceedings: Digital Health · `survey`

### Indic Momentum
- **[Sarvam-M: Hybrid Reasoning Indic LLM (SFT + RLVR)](https://www.sarvam.ai/blogs/sarvam-m)** - Sarvam AI · `indic` `model`
- **[Krutrim LLM: Multilingual Foundation for a Billion People](https://arxiv.org/abs/2502.09642)** - Kallappa et al. · `indic` `model`
- **[Krutrim-2: 12B Indic LLM](https://tech.olakrutrim.com/krutrim-2-a-best-in-class-large-language-model-for-indic-languages/)** - Krutrim AI Labs · `indic`
- **[Mantra-14B: Hindi-English Bilingual](https://huggingface.co/soketlabs/bhasha-14b-base)** - Soket Labs · `indic`
- **[Efficient Continual Pre-training for Low-Resource Indic Languages](https://aclanthology.org/2025.naacl-industry.25.pdf)** - Nag et al., NAACL Industry · `indic` `peft`
- **[Analysis of Indic Language Capabilities in LLMs](https://arxiv.org/abs/2501.13912)** - Vaidya et al. · `indic` `data`
- **[IndicMMLU-Pro](https://arxiv.org/abs/2501.15747)** - Sankalp et al. · `indic` `data`
- **[IndicParam: Benchmark for Low-Resource Indic Languages](https://arxiv.org/abs/2512.00333)** - Maheshwari et al. · `indic` `data`
- **[From Phonemes to Meaning: Evaluating LLMs on Tamil](https://arxiv.org/abs/2511.12387)** - Varsha et al. · `indic` `data`

### Surveys and Guides
- **[State of the Art and Future Directions of SLMs: A Systematic Review](https://www.mdpi.com/2504-2289/9/7/189)** - Corradini et al., BDCC · `survey`
- **[PEFT in LLMs: A Survey of Methodologies](https://doi.org/10.1007/s10462-025-11236-4)** - Wang et al., Artificial Intelligence Review · `survey`
- **[A Survey on LoRA of LLMs](https://doi.org/10.1007/s11704-024-40663-9)** - Mao et al., Frontiers of Computer Science · `survey`
- **[Knowledge Distillation and Dataset Distillation of LLMs](https://doi.org/10.1007/s10462-025-11423-3)** - Fang et al., AI Review · `survey`
- **[A Systematic Literature Review of PEFT for Large Code Models](https://arxiv.org/abs/2504.21569)** - Afrin et al. · `survey`
- **[PEFT of SLMs for Code Generation: Gemma vs Qwen 2.5 vs Llama 3.2](https://www.researchgate.net/publication/400327943)** - Nguyen et al., IJECE · `survey`
- **[PEFT for Low-Resource Text Classification: LoRA vs IA3 vs ReFT](https://www.frontiersin.org/journals/big-data/articles/10.3389/fdata.2025.1677331/full)** - Nwaiwu, Frontiers in Big Data · `survey`
- **[Evolution of Meta's Llama Models and PEFT: A Survey](https://arxiv.org/abs/2510.12178)** - Abdullah et al. · `survey`
- **[Datasets for LLMs: A Comprehensive Survey](https://doi.org/10.1007/s10462-025-11403-7)** - Liu et al., AI Review · `survey`
- **[Empowering Scientific Discovery with Explainable Small Domain-Specific LMs](https://doi.org/10.1007/s10462-025-11365-w)** - AI Review · `survey`
- **[Cryptography-Based Privacy-Preserving LLMs: A Lifecycle Survey](https://doi.org/10.1007/s10462-025-11466-6)** - Luo et al., AI Review · `survey`
- **[Agent-in-the-Loop: Distilling Expert Knowledge into AI Models](https://doi.org/10.1007/s10462-025-11255-1)** - Gao et al., AI Review · `survey`

---

## 📅 2026: The Edge Era

*The frontier moved to agents, safety under quantization, and models small enough to disappear into products. This section grows every week.*

### Models
- **[Gemma 4: E2B, E4B, 26B A4B MoE, 31B Dense](https://deepmind.google/models/gemma/gemma-4/)** - Google DeepMind · `model` — MatFormer-style elastic models purpose-built for on-device.
- **[MedGemma 1.5 Model Update](https://developers.google.com/health-ai-developer-foundations/medgemma/model-card)** - Google Health AI · `domain` `model`

### Agents and Enterprise
- **[Fine-tuning SLMs as Enterprise Search Relevance Labelers](https://arxiv.org/abs/2601.03211)** - Kang et al., Microsoft · `domain`
- **[CyberLLM-FINDS: Domain LLMs with RAG and Graph Integration for MITRE](https://arxiv.org/abs/2601.06779)** - Iyer et al. · `domain`
- **[LLM and AI Agents for Autonomous Systems: A Survey](https://doi.org/10.1109/OJITS.2026.3665677)** - Ferrag et al., IEEE OJ-ITS · `survey`
- **[From Language to Action: LLMs as Autonomous Agents and Tool Users](https://doi.org/10.1007/s10462-025-11471-9)** - Chowa et al., AI Review · `survey`

### Fine-tuning Science
- **[Artificial Entanglement in the Fine-Tuning of LLMs](https://arxiv.org/abs/2601.06788)** - Chen et al. · `peft` — why fine-tuning creates hidden couplings between capabilities.
- **[Fine-Tuning an LLM for Systematic Review Screening](https://arxiv.org/abs/2603.24767)** - Yamoah et al. · `domain`

### Surveys
- **[Small Language Models: Architecture, Evolution, and the Future of AI](https://www.preprints.org/manuscript/202601.0973)** - Shah et al. · `survey`

---

## 🇮🇳 The Indic SLM Index

A cross-year shortcut for anyone building AI in Indian languages, because 1.4 billion people should not need a data center to get a tutor, a doctor's assistant, or a legal explainer.

| Layer | Papers and models |
|-------|-------------------|
| **Encoders and bases** | MuRIL (2021) · IndicBERT (2022) · IndicBART (2022) |
| **Hindi** | OpenHathi (2023) · Airavata (2024) · Nemotron-Mini-Hindi (2024) · Gajendra (2024) · Open Aditi (2024) · Mantra-14B (2025) |
| **Multi-Indic generalists** | Sarvam-2B / Sarvam-1 (2024) · Navarasa 2.0 (2024) · SUTRA (2024) · BharatGen (2024) · Krutrim 1 and 2 (2025) · Sarvam-M (2025) |
| **Language-specific** | Tamil-Llama (2023) · Tamil/Telugu/Malayalam-LLaMA v0.2 (2024) · MahaMarathi (2024) · OdiaGenAI (2024) · Kan-LLaMA (2024) |
| **Data and recipes** | IndicLLMSuite (2024) · IndicVarna-100K (2024) · IndicDialogue (2024) · Efficient CPT for Indic (2025) · OpenHathi QLoRA recipe (2024) |
| **Benchmarks** | IndicGenBench (2024) · IndicMMLU-Pro (2025) · IndicParam (2025) · Tamil phoneme-to-meaning eval (2025) · Indic capabilities analysis (2025) |

---

## 🤝 Contributing

Found a paper that belongs here? PRs are very welcome.

1. One paper per PR, placed under the correct year and subsection
2. Format: `**[Title](link)** - First Author et al., Venue · tags`
3. A one-line "why it matters" note is encouraged for landmark papers
4. Preprints are fine; broken links are not

If this list saved you a literature review, a ⭐ helps others find it.

## 📖 Citation

```bibtex
@misc{awesome-slm-papers,
  title  = {Awesome SLM Papers: A Curated Timeline of Small Language Model Research, 1987-2026},
  author = {Tiwari, Niraj},
  year   = {2026},
  url    = {https://github.com/ntiwari78/awesome-slm-papers/}
}
```

## License

[CC0 1.0 Universal](LICENSE). Take it, fork it, translate it, teach with it.

---

<p align="center"><i>Small models. Big reach. Built with care in Bengaluru.</i> 🇮🇳</p>
