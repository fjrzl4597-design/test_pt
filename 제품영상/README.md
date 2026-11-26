# 제품 영상 작업 방식

제품마다 `_템플릿.md`를 복사해 `번호_제품명/작업.md`로 만들고 칸을 채워요.
예시: `01_원목보석함/작업.md`

## 순서

| 단계 | 할 일 | 크레딧 |
|---|---|---|
| ① 자료 모으기 | 상세페이지 캡처, 실제 사진 5~10장을 `번호_제품명/참고사진/`에 넣기 | 0 |
| ② 제품 카드 | 사진을 Claude에게 주고 "이 제품 카드 만들어줘": 고정 문장과 체크리스트 받기 | 0 |
| ③ 컷 구성 | 아래 컷 템플릿에 제품을 끼워 넣고, 컷마다 **실제 사진** 또는 **AI** 정하기 | 0 |
| ④ 이미지 생성 | AI 컷만. 체크리스트로 바로 통과/탈락 판정 | 0 |
| ⑤ 영상 생성 | 통과한 AI 컷만. **저가 모델 x1 테스트 → 고품질 최종** | 사용 |
| ⑥ 편집 | 실제 사진 컷(확대/이동 효과) + AI 컷 + 자막·음악 | 0 |

여러 제품은 단계별로 몰아서 해요: 3~5개 제품 ①~③ → 전부 ④ → 통과한 것만 ⑤.

## 실제 사진 / AI 고르는 기준

- **실제 사진**: 제품 구조가 전부 보이는 컷 (전체 모습, 열린 내부, 위에서 본 모습). AI가 가장 많이 틀리는 컷이에요.
- **AI**: 손이 움직이는 컷, 문제 상황 컷. 제품의 일부만 보이거나 구조가 덜 중요한 컷이에요.

## 컷 템플릿 (기본 7컷, 9:16)

| 컷 | 내용 | 보통 |
|---|---|---|
| 1 | 문제 상황 (어질러진 물건, 불편한 모습) | AI |
| 2 | 제품 등장 (닫힌 상태, 깔끔한 전체) | 실제 사진 |
| 3 | 기능 1: 손동작 | AI |
| 4 | 기능 2: 손동작 | AI |
| 5 | 기능 3: 손동작 | AI |
| 6 | 전체 구조 한눈에 | 실제 사진 |
| 7 | 정리된 결과 / 마무리 | 실제 사진 또는 AI |

## 배경 고정 문장 (모든 제품 공통)

```
SCENE (keep identical): white desk by a window with sheer white curtains and soft diffused daylight, a white lace doily under the product, a walnut ring-shaped bud vase with small white flowers and a stack of white coffee-table books in the background. Hands are a woman's with natural short nails, cream knit sweater sleeve. Photorealistic, looks like a real iPhone photo, no text, no logo, 9:16 vertical.
```

## 프롬프트 틀

```
[제품 고정 문장]
[배경 고정 문장]
SHOT: [이 컷에서 일어나는 일 한 줄. 카메라는 고정, 움직임은 하나만]
```

이미지 수정일 때는 맨 앞에 `Edit the attached photo. Keep the same camera angle and framing.`를 붙여요.

## 영상 생성 규칙

1. 이미지가 체크리스트를 모두 통과하기 전에는 영상을 만들지 않아요.
2. 한 컷에는 움직임 하나만 넣고, 카메라는 고정해요.
3. 시작 이미지와 끝 이미지는 같은 구도로 맞춰요.
4. 처음에는 저가 모델 x1로 테스트하고, 괜찮을 때만 고품질로 만들어요.
