# RSMHSD: Roman Script Multimodal Hate Speech Dataset

**Cross-Cultural Multimodal Hate Speech Detection for Roman Script South Asian Content Using Vision-Language Models**

GKS R&D Applicant | Faiza Hanif | Master's Research Proposal

## Overview

Hundreds of millions of Pakistani and Indian users write Urdu and Hindi in Roman script on social media, mainly because it's easier to type on a phone (Ashiq et al., 2024). That shared writing space is also where a lot of hate speech now lives, packed into memes and image-caption posts (Rizwan et al., 2020). Most existing detection systems only read one side of that: they catch the caption but miss the image, or read the image but miss the embedded Roman Urdu/Hindi text (Rizwan et al., 2020; Ashiq et al., 2024). Even the strongest multilingual multimodal hate speech dataset available today covers five languages, and none of them are Roman Urdu or Roman Hindi (Bui et al., 2025).

This project works on closing that gap:

- Building the first annotated multimodal dataset of Roman script South Asian hate speech (RSMHSD)
- Fine-tuning vision-language models that can reason over image and text together
- Benchmarking those models against unimodal and traditional fusion baselines
- Running the first empirical study of where Pakistani and Indian annotators agree and disagree on the same hateful content

## Research Questions

**RQ1.** Do vision-language models fine-tuned on Roman script South Asian content outperform text-only and image-only baselines, and do visual signals help specifically on sarcasm or culturally coded content?

**RQ2.** How much do Pakistani and Indian annotators disagree when labeling the same multimodal content, and does that disagreement show up in model performance across the two cultural subsets?

**RQ3.** Can one unified model handle both Pakistani and Indian content well, or does the cross-cultural gap require separate fine-tuning per culture?

## Dataset Plan

- 6,000 image-text pairs (3,000 hateful, 3,000 not hateful), collected from Pakistani and Indian public social media pages
- Balanced 2x2x2 design across hate speech label, cultural origin, and content type: 1,500 Pakistani and 1,500 Indian samples per class, split evenly between memes (750) and image-caption posts (750) per cultural origin per class
- Three-annotator panel: one Pakistani bilingual annotator, one Indian bilingual annotator, and a tie-breaker with exposure to both cultural and linguistic contexts (e.g. diaspora background). The tie-breaker isn't claimed to be culturally neutral, just used to resolve 2-1 splits
- Agreement measured with Fleiss' Kappa; samples kept using a 2/3 majority-vote threshold. Cases the tie-breaker had to resolve are kept and flagged as a separate "culturally contested" subset for the cross-cultural analysis

## Models

| Model | Type |
|---|---|
| mBERT | Text baseline |
| ResNet-50 | Image baseline |
| BiLSTM + EfficientNet | Traditional fusion baseline (Saddozai et al., 2025) |
| CLIP | Vision-language model (LoRA fine-tuned) |
| LLaVA | Vision-language model (LoRA fine-tuned) |

BLIP-2 was cut from the main benchmark to keep compute focused on the strongest candidates. It's still a possible follow-up.

## Methodology Summary

- **Input processing.** Memes have text baked into the image, so they go through OCR (TrOCR / EasyOCR) first. Image-caption posts already have image and text as separate inputs, so no OCR is needed.
- **Fine-tuning.** CLIP and LLaVA are adapted with LoRA, which keeps fine-tuning large vision-language models feasible without full retraining.
- **Annotation quality control.** Three annotators, Fleiss' Kappa for agreement, tie-breaker for disagreements.
- **Evaluation.** A held-out test set (10%, 600 samples), stratified by label and cultural origin. Macro-F1 is the main metric, with Accuracy, Precision, Recall, and AUROC reported alongside it, and everything broken out by Pakistani vs. Indian subsets.
- **Ablation.** Text-only, image-only, and full multimodal input compared for CLIP and LLaVA, to see how much the visual signal actually contributes.

## Korean Connection

South Korean NLP has built solid hate speech benchmarks, BEEP! (Moon et al., 2020) and K-MHaS (Lee et al., 2022), for the same underlying problem: catching hate speech in online communities. Like most Roman Urdu/Hindi work, those are text-only. This research takes that same core idea and applies it where it hasn't gone yet: the multimodal, image-plus-text version of the problem, starting with Roman script South Asian content.

## Timeline

| Year | Months | Focus |
|---|---|---|
| Year 1 | 1 to 12 | Language development (TOPIK Level 3 target) and academic integration |
| Year 2, Sem 1 | 1 to 6 | Data collection, annotator recruitment and training, annotation, quality control |
| Year 2, Sem 2 | 7 to 12 | Preprocessing pipeline, OCR evaluation, baseline training, VLM fine-tuning (LoRA) |
| Year 3, Sem 3 | 13 to 18 | Comparative benchmarking, ablation studies, cross-cultural disagreement analysis, error analysis |
| Year 3, Sem 4 | 19 to 24 | Thesis writing, conference paper submission, dataset release on Hugging Face and GitHub, final thesis submission |

## Long-Term Goals

The plan is to return to Pakistan as an active NLP researcher: publishing, teaching, and building annotated datasets for low-resource South Asian languages, while keeping research ties with Korean institutions active. This work also sets up a possible PhD extension applying the same framework to hate speech targeting migrant communities on Korean platforms.

## References

- Ashiq, W., Kanwal, S., Rafique, A., & Waqas, M. (2024). Roman Urdu hate speech detection using hybrid machine learning models and hyperparameter optimization. *Scientific Reports*, 14, 28590. https://doi.org/10.1038/s41598-024-79106-7
- Bui, M. D., von der Wense, K., & Lauscher, A. (2025). Multi3Hate: Multimodal, multilingual, and multicultural hate speech detection with vision-language models. *Proceedings of NAACL 2025*.
- Rizwan, H., Shakeel, M. H., & Karim, A. (2020). Hate-speech and offensive language detection in Roman Urdu. *Proceedings of EMNLP 2020*, pages 2512 to 2522. https://doi.org/10.18653/v1/2020.emnlp-main.197
- Saddozai, F., Badri, S., & Alghazzawi, D. (2025). Multimodal hate speech detection: A novel deep learning framework for multilingual text and images. *PeerJ Computer Science*, e2801.
- Moon, J., Cho, W. I., & Lee, J. (2020). BEEP! Korean Corpus of Online News Comments for Toxic Speech Detection. In *Proceedings of the Eighth International Workshop on Natural Language Processing for Social Media*, pages 25 to 31.
- Lee, J., Lim, T., Lee, H., Jo, B., Kim, Y., Yoon, H., & Han, S. C. (2022). K-MHaS: A Multi-label Hate Speech Detection Dataset in Korean Online News Comment. In *Proceedings of the 29th International Conference on Computational Linguistics (COLING 2022)*, pages 3530 to 3538.

## License
