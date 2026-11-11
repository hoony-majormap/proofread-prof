# proofread-prof

보고서·기획서·제안서·공문·회의록 같은 업무 문서와 발표 슬라이드(.pptx/.key/PDF)를 위한 한국어 교정교열 Claude Code 스킬입니다.

논문용 스킬 [Eunhye890/paper-proofread](https://github.com/Eunhye890/paper-proofread)의 청크 단위 정밀 점검 방식을 바탕으로, 학술 인용 점검 대신 아래를 봅니다.

- 맞춤법 · 띄어쓰기 · 오탈자 (표 셀, 차트, 발표자 노트까지)
- 문장 교열: 번역투, 이중피동, 업무 문서 군더더기
- 문체 통일: 개조식(`~함`/명사 종결) ↔ 서술형, 종결어미 혼용
- 숫자 · 단위 · 용어 일관성: 요약과 본문 수치 대조, `%`/`%p`, 합계 검산, 날짜·요일
- 구조: 보고서 두괄식·번호 체계 / 슬라이드 제목-본문 일치·불릿 병렬·밀도·출처·목차

> 논문·학술 원고는 `paper-proofread`를 쓰세요. 두 스킬을 함께 설치해도 대상에 따라 나뉘어 동작합니다.

---

## 설치

Claude Code 채팅창에 그대로 붙여넣으세요.

```
이 깃허브 레포를 클로드 스킬로 깔아줘: https://github.com/hoony-majormap/proofread-prof
```

직접 설치하려면:

**Mac / Linux**

```bash
git clone https://github.com/hoony-majormap/proofread-prof.git ~/.claude/skills/proofread-prof
```

**Windows (PowerShell)**

```powershell
git clone https://github.com/hoony-majormap/proofread-prof.git $HOME\.claude\skills\proofread-prof
```

설치 후 새 세션을 열면 인식됩니다. 업데이트는 `git -C ~/.claude/skills/proofread-prof pull`.

---

## 사용 예

```
이 발표자료 교정해줘 [deck.pptx]
```

```
결과보고서 제출 전에 오탈자랑 숫자 맞는지 봐줘 [report.docx]
```

```
이 슬라이드 맞춤법만 봐줘, 수정본은 pptx로 줘
```

옵션은 말로 지정합니다: `엄격하게`(aggressive) / `오류만`(conservative), `맞춤법만`(surface), `숫자만`(numbers), `개조식으로 통일`, `외부 제출용`.

---

## 출력

1. **교정표** — 위치(S7 불릿 2, §3 문단 1 등) / 심각도 / 유형 / 원문 / 수정안 / 사유
2. **수정본** — `.md` 기본. 요청 시 트랙체인지 `.docx` 또는 서식을 유지한 `_proofread.pptx`(원본은 덮어쓰지 않음)
3. **요약** — 반드시 고칠 것 Top 3, 반복 패턴, 문체·용어 통일안, 수치 불일치 목록

심각도: 🔴 error (반드시 수정) / 🟡 suggest (권고) / 🔵 style (선택)

---

## 구조

```
proofread-prof/
├── SKILL.md              # 스킬 본체
├── references/
│   └── rules_ko.md       # 맞춤법·문체·숫자·보고서·슬라이드 규칙
└── README.md
```

## 크레딧

점검 흐름(청크 분할 → 순차 점검 → 통합 출력)과 공통 한국어 규칙 일부는 [Eunhye890/paper-proofread](https://github.com/Eunhye890/paper-proofread)를 바탕으로 했습니다.
