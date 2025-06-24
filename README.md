
# GLIGEN: Open-Set Grounded Text-to-Image Generation (CVPR 2023)

[Yuheng Li](https://yuheng-li.github.io/), [Haotian Liu](https://hliu.cc), [Qingyang Wu](https://scholar.google.ca/citations?user=HDiw-TsAAAAJ&hl=en/), [Fangzhou Mu](https://pages.cs.wisc.edu/~fmu/), [Jianwei Yang](https://jwyang.github.io/), [Jianfeng Gao](https://www.microsoft.com/en-us/research/people/jfgao/), [Chunyuan Li*](https://chunyuan.li/), [Yong Jae Lee*](https://pages.cs.wisc.edu/~yongjaelee/) (*Co-senior authors)

[[Project Page](https://gligen.github.io/)] [[Paper](https://arxiv.org/abs/2301.07093)] [[Demo](https://huggingface.co/spaces/gligen/demo)] [[YouTube Video](https://youtu.be/-MCkU7IAGKs)]
![Teaser figure](figures/concept.gif)

[![IMAGE ALT TEXT HERE](https://github.com/gligen/GLIGEN/blob/master/figures/teaser_v4.png)](https://youtu.be/-MCkU7IAGKs)

출처 : https://github.com/gligen/GLIGEN



## 수행 과정

### 1. 가상환경 설정
```bash
conda create -n gligen2 python=3.8 -y
conda activate gligen
```
### 2. 라이브러리 설치
```bash
conda install pytorch=1.13.0 torchvision=0.14.0 cudatoolkit=11.6 -c pytorch -y -c nvidia
pip install albumentations==0.4.3 opencv-python pudb==2019.2 imageio==2.9.0 imageio-ffmpeg==0.4.2 pytorch-lightning==1.4.2 omegaconf==2.1.1 "test-tube>=0.7.5" "streamlit>=0.73.1" einops==0.3.0 torch-fidelity==0.3.0 git+https://github.com/openai/CLIP.git "protobuf~=3.20.1" torchmetrics==0.6.0 transformers==4.19.2 kornia==0.5.8 && pip uninstall -y torchtext
```
### 3. GLIGEN 모델 가중치 다운로드

| Mode       | Modality       | Download                                                                                                       |
|------------|----------------|----------------------------------------------------------------------------------------------------------------|
| Generation | Box+Text       | [HF Hub](https://huggingface.co/gligen/gligen-generation-text-box/blob/main/diffusion_pytorch_model.bin)       |
| Generation | Box+Text+Image | [HF Hub](https://huggingface.co/gligen/gligen-generation-text-image-box/blob/main/diffusion_pytorch_model.bin) |
| Generation | Keypoint       | [HF Hub](https://huggingface.co/gligen/gligen-generation-keypoint/blob/main/diffusion_pytorch_model.bin)       |
| Inpainting | Box+Text       | [HF Hub](https://huggingface.co/gligen/gligen-inpainting-text-box/blob/main/diffusion_pytorch_model.bin)       |
| Inpainting | Box+Text+Image | [HF Hub](https://huggingface.co/gligen/gligen-inpainting-text-image-box/blob/main/diffusion_pytorch_model.bin) |
| Generation | Hed map        | [HF Hub](https://huggingface.co/gligen/gligen-generation-hed/blob/main/diffusion_pytorch_model.bin)      |
| Generation | Canny map      | [HF Hub](https://huggingface.co/gligen/gligen-generation-canny/blob/main/diffusion_pytorch_model.bin)      |
| Generation | Depth map      | [HF Hub](https://huggingface.co/gligen/gligen-generation-depth/blob/main/diffusion_pytorch_model.bin)      |
| Generation | Semantic map   | [HF Hub](https://huggingface.co/gligen/gligen-generation-sem/blob/main/diffusion_pytorch_model.bin)      |
| Generation | Normal map     | [HF Hub](https://huggingface.co/gligen/gligen-generation-normal/blob/main/diffusion_pytorch_model.bin)      |

가중치(.bin) 파일 다운로드 후(가중치 파일 명이 모두 동일하기 때문에 파일명 변경 추천), 다운로드 받아 저장한 경로에 따라 'gligen_inference.py'내 meta_list의 ckpt 경로 변경

### 4. 실행
`gligen_inference.py`파일 실행
```bash
python gligen_inference.py
```
샘플 이미지는 `generation_samples`에 저장됨.

