# Treaty KR

> 대한민국이 체결한 조약을 Git으로 관리합니다.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) [![data](https://img.shields.io/badge/data-Markdown-blue)](kr/) [![source](https://img.shields.io/badge/source-법제처_DRF_OpenAPI-orange)](https://open.law.go.kr)

대한민국이 체결한 **조약·협약·협정** 을 Markdown + YAML frontmatter 로 변환하여 Git 저장소에서 관리합니다. 각 조약은 발효일자를 Git commit date 로 갖고, 조약명·체결국·발효일자·조약번호·본문을 메타·본문으로 보관합니다.

법령·행정규칙·판례·해석례·헌재결정례·자치법규에 이어, **국제 조약**까지 Git 으로 추적해 국내법과 국제법의 연결을 한 곳에서 관리합니다.

## 왜 필요한가?

조약은 **국내법과 동일한 효력**을 가지며(헌법 제6조), FTA·인권·환경·조세·범죄인 인도 등 실무에서 직접 적용됩니다.

```
한·미 FTA (조약 제2125호)
  └─ 관세법 (시행규칙 별표)
       └─ 한·미 협력 사례 처리
```

## 빠른 시작

```bash
git clone https://github.com/wellsa-ai/treaty-kr.git
cd treaty-kr

# 특정 조약 보기
cat kr/2024/대한민국과_OO국_간의_조세조약.md

# 특정 국가와의 조약 모두 검색
grep -rl "미합중국" kr/
```

## 구조

```
kr/{발효연도}/
  {조약명}.md            # 조약 본문
  ...
```

## 메타데이터 (YAML Frontmatter)

```yaml
---
조약명: "대한민국과 OO국 간의 조세조약"
조약구분: "양자조약"
체결국: ["대한민국", "OO국"]
체결일자: "2024-03-15"
발효일자: "2024-06-15"
조약번호: "제2XXX호"
주관부처: "외교부"
출처: "https://www.law.go.kr/조약/(2XXX)"
---
```

## 자동 업데이트

매일 [국가법령정보센터 DRF API](https://open.law.go.kr) 의 `target=trty` 를 체크하여 신규·개정 조약이 있으면 자동으로 커밋합니다.

- `pipeline/cron_update.sh` — 매일 06:00 KST
- `pipeline/cron_full_sweep.sh` — 매일 23:30 KST

## 관련 프로젝트

| 프로젝트 | 대상 | 설명 |
|---|---|---|
| [legalize-kr](https://github.com/legalize-kr/legalize-kr) | 법률·시행령 | 대한민국 법령 |
| [regulate-kr](https://github.com/wellsa-ai/regulate-kr) | 행정규칙·고시 | 전 부처 행정규칙 |
| [precedent-kr](https://github.com/wellsa-ai/precedent-kr) | 법원 판례 | 대한민국 법원 판례 |
| [interpretation-kr](https://github.com/wellsa-ai/interpretation-kr) | 법령해석례 | 법제처 법령해석례 |
| [constitution-kr](https://github.com/wellsa-ai/constitution-kr) | 헌재결정례 | 헌법재판소 결정례 |
| [localrule-kr](https://github.com/wellsa-ai/localrule-kr) | 자치법규 | 지자체 자치법규 |
| **treaty-kr** (이 저장소) | 조약 | 대한민국 조약 |

## 활용 사례

- **국제 거래 실무**: FTA·조세조약 적용 사전 확인
- **인권·환경 연구**: 국제 조약 가입 현황·이행 추적
- **법률 통합 검색**: 국내법 + 조약 한꺼번에 검색 (예: [MiniLex](https://minilex.wellsa.ai))

## 데이터 출처

모든 조약 데이터는 [국가법령정보센터 DRF API](https://open.law.go.kr) 에서 가져옵니다. 조약 원문은 대한민국 정부 공공저작물로 자유롭게 이용 가능합니다.

## 라이선스

- 조약 원문: 공공저작물 (대한민국 정부)
- 저장소 구조·파이프라인 코드: MIT
