 RSMHSD: Roman Script Multimodal Hate Speech Dataset

Cross-Cultural Multimodal Hate Speech Detection for Roman Script South Asian Content Using Vision-Language Models

GKS R&D Applicant | Faiza Hanif | Master's Research Proposal

Overview

Across South Asia, hundreds of millions of Pakistani and Indian users write Urdu and Hindi in Roman script on social media, since Roman script is easier to type on mobile devices (Ashiq et al., 2024). This shared writing space is increasingly used to spread hate speech that combines images and Roman script text in memes and image-caption posts (Rizwan et al., 2020). Existing detection systems process only one modality at a time — reading the caption but missing the image, or reading the image but missing the embedded Roman Urdu/Hindi text (Rizwan et al., 2020; Ashiq et al., 2024). Even the most advanced multilingual multimodal hate speech dataset available today covers five languages but not Roman Urdu or Roman Hindi, leaving South Asian digital spaces unaddressed (Bui et al., 2025).

This project addresses that gap by:
1. Constructing the first annotated multimodal dataset of Roman script South Asian hate speech (RSMHSD)
2. Fine-tuning vision-language models capable of joint image-text reasoning
3. Benchmarking against unimodal and traditional fusion baselines
4. Conducting the first empirical cross-cultural analysis of Pakistani and Indian annotator agreement/divergence on the same hateful content

 Research Questions
1. Do vision-language models outperform unimodal baselines on this task?
2. How much do Pakistani and Indian annotators disagree on the same content, and why?
3. Can a single unified model handle both cultural contexts effectively?

Dataset Plan
- 12,000 memes and image-caption posts (6,000 hateful / 6,000 not hateful)
- Sourced from Pakistani and Indian public social media pages
- Three-annotator panel: Pakistani bilingual, Indian bilingual, neutral Bangladeshi annotator
- Inter-annotator agreement measured via Fleiss' Kappa; disagreements resolved by majority vote

Models


| Model | Type |
|---|---|
| mBERT | Text baseline |
| XLM-RoBERTa | Text baseline |
| ResNet-50 | Image baseline |
| EfficientNet | Image baseline |
| BiLSTM + EfficientNet | Traditional fusion |
| CLIP | Vision-language model (LoRA fine-tuned) |
| BLIP-2 | Vision-language model (LoRA fine-tuned) |
| LLaVA | Vision-language model (LoRA fine-tuned) |

Korean Connection

South Korean NLP research has established robust text-based hate speech benchmarks — BEEP!, K-MHaS, and KcHateSpeech — but these were designed primarily for textual input, with limited support for multimodal image-text analysis. This research uses these existing Korean benchmarks as a comparative control framework, allowing isolation of which harm patterns are language/culture-specific versus which appear across both South Asian and Korean contexts. The proposed methodology extends this foundation into the multimodal domain, producing a transferable framework that may support future research on multimodal hate speech in Korean online environments.

Timeline

| Year | Months | Focus |
|---|---|---|
| Year 1 | 1–12 | Language development (TOPIK Level 3 target) and academic integration |
| Year 2, Sem 1 | 1–6 | Literature review, annotation design, dataset construction (RSMHSD) |
| Year 2, Sem 2 | 7–12 | Pipeline development, training all 8 models |
| Year 3, Sem 3 | 13–18 | Evaluation, cross-cultural analysis, conference paper draft |
| Year 3, Sem 4 | 19–24 | Thesis writing, paper submission, public dataset/model release |

 Long-Term Goals

The long-term goal is to return to Pakistan as an active NLP researcher — publishing, teaching, and building annotated datasets for low-resource South Asian languages — while maintaining active research collaborations with Korean institutions. This research also lays groundwork for a planned PhD extension applying the same framework to hate speech targeting migrant communities on Korean platforms.

References
Ashiq, W., Kanwal, S., Rafique, A., & Waqas, M. (2024). Roman Urdu hate speech detection using hybrid machine learning models and hyperparameter optimization. Scientific Reports, 14, 28590. https://doi.org/10.1038/s41598-024-79106-7

Bui, M. D., von der Wense, K., & Lauscher, A. (2025). Multi³Hate: Multimodal, multilingual, and multicultural hate speech detection with vision–language models. Proceedings of NAACL 2025.

Rizwan, H., Shakeel, M. H., & Karim, A. (2020). Hate-speech and offensive language detection in Roman Urdu. *Proceedings of EMNLP 2020*, 2512–2522. https://doi.org/10.18653/v1/2020.emnlp-main.197

## License
Research data and outputs planned for release under [CC-BY-NC 4.0](./LICENSE-DATA.md).
