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
| Apr / Jun / Sep 2026 | Laboratory affiliation confirmed; finer-grained dated records not yet recovered |

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