# Undergraduate Research | Medical AI

**Medical Imaging · Segmentation · Image Registration · Cerebrovascular Analysis**

**Research Period:** March–September 2026 (7 months)  
**Affiliation:** Undergraduate Researcher, Medical AI Laboratory  
**Focus:** Medical image segmentation, loss-function design, anatomical registration, and vascular structure analysis

> This repository documents the research topics, experiments, technical challenges, and lessons from my undergraduate research experience. Implemented work and literature reviews are distinguished throughout.

## Overview

During seven months of undergraduate research, I explored how deep learning models can process medical images and how to evaluate their outputs beyond conventional pixel-level accuracy. My work covered two main directions:

1. **Skin lesion segmentation:** Studied and experimented with boundary-aware loss functions for U-Net using the ISIC 2018 dataset.
2. **Cerebrovascular imaging:** Worked on 3D vessel skeletonization and attempted atlas-based registration of Circle of Willis structures, investigating the limitations caused by patient-specific vascular variability.

I also reviewed research related to VoxelMorph, TopCoW, Voreen centerline graphs, and vessel topology analysis.

## Research Projects

### 01. Boundary-Aware Skin Lesion Segmentation

**Keywords:** `U-Net` `ISIC 2018` `PyTorch` `Boundary Loss` `Curriculum Learning`

**Problem.** Pixel-wise segmentation losses such as BCE can underemphasize ambiguous lesion boundaries, even when region-level overlap is satisfactory.

**Approach.** Investigated a Boundary Weighted BCE + Dice loss that creates a boundary band from the ground-truth mask using morphological dilation and erosion. The curriculum variant gradually increases boundary weighting after an initial warm-up period.

```text
Dermoscopy image + lesion mask
  → U-Net segmentation
  → GPU-based boundary-band extraction
  → Boundary-weighted BCE + Dice
  → Static / curriculum weighting comparison
  → Region and boundary evaluation
```

**Experiment settings documented in the research manuscript:**

| Item | Setting |
|---|---|
| Dataset | ISIC 2018 Task 1 |
| Split | 2,335 training / 259 validation images |
| Model | Standard U-Net |
| Training | Adam, lr=1e-4, batch size 8, 30 epochs |
| Comparisons | BCE, BCE+Dice, Focal+Dice, BCE+Tversky, Kervadec Boundary Loss and proposed variants |
| Evaluation | Dice, IoU, Boundary Dice, Boundary IoU, HD95 |
| Experiments | 24 controlled comparisons reported; 3 random seeds |

**Results reported in the manuscript (multi-seed):** Boundary IoU **0.319** and HD95 **10.24**, corresponding to **+9.6% Boundary IoU** and **−10.3% HD95** compared with BCE. The manuscript also reports an approximately 150× difference in the *loss forward-computation time* against its Kervadec implementation, **not** end-to-end model inference speed.

**Research manuscript:** *Progressive Boundary-Weighted Loss for U-Net Based Skin Lesion Segmentation* (PDF upload pending; source available in the local research archive)  
**Status:** Research manuscript / publication status unverified. The manuscript is not claimed as a peer-reviewed publication.

### 02. Circle of Willis Vessel Analysis and Atlas Registration

**Keywords:** `CTA/MRA` `Circle of Willis` `3D Skeletonization` `Atlas Registration` `TopCoW` `Centerline Graph`

**Motivation.** A vascular segmentation mask does not fully capture anatomical connectivity, branching patterns, or vessel-specific correspondence across patients.

**Work performed:**
- Worked on **3D cerebrovascular skeletonization**, converting vessel structures toward a thinner representation for structural analysis.
- **Attempted atlas-based vascular registration** and observed that patient-to-patient variations in vessel pathways and connectivity prevented satisfactory anatomical correspondence.
- Studied the distinction between spatial alignment and anatomical structure matching.

**Literature and technical analysis:**
- Reviewed **TopCoW** and Circle of Willis vascular segmentation/labeling concepts.
- Studied **Voreen** centerline extraction, node-edge graphs, invalid connections, self-loops, and spurious branches.
- Examined potential vessel descriptors such as centerline radius, length, curvature, tortuosity, and bifurcation geometry.
- Explored aneurysm location mapping and a separate 52-class location taxonomy. This was an analysis/visualization topic, **not** a confirmed trained 52-class classifier.

**Key lesson.** Aligning scans in a shared coordinate space does not ensure that corresponding vessels and branches are anatomically matched. A high mask-overlap score can also hide connectivity errors. The registration attempt did not achieve the intended result; this limitation is documented as part of the research process rather than presented as a successful model.

### 03. Related Paper Reviews

- **VoxelMorph:** moving/fixed images, deformation fields, spatial warping, and segmentation-assisted registration.
- **Other registration methods:** NiftyReg, SyN, B-spline deformations, and folding concerns (technical review; direct implementation not established).
- **Medical AI topics:** chest X-ray multilabel learning, uncertainty/loss design, and medical-image model evaluation.
- **MICCAI-related work:** reviewed challenge datasets and vascular analysis approaches; competition submission or award not claimed.

## Timeline

| Period | Focus |
|---|---|
| Mar 2026 | Medical AI literature-review methods |
| May 2026 | ISIC 2018 segmentation research and manuscript refinement |
| Jul 2026 | Medical image registration and VoxelMorph analysis |
| Aug 2026 | Cerebrovascular skeletonization, atlas registration attempt, TopCoW and centerline graph review |

## Skills and Research Takeaways

- **Experimentation:** baseline comparisons, ablation studies, reproducible evaluation, and interpretation of boundary metrics.
- **Medical imaging:** segmentation masks, registration, centerlines, vascular anatomy, and topology-aware evaluation.
- **Research practice:** paper review, identifying methodological limitations, recording failed approaches, and separating observed results from proposed next steps.

## Documentation

- [`research-notes/`](research-notes/) — dated research questions, paper notes, experiments, and limitations (add source records when available).
- [Full research manuscript (PDF)](papers/Progressive_Boundary_Weighted_Loss_UNet_Skin_Lesion.pdf) — complete skin lesion segmentation manuscript.
- [Research notes (Mar–Sep 2026)](research-notes/Research_Notes_2026_03-09.md) — reconstructed research timeline and evidence boundaries.

> **Before publishing publicly:** Check permission to share the manuscript and any institutional materials; the PDF includes author/contact information. Confirm submission/publication status separately.

## Scope and Verification

This README summarizes research notes and an existing manuscript. Some older discussions have been reconstructed rather than recovered verbatim. Directly reported work includes 3D vessel skeletonization and an unsuccessful atlas-registration attempt; detailed code, datasets, and registration logs have not yet been verified. Literature review does not imply reproduction, MICCAI competition submission, or publication.

---

## 한국어 소개

**가천대학교 소프트웨어학과 | 의료 AI 학부연구생**  
**활동 기간:** 2026년 3월~9월 (7개월)

의료영상 분할과 정합, 뇌혈관 구조 분석을 중심으로 논문 리뷰와 실험을 진행했습니다. 실제 수행한 작업과 논문에서 검토한 내용을 구분해 기록했습니다.

### 01. 피부 병변 분할 연구 (Skin Lesion Segmentation)

- **ISIC 2018 Task 1** 데이터셋과 **U-Net** 기반 피부 병변 분할 연구
- 팽창·침식 연산으로 경계를 추출하는 **Boundary Weighted BCE + Dice Loss** 및 학습 진행에 따라 경계 가중치를 증가시키는 **Curriculum Boundary Loss** 설계
- 연구 원고에 기록된 **24개 통제 실험**과 **3개 랜덤 시드** 재현성 검증
- BCE, BCE+Dice, Focal+Dice, BCE+Tversky, Kervadec Boundary Loss 등 비교
- **연구 원고의 multi-seed 결과:** Boundary IoU **0.319**, HD95 **10.24**; BCE 대비 각각 **+9.6%**, **−10.3%**
- Kervadec 대비 약 150배 속도 차이는 **손실 함수 forward 계산 시간** 기준이며 전체 모델 추론 속도가 아님

**작성 논문:** *Progressive Boundary-Weighted Loss for U-Net Based Skin Lesion Segmentation*  
**상태:** 연구 원고 작성. 학술대회 게재 여부는 확인되지 않았으며 PDF는 저장소에 아직 업로드되지 않았습니다.

### 02. 뇌혈관 구조 분석 및 Atlas Registration

- **직접 수행:** 3D 뇌혈관 Skeletonization 작업
- **직접 시도:** Atlas 기반 뇌혈관 정합. 환자마다 Circle of Willis의 혈관 형태와 분기·연결 구조가 달라 기대한 정합 결과에 도달하지 못함
- **논문 및 방법 검토:** TopCoW, MICCAI 관련 혈관 라벨링, Voreen 기반 Centerline Graph, 혈관 연결 오류와 Self-loop
- **특징 분석 학습:** 중심선 반지름, 혈관 길이, 곡률, 굴곡도, 분기각 및 52개 동맥류 위치 클래스 매핑

**배운 점:** 영상의 공간적 정렬과 해부학적으로 같은 혈관을 정확하게 대응시키는 것은 다르며, 혈관 분할 성능뿐 아니라 연결 구조의 타당성을 확인해야 한다는 점을 이해했습니다.

### 03. 관련 논문 및 기술 학습

VoxelMorph의 Deformation Field와 Warping, Segmentation-assisted Registration을 비롯해 NiftyReg, SyN, B-spline, 의료영상 정합·평가 기법을 검토했습니다. 이 항목들은 논문 리뷰와 기술 학습에 해당하며, 전부 직접 구현했다는 의미는 아닙니다.

### 연구 기록

- [2026년 3~9월 연구 및 질문 기록](research-notes/Research_Notes_2026_03-09.md)

> 이 README는 현재 확보된 과거 기록과 연구 원고를 기준으로 작성했습니다. 확인되지 않은 MICCAI 대회 제출·수상 또는 논문 게재 실적은 주장하지 않습니다.
