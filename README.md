# mDeBERTa-v3-base-kor-further
Further pre-trained mDeBERTa-v3-base Model with Korean dataset

> ๐ก ์๋ ํ๋ก์ ํธ๋ย KPMG Lighthouse Korea์์ ์งํํ์์ต๋๋ค.   
> KPMG Lighthouse Korea์์๋, Financial area์ ๋ค์ํ ๋ฌธ์ ๋ค์ ํด๊ฒฐํ๊ธฐ ์ํด Edge Technology์ NLP/Vision AI๋ฅผ ๋ชจ๋ธ๋งํ๊ณ  ์์ต๋๋ค.
  

## What is DeBERTa?
- [DeBERTa](https://arxiv.org/abs/2006.03654)๋ `Disentangled Attention` + `Enhanced Mask Decoder` ๋ฅผ ์ ์ฉํ์ฌ ๋จ์ด์ positional information์ ํจ๊ณผ์ ์ผ๋ก ํ์ตํฉ๋๋ค. ์ด์ ๊ฐ์ ์์ด๋์ด๋ฅผ ํตํด, ๊ธฐ์กด์ BERT, RoBERTa์์ ์ฌ์ฉํ๋ absolute position embedding๊ณผ๋ ๋ฌ๋ฆฌ DeBERTa๋ ๋จ์ด์ ์๋์ ์ธ ์์น ์ ๋ณด๋ฅผ ํ์ต ๊ฐ๋ฅํ ๋ฒกํฐ๋ก ํํํ์ฌ ๋ชจ๋ธ์ ํ์ตํ๊ฒ ๋ฉ๋๋ค. ๊ฒฐ๊ณผ์ ์ผ๋ก, BERT, RoBERTA ์ ๋น๊ตํ์ ๋ ๋ ์ค์ํ ์ฑ๋ฅ์ ๋ณด์ฌ์ฃผ์์ต๋๋ค.
- [DeBERTa-v3](https://arxiv.org/abs/2111.09543)์์๋, ์ด์  ๋ฒ์ ์์ ์ฌ์ฉํ๋ MLM (Masked Language Model) ์ RTD (Replaced Token Detection) Task ๋ก ๋์ฒดํ ELECTRA ์คํ์ผ์ ์ฌ์ ํ์ต ๋ฐฉ๋ฒ๊ณผ, Gradient-Disentangled Embedding Sharing ์ ์ ์ฉํ์ฌ ๋ชจ๋ธ ํ์ต์ ํจ์จ์ฑ์ ๊ฐ์ ํ์์ต๋๋ค.
- DeBERTa์ ์ํคํ์ฒ๋ก ํ๋ถํ ํ๊ตญ์ด ๋ฐ์ดํฐ๋ฅผ ํ์ตํ๊ธฐ ์ํด์,  `mDeBERTa-v3-base-kor-further` ๋ microsoft ๊ฐ ๋ฐํํ `mDeBERTa-v3-base` ๋ฅผ ์ฝ 40GB์ ํ๊ตญ์ด ๋ฐ์ดํฐ์ ๋ํด์ **์ถ๊ฐ์ ์ธ ์ฌ์ ํ์ต**์ ์งํํ ์ธ์ด ๋ชจ๋ธ์๋๋ค.
  
## How to Use
- Requirements
    ```
    pip install transformers
    pip install sentencepiece
    ```   
- [Huggingface Hub](https://huggingface.co/lighthouse/mdeberta-v3-base-kor-further)
    ```python
    from transformers import AutoModel, AutoTokenizer
    
    model = AutoModel.from_pretrained("mdeberta-v3-base-kor-further")  # DebertaV2ForModel
    tokenizer = AutoTokenizer.from_pretrained("mdeberta-v3-base-kor-further")  # DebertaV2Tokenizer (SentencePiece)
    ```

## Pre-trained Models
- ๋ชจ๋ธ์ ์ํคํ์ฒ๋ ๊ธฐ์กด microsoft์์ ๋ฐํํ `mdeberta-v3-base`์ ๋์ผํ ๊ตฌ์กฐ์๋๋ค.
    
    |  | Vocabulary(K) | Backbone Parameters(M) | Hidden Size | Layers | Note |
    | --- | --- | --- | --- | --- | --- |
    | mdeberta-v3-base-kor-further (mdeberta-v3-base์ ๋์ผ) | 250 | 86 | 768 | 12 | 250K new SPM vocab |

## Further Pretraing Details (MLM Task)
- `mDeBERTa-v3-base-kor-further` ๋ `microsoft/mDeBERTa-v3-base` ๋ฅผ ์ฝ 40GB์ ํ๊ตญ์ด ๋ฐ์ดํฐ์ ๋ํด์ MLM Task๋ฅผ ์ ์ฉํ์ฌ ์ถ๊ฐ์ ์ธ ์ฌ์  ํ์ต์ ์งํํ์์ต๋๋ค.
    
    |  | Max length | Learning Rate | Batch Size | Train Steps | Warm-up Steps |
    | --- | --- | --- | --- | --- | --- |
    | mdeberta-v3-base-kor-further | 512 | 2e-5 | 8 | 5M | 50k |
    

## Datasets
- ๋ชจ๋์ ๋ง๋ญ์น(์ ๋ฌธ, ๊ตฌ์ด, ๋ฌธ์ด), ํ๊ตญ์ด Wiki, ๊ตญ๋ฏผ์ฒญ์ ๋ฑ ์ฝ 40 GB ์ ํ๊ตญ์ด ๋ฐ์ดํฐ์์ด ์ถ๊ฐ์ ์ธ ์ฌ์ ํ์ต์ ์ฌ์ฉ๋์์ต๋๋ค.
    - Train: 10M lines, 5B tokens
    - Valid: 2M lines, 1B tokens
    - cf) ๊ธฐ์กด mDeBERTa-v3์ XLM-R ๊ณผ ๊ฐ์ด [cc-100 ๋ฐ์ดํฐ์](https://data.statmt.org/cc-100/)์ผ๋ก ํ์ต๋์์ผ๋ฉฐ, ๊ทธ ์ค ํ๊ตญ์ด ๋ฐ์ดํฐ์์ ํฌ๊ธฐ๋ 54GB์๋๋ค.
    

## Fine-tuning on NLU Tasks - Base Model
| Model | Size | NSMC(acc) | Naver NER(F1) | PAWS (acc) | KorNLI (acc) | KorSTS (spearman) | Question Pair (acc) | KorQuaD (Dev) (EM/F1) | Korean-Hate-Speech (Dev) (F1) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| XLM-Roberta-Base | 1.03G | 89.03 | 86.65 | 82.80 | 80.23 | 78.45 | 93.80 | 64.70 / 88.94 | 64.06 |
| mdeberta-base | 534M | 90.01 | 87.43 | 85.55 | 80.41 | **82.65** | 94.06 | 65.48 / 89.74 | 62.91 |
| mdeberta-base-kor-further (Ours) | 534M | **90.52** | **87.87** | **85.85** | **80.65** | 81.90 | **94.98** | **66.07 / 90.35** | **68.16** |

## Citation
```
@misc{he2021debertav3,
      title={DeBERTaV3: Improving DeBERTa using ELECTRA-Style Pre-Training with Gradient-Disentangled Embedding Sharing}, 
      author={Pengcheng He and Jianfeng Gao and Weizhu Chen},
      year={2021},
      eprint={2111.09543},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```

```
@inproceedings{
he2021deberta,
title={DEBERTA: DECODING-ENHANCED BERT WITH DISENTANGLED ATTENTION},
author={Pengcheng He and Xiaodong Liu and Jianfeng Gao and Weizhu Chen},
booktitle={International Conference on Learning Representations},
year={2021},
url={https://openreview.net/forum?id=XPZIaotutsD}
}
```

## Reference
- [DeBERTa](https://github.com/microsoft/DeBERTa)
- [Huggingface Transformers](https://github.com/huggingface/transformers)
- [๋ชจ๋์ ๋ง๋ญ์น](https://corpus.korean.go.kr/)
- [Korpora: Korean Corpora Archives](https://github.com/ko-nlp/Korpora)
- [sooftware/Korean PLM](https://github.com/sooftware/Korean-PLM)
