# 의료 AI 연구실 연구·질문 통합 기록 (현재 확보분) — 2026년 3월~9월

> 통합 복원일: 2026-11-10 · 저장 형식: Markdown / GitHub-friendly UTF-8  
> **연구실 활동 기간:** 2026-03 ~ 2026-09 (사용자 직접 확인, 총 7개월)  
> **성격:** 과거 대화에서 조회 가능한 질문 이력 + 작성한 연구 파일 + 당시 논문 원문에 기재된 실험 결과를 합친 **재구성본**. 모든 대화의 무손실 원문 백업은 아니다.

## 복원 원칙 및 증거 등급

- **[직접 진술]** 본인이 과거 대화에서 실제 작업으로 확인한 사실. 예: 3~9월 연구실, 3D 뇌혈관 skeleton 작업, Atlas 정합 시도 및 실패.
- **[날짜 확인]** 검색에서 질문 날짜와 주제가 회수됨. 정확한 인용이 확인되지 않으면 질문은 '요지'로 적는다.
- **[원고 확인]** 보유 논문 파일 `14244002.pdf`에 명시된 연구 방법·실험값. 독립적으로 코드를 재실행한 검증 결과는 아님.
- **[기존 MD]** 이전 대화의 종합 정리 파일에 있던 내용. 1차 원문과 구분.
- **[맥락/회상]** 대화 요약에서 주제가 확인되지만 상세 근거나 날짜는 불충분.
- **[미확인]** 확보되지 않은 코드, 임상 사례, 저자 기여, 결과, 수상·제출 등. 완료한 것으로 쓰지 않는다.

**중요한 구분:** ① 논문을 읽음 ② 방법을 설계·실험함 ③ 대회에 출전·제출함 ④ 논문을 게재함은 서로 다르다. 자료가 증명하는 단계까지만 기록한다.

## 월별 타임라인

| 월 | 확인된 질문·프로젝트 | 근거 및 한계 |
|---|---|---|
| **3월** | 의료 AI 논문 리뷰 방법을 익힘. Abstract → Figure → Conclusion → 본문 흐름, 핵심 아이디어·실험 한계 검토 | 3/4 대화 확인 |
| **4월** | 날짜가 특정된 연구 질문 회수되지 않음 | 활동이 없었다는 뜻이 아님 |
| **5월** | ISIC 피부 병변 분할: U-Net, 정적 Boundary Weighted BCE+Dice, epoch 진행에 따라 λ가 커지는 Curriculum Boundary Loss. 논문/실험 수정 및 검토 | 5/17, 5/19 질문 + 원고 PDF |
| **6월** | 독립적으로 날짜를 특정할 대화 미확인; 피부병변 논문의 중간 연구 기간은 단정 불가 | 실험 시작·종료일 미확인 |
| **7월** | Atlas-based segmentation, VoxelMorph, 정합 개념 비교; CXR 및 뇌 CTA/MRA/CT 활용 질문; AUPRC 0.41 언급 | 7/18, 7/29 대화 확인. AUPRC 데이터셋 연결 미확인 |
| **8월** | SwinCross/VoxelMorph 비교, MICCAI·TopCoW, CoW 52 위치 클래스, Voreen centerline, graph topology, radius·곡률 등; 직접 3D skeleton 및 Atlas 정합 시도 | 8/19~23 세부 기록 + 사용자 확인 |
| **9월** | 연구실 소속 기간에 해당. 개별 질문·모델·실험·발표 기록 미회수 | 빈칸을 임의로 채우지 않음 |

## Part I — 3~7월 연구 활동 상세 복원

### 1. 2026-03-04 — 의료 AI 논문 리뷰 방법

**[날짜 확인]** 논문을 전문가 수준으로 읽고, 핵심 직접 인용구와 아이디어 및 기여점을 중심으로 설명해 달라고 요청함. 복잡한 연구 기법을 쉬운 예시로 이해하려는 접근을 병행함.

- 2026-03-04 13:50 UTC: 의료 AI 논문 학술적 설명 방식에 대한 질문·요구.
- 2026-03-04 14:02 UTC: `Abstract → Figure → Conclusion`을 먼저 읽고, 세부 본문으로 돌아가는 방식이 적절한지 질문.
- 당시 확인된 학습 전략: Abstract로 문제·기여 파악, Figure와 Table로 방법·데이터·비교 구조 파악, Conclusion 및 Limitations로 주장 범위 확인, 필요 시 Methods/Experiments로 검증.
- **성과 해석:** 학술 논문 리뷰 역량을 학습한 기록. 특정 논문 실험 수행이나 발표는 이 날짜의 증거만으로 확인 불가.

### 2. 2026-05-17~19 — ISIC 피부 병변 분할 논문 및 실험

**[직접 연구 활동 및 원고 확인]** 제목: **「점진적 경계 강조 손실 함수를 이용한 U-Net 기반 피부 병변 이미지 분할 성능 개선」** (영문: *Progressive Boundary-Weighted Loss for U-Net Based Skin Lesion Segmentation*). 사용자 기존 논문 자료 `14244002.pdf` 8쪽을 확인함. 학회 게재 확정이나 발표·수상 실적은 확인되지 않음.

#### 2.1 복원된 시간 순서

| 시각(UTC) | 당시에 한 질문·작업(요지) | 확신 수준 |
|---|---|---|
| 2026-05-17 13:49 | U-Net으로 skin lesion segmentation 실험, 서버 GPU에서 ISIC 데이터 내려받아 BCE/Dice/Boundary Loss 비교, 이미지·Dice/IoU/Boundary F1·로그·weight 저장 계획 | 대화 확인 / 초기 계획 |
| 2026-05-17 13:53 | 하계 전자공학회 목표로 경계 강조 손실 함수를 이용한 U-Net 논문 연구 방향 확정, 연구실 서버 사용 질문 | 대화 확인 / 목표와 제출 완료는 구분 |
| 2026-05-19 02:42 | Static λ와 epoch-dependent Curriculum λ의 차이, 경계 마스크 dilation/erosion 및 BCE 재가중 설계 | 대화 확인 |
| 2026-05-19 12:03 | 논문 개선: 핵심 기여를 DT-free boundary weighting과 curriculum weighting으로 정리, 성능·안정성·효율성 중심으로 실험 재구성 | 질문/피드백 확인 |
| 2026-05-19 12:28 | 수정 논문 평가; 데이터셋·표준 U-Net·seed 제한, HD95와 임상 관련 지표, 문장/표 구성 개선 검토 | 대화 확인 |

#### 2.2 연구 문제 정의

일반 BCE 또는 BCE+Dice는 병변 내부와 흐릿한 경계 근처를 유사하게 취급한다. 병변 경계의 작은 오차가 면적, 둘레, 비대칭성 지표에 영향을 줄 수 있어, 모델 구조를 바꾸지 않고 **손실 함수가 경계 픽셀을 더 강조**하도록 설계함.

#### 2.3 방법의 핵심

정답 마스크 `M`에서 dilation `D_k(M)`과 erosion `E_k(M)`으로 경계 띠 `B`를 만들고, 그 위에 BCE weight를 강화한다.

```text
B = D_k(M) - E_k(M)
W = 1 + lambda * B
L_static = mean(W * BCEWithLogits(logits, mask)) + DiceLoss(logits, mask)

Curriculum:
  warm-up epoch: lambda(e) = 0
  ramp epoch: lambda(e) -> lambda_max (선형 증가)
  steady epoch: lambda(e) = lambda_max
```

- PyTorch `F.max_pool2d` 기반의 2D morphology로 GPU 상에서 경계 띠를 즉석 생성하는 구상.
- Static 모델은 λ 고정. Curriculum 모델은 초기 영역 학습 후 경계 가중치 증가.
- Kervadec의 distance-transform 기반 Boundary Loss와 **비교하는 연구**이며, 수학적으로 같은 손실 함수라고 주장하지 않음.
- `DT-free`는 사전 distance transform을 만들 필요가 없다는 주장임. 원고에 '추가 메모리 없음/미분 가능'과 같은 표현이 있어도 실제 성능·메모리 프로파일 없이 절대적 주장으로 과장하지 않을 것.

#### 2.4 논문 PDF에 기록된 재현 설정

| 항목 | 원고 기재 값 |
|---|---|
| 데이터 | ISIC 2018 Task 1, 총 2,594장의 학습용 이미지 |
| split | 학습 2,335장 / validation 259장 (9:1) |
| 해상도 | image/mask 256×256 |
| 모델 | 표준 U-Net, encoder 64→128→256→512, bottleneck 1024 |
| optimizer | Adam, learning rate 1e-4 |
| 학습 | batch size 8, 30 epochs |
| augmentation | horizontal·vertical flip 0.5, ±30° rotation, ColorJitter 0.2 |
| loss 비교 | BCE; BCE+Dice; Focal+Dice; BCE+Tversky; Kervadec; Static Boundary BCE+Dice; Curriculum Boundary BCE+Dice |
| ablation | λ, λmax, warm-up/ramp schedule, boundary kernel k=3/5/7 |
| seed | 42, 2024, 7 (3개) |
| 지표 | Dice, IoU, Boundary Dice, Boundary IoU, HD95 |
| 통제 실험 | 논문에 총 **24개**라고 기재 |

#### 2.5 원고에 기재된 정량 결과 — 검증 단계 주의

- **단일 seed=42에서:** 논문 본문은 Curriculum의 Dice **0.8840**, IoU **0.8123**을 기록. 같은 부분에 HD95 **8.99**라고 적음.
- **3-seed 평균을 포함한 초록:** Curriculum Boundary IoU **0.319**, HD95 **10.24**. BCE 대비 Boundary IoU **+9.6%**, HD95 **−10.3%**.
- **연산 시간:** 원고는 Boundary loss forward 계산이 Kervadec 비교 대비 약 **150배 빠르다**고 주장. 본문 표에서는 **0.30 ms vs 45.8 ms**라는 수치를 제시함(근사 비율 153배). 이는 전체 네트워크 추론이 150배 빠르다는 뜻이 아님.
- **주의:** 단일 seed와 multi-seed 평균의 HD95가 다르다. 동일한 값처럼 섞어 쓰면 안 됨.
- **주의:** 원고가 24개 실험과 재현성을 기술하지만, 별도 원본 train log, checkpoints 및 원시 seed별 결과 CSV까지 현재 독립적으로 확인한 것은 아님.

#### 2.6 5월 당시 검토한 논문 보완점

- 단일 데이터셋(ISIC 2018) 및 표준 U-Net 위주의 일반화 한계.
- ISIC 2017·PH2, U-Net++·Attention U-Net을 확장 후보로 논의했지만 실제로 모든 실험을 완료했다고 가정하지 않음.
- HD95에서 Kervadec이 특정 비교에서 더 우수한 결과를 보였다는 점을 숨기지 않도록 검토.
- 임상 관련 면적·둘레·비대칭성의 실제 downstream 평가 미흡을 한계로 구분.
- Abstract 길이, 표 나열식 분석, 제목·저자 중복, 기여 문장 과장 등 원고 교정 의견을 검토.

#### 2.7 파일 및 원본 증빙

- 확인된 논문: `14244002.pdf` (8페이지, 직접 작성·수정해 온 원고로 검색됨).
- 이전 기록에 `ISIC 2017` 언급이 있지만 **확인된 실험 결과의 주 데이터는 ISIC 2018**.
- 추후 Git 저장 시 원고 PDF의 연락처·개인정보와 실험 서버 경로·환자/의료 데이터 라이선스를 확인할 것.

### 3. 2026-07-18 — Atlas와 VoxelMorph를 학습한 기록

**[날짜 확인]** 2026-07-18 09:30 UTC 전후에 VoxelMorph 논문 설명을 요청하고, Atlas를 이용하는 의료영상 논문 및 2005년경 Atlas-based Segmentation 기초 개념을 질문함.

- Atlas는 기준 이미지/해부학 구조를 활용하는 접근이며, 모든 Registration이 Atlas-based인 것은 아님.
- VoxelMorph: moving image를 fixed image에 맞추는 변형장 추정과 spatial warp.
- 복원된 과거 관심사: registration, atlas-based segmentation, deformable/affine 차이, 전통적 정합과 학습 기반 정합을 연결해 이해하기.
- **수행 여부 주의:** 7/18의 해당 질문만으로 VoxelMorph 코드를 직접 구현하거나 사용했음을 입증하지 않음. 뇌혈관 Atlas 정합 직접 시도는 별도로 사용자가 확인한 사실.

### 4. 2026-07-29 — AUPRC와 CXR, 뇌혈관 영상

- **2026-07-29 10:34 UTC [날짜 확인]:** `AUPRC 0.41` 값을 제시하고 평가/해석을 질문함. **어느 모델·데이터셋·양성 클래스의 성적이었는지는 확인되지 않았으므로 피부 병변 실험 성능으로 연결하지 않음.** AUPRC 해석은 양성 클래스 prevalence 및 baseline을 참고해야 함.
- **2026-07-29 11:37 UTC [날짜 확인]:** CXR가 Chest X-ray(흉부 X선)인지 질문. 혈관 출혈/동맥류 같은 두개내 혈관 질환은 CXR보다 Brain CT/CTA/MRA 등의 영상에서 다뤄지는지 질문함.


### 4.1 2026-07-29 — VoxelMorph의 정합 연산에 관한 후속 질문 (추가 복원)

**[이전 대화 요약에서 확인 / 질문 원문·정확한 시각 미확보]** 7월 29일 VoxelMorph의 실제 계산 구조를 더 깊게 질문한 이력이 추가로 확인되었다. 아래 문장은 질문 원문이 아닌 논점의 재구성이다.

- **Deformation field:** moving 영상의 각 공간 위치가 fixed 영상과 어떻게 대응되는지를 표현하는 변위장. 모델이 직접 영상 픽셀의 분류값만 출력하는 것이 아니라 공간 변형을 추정한다는 점을 이해하려고 함.
- **Warp / spatial transformer:** 예측한 변형장에 따라 moving 영상을 샘플링하여 fixed 좌표계에 맞춘 warped image를 얻는 과정. 보간 과정 및 좌표계의 의미를 검토.
- **Backpropagation:** differentiable spatial transformer를 통해 유사도 손실 및 변형장 정규화 손실의 기울기가 네트워크로 전달되는 원리를 질문.
- **Auxiliary segmentation loss:** 고정 영상/이동 영상의 segmentation mask를 추가로 활용해 정합 과정에서 해부학적 구조를 보존하거나 대응시키는 방식에 관심.
- **동일한 변형장 적용:** moving 영상과 moving segmentation에 같은 공간 변형을 적용하되, 영상과 이산 라벨의 보간 방식은 구분해야 한다는 개념을 검토.
- **수행 여부:** 이 항목은 학습·질문 기록이다. VoxelMorph를 직접 학습·구현하거나 auxiliary loss 실험을 완료했다는 증거는 아니다.

### 5. 날짜가 회수되지 않은 연구실 관련 주제

다음 주제는 이전 대화 요약에서 등장하지만, **2026년 3~9월 어느 날인지 특정하지 못했고 직접 수행인지 논문 리뷰인지 아래에 구분**한다.

| 주제 | 남은 대화·맥락 | 근거 수준 |
|---|---|---|
| 태아 Trisomy 21 초음파 | 2022년 *Development and Validation...* 계열 태아 21번 삼염색체 초음파 스크리닝 연구, MICCAI와 AAAI 및 인용 수 비교 질문 | 과거 주제 요약, 정확한 제목·저자·출판 정보 미확인 |
| Chest X-ray 멀티라벨 | CXR label noise·uncertainty·Hybrid Bayesian Loss 관련 발표를 듣고 후기·요약 | 발표 청취/질문 맥락; 공동저자·실험 주장 금지 |
| NiftyReg vs SyN | B-spline, folding, deformation field, 보조 segmentation 입력·warping 비교 | 기술 질문 주제 회수; 실제 사용 소프트웨어 미확인 |
| GPU 환경 | RTX 3090 ×4, PyTorch 2.5.1+cu121 서버 환경이 이전 연구 맥락에 언급 | 과거 요약 수준; 당시 어느 모델을 어느 GPU에서 돌렸는지 미확인 |
| MICCAI 챌린지 참관 | MICCAI 챌린지 관련 발표/과제 참관과 혈관 라벨링을 경험으로 설명하려는 기록 | 참관·라벨링 관련 진술, 챌린지 참가/제출·수상과 구분 |

### 6. 2026-09 — 활동 종료 시점

**[직접 진술]** 2026년 9월까지 연구실에 소속되어 활동했다. **[미확인]** 그달에 수행한 구체적인 실험, 발표, 논문 제출·게재, 인수인계 내용이나 날짜는 현 자료로 회수되지 않음. 9월을 임의로 '최종 모델 완성', '챌린지 제출'로 채우지 않는다.

## 3~9월 질문 색인(원문 아님)

| 일시 UTC | 질문/행동 요지 | 범주 |
|---|---|---|
| 03-04 13:50 | 의료 AI 논문을 전문적으로 설명받고 학술적 핵심·수식·직관 파악 | 논문 리뷰 |
| 03-04 14:02 | Abstract→Figure→Conclusion 순서로 읽으면 되는가 | 논문 리뷰 |
| 05-17 13:49 | ISIC U-Net 학습·손실함수 비교·GPU 서버 실험과 저장 산출물 | 피부병변 |
| 05-17 13:53 | 경계 강조 손실 함수 논문/하계 학회 목표 | 피부병변 |
| 05-19 02:42 | Static Boundary Loss와 Curriculum λ 스케줄 | 피부병변 |
| 05-19 12:03 | 논문 구조 및 핵심 기여·실험 비교 개선 | 피부병변 |
| 05-19 12:28 | ISIC 2018 논문 수정안 검토·한계 정리 | 피부병변 |
| 07-18 09:30 | VoxelMorph, Atlas 기반 segmentation, 이전 Atlas 연구 개념 | 정합 |
| 07-29 10:34 | AUPRC 0.41 해석 | 평가 지표 |
| 07-29 11:37 | CXR란 무엇이며 뇌혈관 질환에 필요한 영상은? | 의료영상 |
| 07-29 (시각 미확인) | VoxelMorph deformation field, warp, spatial transformer와 역전파 | 정합 원리 |
| 07-29 (시각 미확인) | auxiliary segmentation loss와 moving segmentation 변형장 적용 | 정합 손실 |
| 08-19 11:42 | SwinCross와 VoxelMorph의 차이 | 정합/멀티모달 |
| 08-22 07:49 | Voreen centerline extraction, graph 오류와 보정 | 뇌혈관 |
| 08-22 10:21 | CoW feature extraction과 radius | 뇌혈관 |
| 08-23 03:06 | Circle of Willis centerline graph 논문 | 뇌혈관 |
| 08-23 03:12~03:17 | 52개 동맥류 위치 클래스 번호와 혈관 그림 매핑 | MICCAI/해부학 |
| 08-23 06:08 | TopCoW 데이터·혈관 라벨·분할 구성 | TopCoW |
| 08-23 08:45 | segment/bifurcation별 형태 특징 | 뇌혈관 |

> 질문 일시는 검색 시스템에서 회수된 UTC 기준이다. 한국 시각은 UTC+9. 원문이 아닌 요지이며, 대화 전체 메시지의 완전 목록이 아니다.

## 실무 기록 — GitHub에 공개하기 전

1. `research/2026-medical-ai-lab/README.md`에 본 문서 링크와 2026.03~09 기간 표기.
2. `papers/`에는 공유 가능한 본인 원고만 보관하고, 이메일·협업자 비공개 정보가 포함되어 있는지 확인.
3. `experiments/`에는 실험 설정 config, seed별 CSV, loss/metric plot, 환경 버전·명령어 보존. 실제 없는 로그를 만들지 않음.
4. `registration/`에는 Atlas 정합 **시도/실패의 재현 설명**을 남기되 환자 원본 영상·식별 정보는 공개 저장소에 넣지 않음.
5. 필요하면 ChatGPT 데이터 내보내기 `conversations.json`에서 검색어(`Atlas`, `MICCAI`, `TopCoW`, `Voreen`, `Skeleton`, `ISIC`, `Boundary`, `VoxelMorph`, `NiftyReg`, `SyN`)로 원문 대화를 추가 추출·중복 제거할 수 있음.

---

# Part II — Atlas Registration · MICCAI · TopCoW 연구 및 질문 기록 아카이브

> 연구실 활동 기간: **2026년 3월~9월** (사용자 직접 확인). 이 아카이브에서 복원된 뇌혈관 관련 질문은 8월에 집중되어 있으며, 3~9월 전체 대화가 확보된 것은 아님.
> 기록 범위: 과거 대화에서 회수 가능한 2026년 8월 중심의 뇌혈관 연구 질문, 2026년 11월 연구경험 재정리 대화, 기존 MD 자료.  
> 정리일: 2026-11-10  
> 목적: GitHub 연구 노트 / 포트폴리오용 개인 연구 이력 보존.  
> **증거 구분:** `[사용자 직접 확인]` 실제 수행을 사용자가 명시한 작업 · `[대화 확인]` 과거 질문/응답 일부가 검색된 내용 · `[기존 MD]` 대화 기반 이전 요약 파일 · `[이론 정리]` 기술 설명 · `[미확인]` 원본 코드·로그·원문 부재.
>
> **완전성 고지:** 이 문서는 *과거 전체 ChatGPT 대화 원문의 무손실 추출본이 아니다*. 검색으로 복원된 질문의 시각과 주제, 이전 작성 MD에 남은 분석, 확인된 활동을 최대한 통합한 **복원 기록**이다. 확인하지 못한 당시 질문 문장은 임의로 원문처럼 꾸미지 않았다. 아래 ‘질문 주제’는 원문이 확인되지 않은 경우 요지로 표시했다.

## 목차
1. [한눈에 보는 활동](#1-한눈에-보는-활동)
2. [날짜별 질문 및 연구 이력](#2-날짜별-질문-및-연구-이력)
3. [Atlas 정합 시도와 실패](#3-atlas-정합-시도와-실패)
4. [Skeletonization, Voreen, Centerline Graph](#4-skeletonization-voreen-centerline-graph)
5. [TopCoW 데이터와 윌리스 동맥륜](#5-topcow-데이터와-윌리스-동맥륜)
6. [형태학적 특징](#6-형태학적-특징)
7. [MICCAI 52-class 뇌동맥류 위치 매핑](#7-miccai-52-class-뇌동맥류-위치-매핑)
8. [의료영상 정합 논문 관련 추가 질문](#8-의료영상-정합-논문-관련-추가-질문)
9. [질문-답변 상세 복원](#9-질문-답변-상세-복원)
10. [수행/검토/미확인 구분](#10-수행검토미확인-구분)
11. [발표·자기소개서용 정리](#11-발표자기소개서용-정리)
12. [원본 증빙 체크리스트](#12-원본-증빙-체크리스트)

## 1. 한눈에 보는 활동

- **연구실 소속·활동 기간:** **2026년 3월~9월** (사용자 직접 확인).
- **아카이브에서 구체적 질문이 확인된 시기:** 주로 2026년 8월. 2026년 11월에 연구 경험 서술을 보완.
- **주의:** 8월은 확인된 세부 연구 질문의 집중 시기일 뿐, 전체 연구실 활동 기간을 뜻하지 않음.
- **핵심 주제:** 뇌혈관(특히 Circle of Willis) Segmentation → Skeleton/Centerline → Graph/Topology → 혈관 형태 특성 → 동맥류 위치 해석.
- **사용자 직접 확인:** 3D 뇌혈관 Skeletonization 관련 작업과 Atlas 기반 정합을 시도. Atlas 정합은 환자별 해부학적 변이가 커서 의도한 수준의 결과를 얻지 못함.
- **연구 검토:** TopCoW 데이터셋, Voreen 중심선 그래프, 해부학적 오류 보정, 혈관 형태학적 특징, 52-class 뇌동맥류 위치 체계.
- **구분:** 이론적으로 논의한 Graph topology 보정 알고리즘 전체를 직접 구현했다거나 MICCAI 챌린지에 모델을 제출했다는 증거는 없음.

### 전체 개념 흐름

```text
CTA / MRA 영상
  └─ Vessel segmentation mask (혈관 분할)
       └─ Skeleton / Centerline extraction
            └─ Node (끝점/분기점) + Edge (혈관 segment)
                 └─ Topology 검사: 잘못된 연결 / 불필요한 가지 / 루프
                      └─ Radius, length, curvature, tortuosity, bifurcation features
                           └─ 혈관 해부학 구조 / 동맥류 위치 분류의 맥락에서 해석
```

> 위 흐름은 **검토한 전체 연구 파이프라인**이며 모든 단계를 직접 구현했다는 뜻이 아니다.

## 2. 날짜별 질문 및 연구 이력

### 2026-08-19 — Registration과 SwinCross 관련 비교

- **대화 확인:** PET/CT 기반 SwinCross segmentation 논문 리뷰에서 VoxelMorph와 어떻게 다른지, 공간 정렬과 feature interaction의 차이를 연결해 질문.
- SwinCross: PET/CT 두 가지 영상 입력, Swin Transformer dual branch, stage별 Cross-Modality Attention(CMA), U-Net decoder 구조를 분석.
- 회수된 당시 설명: HECKTOR 224 cases·144³, TCIA HNC 122 cases·128³, Dice 0.769, Swin UNETR 0.754 대비 CMA 0.769. **이 수치는 당시 대화의 서술이며 논문 재검증 전 확정 지표로 인용하지 말 것.**
- 기술적 구분: VoxelMorph는 fixed/moving 영상 간 공간변형장(deformation field)을 추정하여 영상 좌표를 warp하는 **registration**; SwinCross CMA는 영상 특징을 교환하는 **feature fusion**이므로 물리적 영상 정합과 다름.
- 검토한 한계: PET/CT 정렬 오차, 3D Transformer 계산/메모리 비용, 두 모달리티 의존, 다른 환자군 일반화.
- **주의:** 이때 VoxelMorph를 실제로 실행했다는 증거는 없음.

### 2026-08-22 07:49:47 UTC — TopCoW 논문 2.2, Voreen Centerline Extraction

- **대화 확인:** TopCoW 관련 논문의 `2.2 Voreen centerline extraction` 부분을 질문.
- 논점: 자동 추출한 Centerline Graph가 처음부터 정확한가, 왜 후처리가 필요한가.
- 검토된 사례: invalid connection, self-loop, extra/spurious branch, 해부학적으로 맞지 않는 edge.
- 검토한 후처리: anatomy/rule-based node extraction, selective segment merging, spurious-edge removal, 전문가(CoW expert) 확인.
- 복원된 **구체적인 잘못된 연결 사례**: `R-ICA ↔ R-ACA`, `Acom ↔ L-ACA`, `L-ICA ↔ L-Pcom`, `L-ICA self-loop`. 이들은 논문/그래프 사례로 검토한 것으로, 본인의 데이터에서 직접 발견했다는 증거는 없음.

### 2026-08-22 10:21:39 UTC — 논문 2.3, CoW Feature Extraction

- **대화 확인:** `2.3 CoW feature extraction` 부분을 질문.
- 논점: node/edge 속성, Voreen radius와 cross-section 기반 CE radius 차이, 혈관 segment 및 bifurcation을 어떻게 정의하는가.
- 회수된 요소: segment 단위 반지름·길이·굴곡도·곡률, bifurcation 단위 각도 및 굵기 비율.

### 2026-08-23 03:06:44 UTC — Circle of Willis Centerline Graphs 논문 및 52-class 위치표

- **대화 확인:** 「Circle of Willis Centerline Graphs: A Dataset and Baseline Algorithm」과 관련 내용 질문.
- **03:12:41 UTC:** MICCAI 맥락의 52개 동맥류 위치 클래스 표를 제시하고 혈관 그림과 매핑하려 함.
- **03:13:03 UTC:** 혈관 위치 지도 사진 요청.
- **03:17:26 UTC:** “1~52번을 실제 혈관 그림에 표시한 이해하기 쉬운 한 장짜리 지도”를 요구한 기록 확인.
- 당시 설명에서 식별되는 예시 라벨: 17=BA tip, 28=Right ICA C7–PCom junction, 46=Left M1 trunk. **원표 재확인 필요.**

### 2026-08-23 06:08:45 UTC — TopCoW 데이터 구성

- **대화 확인:** TopCoW의 환자 수, CTA/MRA 영상 수, 혈관 라벨, 데이터 분할을 질문.
- 과거 대화에 기록된 수치: **200명 / CTA+MRA 총 400 images / train 125, validation 5, test 70 / 13 artery labels**.
- 주의: 원 논문 또는 챌린지 버전·데이터 공개 범위에 따라 다를 수 있으므로 저장 당시 회수된 값으로만 보존함.
- 중요 구분: **TopCoW의 13개 혈관 라벨**과 **별도로 다룬 52개 동맥류 위치 클래스**는 같은 라벨 체계로 합치지 말 것.

### 2026-08-23 08:45:36 UTC — Centerline features 추가 검토

- **대화 확인:** CE radius, 혈관 segment별 특징, bifurcation별 특징을 이어서 질문.
- 당시 답변 요지: segment features로 radius, centerline length, tortuosity, spline 기반 curvature 검토; 분기점에 3개 각도, 주요 분기점에서 radius/area difference·ratio, area-sum ratio, bifurcation exponent 검토.
- 당시 주요 분기 구조로 BA 및 양측 ICA 3곳, 작은 분기 구조로 2 Acom 및 4 Pcom 관련 표현이 회수됨. 이는 **당시 자료에서의 분기점 단위 구분 설명**이며 실제 환자에서 모두 존재한다는 주장이 아님.

### 2026-11-05 — 과거 8월 연구활동 재구성

- 당시 질문들: “과거에 MICCAI 관련 무엇을 했나”, “8월 동맥류 연구 정리”, “GitHub/자소서에 쓸 수 있게 MD 작성”, “Circle of Willis 포함됐나”, “Skeleton 작업도 했다”, “Atlas 정합을 했으나 개인별 혈관 변이 때문에 실패했다”.
- 이 과정에서 초기 연구 요약 MD에 없던 **직접 수행 범위(스켈레톤 및 Atlas 정합)**와 **실패 사례**가 사용자 진술로 보강됨.
- 이후 생성된 기존 파일들의 내용을 이 아카이브에 통합함.

## 3. Atlas 정합 시도와 실패

### 3.1 수행 사실 — 사용자 직접 확인

- 2026년 8월경 뇌혈관 관련 실험에서 Atlas 기반 정합 시도.
- 환자마다 Circle of Willis 혈관 위치, 굵기, 분지 및 연결 형태가 상당히 달랐음.
- 따라서 공통 Atlas를 통한 기대한 수준의 대응에 실패.
- 정확한 사용 Atlas/도구/영상 파일, 정합 단계, 평가 지표, 오류 영상은 현재 확보하지 못함.

### 3.2 왜 실패했는지에 대한 기술적 분석

1. **Spatial alignment ≠ anatomical correspondence:** 큰 구조가 공간적으로 겹쳐도 같은 분기점·혈관 segment를 가리킨다는 보장이 없음.
2. **CoW variability:** ACom/PCom 등 연결 존재 여부와 형태가 환자마다 달라 고정된 구조의 Atlas만으로 전체 변이를 설명하기 어려움.
3. **Topology mismatch:** 두 환자의 실제 혈관 연결 관계가 다르면 연속 좌표 변형만으로 서로 다른 그래프 위상을 해부학적으로 정당하게 일치시키는 데 한계가 있음.
4. **Thin vessel sensitivity:** 가느다란 가지의 작은 위치 차이 또는 segmentation 누락이 전체 대응 관계를 흐릴 수 있음.

이는 경험을 해석하기 위한 설명이다. **특정 알고리즘의 객관적 성능 실패를 입증한 실험 결과는 아님.**

### 3.3 당시 작업에서 확인되지 않은 항목

- Atlas 이름 및 환자 수
- 입력: 원본 CTA/MRA인지, vessel segmentation mask인지
- 초기 rigid / affine 수행 여부
- deformable registration 또는 구체적 optimizer
- ANTs/SyN/NiftyReg/VoxelMorph 실제 사용 여부
- Dice, TRE, HD95, Jacobian, landmark error 등 정량 지표
- 실제 학습/실행 코드와 정합 전후 캡처

### 3.4 추후 시도할 수 있는 대안 — *실제 수행 아님*

- 전뇌 영상 정합과 혈관 ROI 중심 정합 분리
- 다중 Atlas / template-free graph correspondence
- vessel mask 또는 segmentation-aware loss 활용
- bifurcation landmark / centerline 매칭
- overlap뿐 아니라 graph connectivity, anatomical segment correspondence까지 평가
- 변형장 regularity 및 folding(Jacobian determinant) 검사

## 4. Skeletonization, Voreen, Centerline Graph

### 4.1 용어 구분

| 용어 | 뜻 | 주의 |
|---|---|---|
| Vessel segmentation | 3D 혈관 마스크 | 연결 관계를 명시적으로 기술하지는 않음 |
| Skeleton | 두께를 축약한 복셀 구조 | spurs/noise/가지 단절 발생 가능 |
| Centerline | 각 혈관을 따라가는 기하학적 중심 경로 | Skeleton과 정확히 동일한 개념은 아님 |
| Centerline Graph | 끝점·분기점(nodes) 및 혈관 구간(edges) | 추출 후 위상 보정 필요할 수 있음 |
| Topology correction | 혈관 해부학에 맞게 연결성 검증·수정 | 임의로 모든 loop를 삭제해서는 안 됨 |

### 4.2 사용자의 수행 범위

- `[사용자 직접 확인]` 뇌혈관 스켈레톤 작업을 진행함.
- `[대화 확인]` Voreen 기반 centerline graph 생성 과정과 후처리 알고리즘 논문 리뷰.
- `[미확인]` Voreen 소프트웨어를 직접 실행했는지, 그래프 보정 코드를 직접 개발했는지는 현 자료로 확정 불가.

### 4.3 Voreen에서 논의된 실패 사례

| 오류 | 이전 대화에 등장한 예시 | 해석 |
|---|---|---|
| False edge | R-ICA—R-ACA | 실제 구조와 대조해 연결 적합성 확인 필요 |
| False edge | Acom—L-ACA | 추출한 그래프에서 잘못된 엣지 사례로 검토 |
| False edge | L-ICA—L-Pcom | 해부학/라벨링 기준과 비교 필요 |
| Self-loop | L-ICA self-loop | 인공 loop인지 실제 CoW 해부학 고리인지 구분 필요 |
| Spurious branch | 잡음에 의한 짧은 추가 가지 | pruning 대상이 될 수 있음 |
| Missing branch | 미세혈관 소실/가지 단절 | 가는 혈관의 connectivity 손실 |

> 연결 이름들은 논문 분석 과정에서 회수된 **예시 표현**. 해부학적으로 어떤 접합부를 포함할 수 있는지의 정의가 중요하므로, 원 논문 figure와 함께 검토해야 한다.

### 4.4 왜 segmentation Dice만으로 충분하지 않은가

Dice는 두 3D mask의 복셀 겹침을 평가한다. 하지만 작은 false-positive bridge 하나가 원래 분리된 혈관을 연결하거나, 작은 false-negative gap이 원래 연결된 혈관을 단절시킬 수 있다. 이런 차이는 Dice에 작게 보이더라도 centerline graph 최단경로와 분기점 분석을 크게 바꿀 수 있다.

## 5. TopCoW 데이터와 윌리스 동맥륜

### 5.1 당시 대화에 기록된 데이터셋 수치

- TopCoW 대상: **200명**
- 두 영상 모달리티: CTA, MRA
- 총 영상: **400** (CTA+MRA)
- 분할 수: train **125**, validation **5**, test **70** (환자 수 기준으로 과거 대화에 기재)
- 해부학적 라벨: **13개 혈관 라벨**
- **중요:** 위는 당시 대화에서 회수된 숫자다. 공식 dataset release와 class definition을 이용해 버전 재검증해야 한다.

### 5.2 관련 주요 혈관

- ICA: Internal Carotid Artery — 내경동맥
- ACA: Anterior Cerebral Artery — 전대뇌동맥
- MCA: Middle Cerebral Artery — 중대뇌동맥
- PCA: Posterior Cerebral Artery — 후대뇌동맥
- ACom: Anterior Communicating Artery — 전교통동맥
- PCom: Posterior Communicating Artery — 후교통동맥
- BA: Basilar Artery — 기저동맥

### 5.3 검토한 논문

- 제목(대화에 등장): **Circle of Willis Centerline Graphs: A Dataset and Baseline Algorithm**
- 당시 검토 범위: TopCoW 데이터 소개, Voreen centerline extraction, graph cleanup, CoW feature extraction.
- 정확한 연도, 저자, DOI, URL은 당시 대화 원문 및 논문 파일 재확보 전 미기입.

## 6. 형태학적 특징

### 6.1 Segment level

| 특징 | 당시 질문 내용 | 기술적 의미 |
|---|---|---|
| CE radius | Voreen radius와 cross-section 기반 CE radius 차이 | 혈관 단면에서 추정한 유효 반경 / 구현 세부는 논문 정의 확인 |
| Length | centerline length | 점들의 3D 경로 합계 |
| Tortuosity | 굴곡도 | 당시 회수된 식: `τ = C/L − 1`, C=곡선 경로 길이, L=양 끝점 직선거리 |
| Curvature | Spline 기반 곡률 | 당시 응답에 Splipy spline이 등장; 실제 실행 여부 미확인 |
| Volume | segment volume | 혈관 구간의 부피 |

### 6.2 Bifurcation level

- 분기점 각도 **3개**를 살펴봄.
- 주요 분기점(BA, 양측 ICA 기준의 총 3곳이라는 과거 설명)에서는 반지름 차/비, 단면적 차/비, 면적 합의 비, bifurcation exponent 등을 검토.
- ACom 및 PCom과 관련한 더 작은 분기부의 묶음(2 ACom + 4 PCom)도 과거 답변에 등장.
- **수치와 식의 구체 정의는 원 논문 확인 필요.** 직접 계산해 실험을 완료했다는 증거 없음.

## 7. MICCAI 52-class 뇌동맥류 위치 매핑

### 7.1 사용자의 요구

- MICCAI 관련 **52-class aneurysm location** 표를 실제 혈관 이미지 위에 번호로 표시하여 공간적으로 이해하려고 함.
- 2026-08-23 03:13:03 UTC: 혈관 위치 그림 요청.
- 2026-08-23 03:17:26 UTC: **1~52 모든 번호가 실제 혈관 그림 위에 표기된 한 장의 이해하기 쉬운 지도** 요청.
- 당시 **`뇌혈관 동맥류 위치 분류 지도.png`**라는 그림 파일이 생성된 기록이 있으나 이 MD에는 이미지를 재삽입하지 않음. 별도 원본 이미지 파일 확보 권장.

### 7.2 회수된 클래스 범위/예시 — 원표 대조 전까지 잠정

- Posterior circulation 관련 구간: **1–17**로 당시 정리.
- ICA 구간: **22–35**
- ACA 구간: **36–44**
- MCA 구간: **45–52**
- 과거 답변에는 **P1/P2 관련 18/19**도 등장하여 분류표를 반드시 통째로 다시 확인해야 함.

| Class | 과거 답변에서 나온 대응 | 상태 |
|---:|---|---|
| 17 | BA tip | 과거 답변 회수; 원본 표 검증 필요 |
| 18/19 | Right/Left P1P2 | 과거 답변 회수; 원본 표 검증 필요 |
| 28/29 | ICA C7–PCom 관련 좌/우 | 과거 답변 회수; 방향·세부 표기 원표 확인 |
| 36 | ACom | 과거 답변 회수; 원본 표 검증 필요 |
| 37/38 | A1 | 과거 답변 회수; 좌우 원표 확인 |
| 45/46 | M1 | 과거 답변 회수; 46=Left M1 trunk 예시 |

- 52개 클래스 전체 목록은 현재 확보한 텍스트에 없으므로 **누락된 클래스 번호의 혈관 명칭을 지어 채우지 않음.**
- TopCoW 13 vessel labels와 52 aneurysm location labels는 **별도의 체계**로 기록.

### 7.3 분류 접근의 당시 아이디어

- 동맥류의 3D 좌표만 보지 않고, 어느 혈관 segment/branch와 인접한지, 좌우와 분기점의 상대 위치를 이용하여 라벨을 설명.
- 예시: Left M1 trunk → class 46 / Right ICA C7–PCom junction → class 28 / BA tip → class 17 (당시 응답; 검증 필요).
- 이 단계는 **표 시각화 및 매핑 개념 검토**, 52-class 분류기 직접 구현으로 확인된 것이 아님.

## 8. 의료영상 정합 논문 관련 추가 질문

### 8.1 VoxelMorph

- 당시 이해한 핵심: `moving image`에서 `fixed image`에 맞추기 위한 dense deformation field를 추정하고, spatial transformer/warping으로 정렬.
- SwinCross의 CMA는 PET-CT 특징을 섞는 모듈이지 좌표 변형장을 계산하지 않으므로 별개.
- 정합이 틀어진 상황에서 segmentation-only cross attention은 spatial mismatch에 민감할 수 있어 전처리/robustness 연구 주제로 검토.

### 8.2 NiftyReg / SyN / B-spline / Folding / Segmentation-assisted registration

- 사용자가 과거 정합 공부를 했다는 범주별 기억은 있으나, **이 항목 각각에 대한 질문 원문, 시각, 사용 프로그램, 파라미터는 이번 검색에서 회수되지 않음.**
- 따라서 실제 사용했다고 주장하지 않는다.
- 참고 개념만 구분:
  - NiftyReg: 영상 정합 소프트웨어 도구군.
  - SyN: 비선형 정합을 위한 대칭적 정규화 계열 방법.
  - B-spline: 매끄러운 비선형 변형 표현에 쓰이는 방식.
  - Folding: 추정한 변형장으로 공간이 접히는 비정상적인 매핑 현상.
  - Segmentation assistance: anatomy mask/label 정보를 registration의 보조 손실이나 입력으로 활용하는 접근.
- 이들은 관련 기술 설명이지, 과거 실제 사용 기록이 아님.

## 9. 질문-답변 상세 복원

> `질문 주제(요지)`는 검색에 잡힌 과거 질문의 의미를 재서술한 것이다. **따옴표로 감싼 정확한 사용자 발화 원문이 아님.**

| 날짜(UTC) | 질문 주제(요지) | 회수된 핵심 답변 / 이후 의미 |
|---|---|---|
| 2026-08-19 11:42 | SwinCross와 VoxelMorph가 어떻게 다른가? | CMA는 모달리티 feature 교환, VoxelMorph는 실제 공간 warp를 수행. 정합 없이 fusion할 때 오정렬 문제. |
| 2026-08-22 07:49 | 논문 2.2 Voreen centerline extraction은 어떻게 하는가? | 혈관 mask→centerline/graph, 자동 추출 오류와 해부학적 후처리 필요. |
| 2026-08-22 07:49 | Invalid connections, loop, extra branches를 왜 보정하는가? | false edge, spurious branches, ICA self-loop 등은 혈관 네트워크를 왜곡할 수 있음. |
| 2026-08-22 10:21 | 2.3 CoW feature extraction의 radius/graph attribute는? | CE radius vs Voreen radius, segment/bifurcation 속성을 구분. |
| 2026-08-23 03:06 | Circle of Willis Centerline Graphs 논문 내용은? | 데이터셋과 baseline graph 알고리즘, 특징 분석. |
| 2026-08-23 03:12 | MICCAI 52-class 뇌동맥류 위치표를 혈관에 매핑하려면? | 혈관별 segment, laterality, branch를 함께 표시. |
| 2026-08-23 03:13 | 혈관 그림을 보여줄 수 있는가? | 위치 지도 레퍼런스 요청. |
| 2026-08-23 03:17 | 1–52 모든 클래스를 한 장에 표시해달라 | 번호가 실제 혈관에 대응된 시각화 요구. |
| 2026-08-23 06:08 | TopCoW 데이터셋 구성과 라벨은? | 당시 대화: 200명, 400 CTA/MRA, 125/5/70, 13 artery labels. |
| 2026-08-23 08:45 | CE radius, segment/bifurcation 특징은? | 반지름·길이·굴곡도·곡률, 각도·면적/반지름 비·exponent 등. |
| 2026-11-05 | 8월 동맥류 연구·MICCAI 경험을 어떻게 정리할까? | 포트폴리오 MD로 논문 리뷰와 직접 활동을 분리 기록. |
| 2026-11-05 | Circle of Willis도 했나? Skeleton은? Atlas 정합은? | Skeletonization 직접 수행, Atlas 정합 직접 시도, 개인별 해부학 변이 때문에 실패한 이력 반영. |

### 기존 MD에 재구성된 기술 질문 — **당시 발화 원문이 아님**

1. **분할이 정확하면 혈관 구조 분석도 정확한가?**  
   아니며 Dice가 좋더라도 혈관 간 거짓 연결/끊김이 있을 수 있음.
2. **이미지 대신 왜 그래프로 표현하는가?**  
   혈관 구간과 분기점을 명시적으로 연결하여 topology를 분석할 수 있음.
3. **Voreen 그래프를 그대로 사용해도 되는가?**  
   false connection, self-loop, spurious branch를 검사해야 함.
4. **반지름·분기각은 왜 계산하는가?**  
   혈관 형태의 정량화에 유용하나 동맥류 위험도 예측 성능/인과관계 입증은 별개.

## 10. 수행/검토/미확인 구분

| 항목 | 상태 | 근거 |
|---|---|---|
| 뇌혈관 Skeletonization | **직접 수행 확인** | 2026-11-05 사용자 진술 |
| Atlas 기반 뇌혈관 정합 | **직접 시도 확인(원하는 결과 미달)** | 2026-11-05 사용자 진술 |
| TopCoW 논문/데이터셋 분석 | **질문/리뷰 확인** | 2026-08-22~23 대화 |
| Voreen centerline extraction 구조 학습 | **질문/리뷰 확인** | 2026-08-22 대화 |
| Voreen 소프트웨어 직접 실행 | **미확인** | 코드/로그 없음 |
| ICA 연결 오류와 self-loop 사례 분석 | **논문 사례 검토 확인** | 2026-08-22 대화 |
| Topology correction 알고리즘 직접 구현 | **미확인** | 코드/실험 증빙 없음 |
| 형태학적 특징 추출 실제 계산 | **미확인** | 논문/방법 질문 확인, 실제 값 없음 |
| MICCAI 52-class 라벨표 및 시각화 요청 | **질문 확인** | 2026-08-23 대화 |
| 52-class 모델 학습 / 평가 | **미확인** | 결과표/코드 없음 |
| MICCAI 대회 제출/수상 | **미확인** | 제출 증빙 없음 |
| VoxelMorph 실제 구현 및 Atlas 실험에서 사용 | **미확인** | 비교 질문만 확인 |

## 11. 발표·자기소개서용 정리

### 11.1 GitHub README 한 줄

> Circle of Willis 뇌혈관 영상에서 Skeletonization과 Atlas 정합을 시도하고, 해부학적 변이로 인한 정합의 한계를 경험했습니다. TopCoW/Voreen 중심선 그래프와 혈관 위상 오류, 형태학적 특징을 논문 리뷰로 분석했습니다.

### 11.2 면접용 45초 설명

> 2026년 8월 뇌혈관 연구에서 혈관 스켈레톤 추출을 진행하고 Atlas 정합도 시도했습니다. 하지만 환자마다 윌리스 동맥륜의 모양과 분기 구조가 달라 기준 Atlas에 안정적으로 대응시키는 데 어려움이 있었습니다. 이후 TopCoW와 Voreen 중심선 그래프 연구를 검토하면서 분할 마스크가 유사하게 겹치는 것과 실제 혈관의 연결 관계가 올바른 것은 다르다는 점을 배웠습니다. 특히 잘못된 연결과 self-loop를 분석하며 의료영상에서 해부학적 구조 검증의 중요성을 이해했습니다.

### 11.3 향후 발전 방향 — 수행한 것으로 주장하지 않음

- Graph-based anatomical landmark matching.
- Multi-atlas 또는 patient-specific topology-aware alignment.
- Graph connectivity 기반 정합 평가 지표 설계.
- Voreen 결과와 직접 만든 3D skeleton 코드의 비교 검증.

## 12. 원본 증빙 체크리스트

### 확인할 원본 자료

- [ ] 2026-08-19 SwinCross/VoxelMorph 질문 원문 전체
- [ ] 2026-08-22 Voreen 2.2 및 2.3 질문·논문 그림 원본
- [ ] 2026-08-23 52-class 라벨 표 **1~52 전체**, 라벨 정의 출처
- [ ] `뇌혈관 동맥류 위치 분류 지도.png` 원본 시각화
- [ ] TopCoW 공식 버전·데이터셋 수·라벨표·해당 논문 PDF
- [ ] Skeletonization 직접 실행 스크립트, 라이브러리, 입력/출력 예시
- [ ] Atlas 이름, 정합 코드/명령어, 사용 변형 방식, 정합 전후 사진
- [ ] 실패했던 특정 환자 케이스 및 해부학적 변이 위치
- [ ] 정량 평가 기준과 실험 로그 (없다면 ‘미수행’ 명시)
- [ ] 연구실 발표 자료, 2026년 8월 노션·PPT, 당시 발표 피드백
- [ ] MICCAI 관련 활동이 참관/라벨링/분석/참가 중 어느 범위였는지 증빙

### 이미 작성됐던 참고 기록 파일명

- `2026-08_뇌동맥류_TopCoW_연구경험.md`
- `2026-08_뇌동맥류_TopCoW_연구경험_상세.md`
- `2026-08_뇌동맥류_TopCoW_연구경험_상세(1).md`
- `2026-08_뇌동맥류_TopCoW_연구경험_상세(2).md`
- `뇌혈관 동맥류 위치 분류 지도.png`

> **최종 주의:** 이 MD는 확인된 기록을 최대한 집대성한 버전이다. 정확한 원문 대화의 모든 메시지, 코드, 수식, 이미지 첨부를 포함하는 ChatGPT 데이터 내보내기(export)와 동일하지 않다. 원본 export를 확보하면 이 문서의 날짜별 표와 52-class 라벨을 대조하여 무손실에 가깝게 확장할 수 있다.