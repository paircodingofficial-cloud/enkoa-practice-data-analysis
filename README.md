# 데이터 분석 실습자료

엔코아 AI캠퍼스 「데이터 분석 & AI 머신러닝 캠프」 **데이터 분석·자연어 처리** 실습용 주피터 노트북입니다.
수업 진도에 맞춰 자료가 추가됩니다.

### 수록 자료

| 일차 | 주제 | 배우는 것 |
|---|---|---|
| **day06** | 판다스 기초 | DataFrame 조회·선택·정렬, 결측치·이상치, 형변환·문자열, 파생 변수 |
| **day07** | EDA·시각화 | 결합(merge·concat)·집계(groupby·pivot_table·사용자 정의 집계), Matplotlib·Seaborn 유형별 그래프 |
| **day08** | 기술통계·추론통계 | 대푯값·산포·상관, 확률분포, 표본분포·신뢰구간·p-value |
| **day09** | 가설검정·회귀분석 | 정규성·등분산 점검, t-검정·ANOVA·카이제곱과 사후검정, 효과크기, 회귀와 LINE 4가정 |
| **day10** | 데이터 분석 종합 실습 | H&M 커머스 데이터로 문제 정의 → 전처리 → EDA → 통계 검정 → 인사이트 리포트를 **스스로** 완성 |
| **day11** | 텍스트 전처리·분석 | 정규표현식·형태소·불용어, 빈도·워드클라우드, TF-IDF·n-gram·동시 출현 |

---

## ⚠️ 딱 하나만 기억하세요

> ### 배포된 자료는 **읽기 전용**입니다.
> ### 실습은 **`내작업/` 폴더에 복사해서** 하세요.

셀을 실행만 해도 파일이 바뀔 수 있으니, 원본은 건드리지 마세요.

---

## 1. 준비 (처음 한 번만)

```bash
# 자료 내려받기
git clone https://github.com/paircodingofficial-cloud/enkoa-practice-data-analysis.git
cd enkoa-practice-data-analysis

# uv 설치 — macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
# Windows(PowerShell): powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
#  설치 후 터미널을 새로 열어야 합니다.

# 파이썬 환경 구축 — 이 한 줄이면 끝!
uv sync
```

> ### ✅ `uv sync` **하나로 환경이 완성됩니다.**
> 이 저장소에는 `pyproject.toml` 과 `uv.lock` 이 들어 있어서,
> `uv sync` 를 실행하면 **파이썬 3.12 가상환경(`.venv`)** 과 **필요한 라이브러리 전부**가
> 자동으로 설치됩니다. 따로 하나씩 설치할 필요가 없어요.

### 이미 포함된 라이브러리

`uv sync` 를 하면 아래가 모두 깔립니다 (직접 설치 안 해도 됩니다).

| 라이브러리 | 용도 |
|---|---|
| **pandas** | 표(DataFrame) 데이터 분석의 핵심 |
| **numpy** | 수치 계산 (pandas 의 토대) |
| **matplotlib** · **seaborn** | 그래프·시각화 |
| **scipy** | 통계 계산 (정규분포·신뢰구간 등) |
| **openpyxl** | 엑셀(.xlsx) 읽기·쓰기 |
| **jupyterlab** · **ipykernel** | 주피터 노트북 실행 |
| **scikit-learn** | TF-IDF·CountVectorizer 텍스트 벡터화 |
| **kiwipiepy** | 한국어 형태소 분석 |
| **wordcloud** | 한글 워드클라우드 |
| **networkx** | 단어 동시 출현 네트워크 |

### 라이브러리를 더 추가하고 싶다면

새 라이브러리가 필요할 땐 `uv add` 로 추가합니다. 예:

```bash
uv add scikit-learn        # 라이브러리 1개 추가
uv add pandas matplotlib   # 여러 개도 한 번에
```

`uv add` 는 `pyproject.toml` 과 `uv.lock` 에 자동으로 기록해 줍니다.
**다만 지금은 위 목록이 이미 들어 있으니, `uv sync` 만 하면 실습에 필요한 건 다 준비됩니다.**

---

## 2. 실습하기

오늘 자료를 `내작업/` 으로 **복사한 뒤** 복사본을 열어 작업합니다.

```bash
# (다른 터미널에서) 오늘 자료를 내작업으로 복사 — day08 이라면
mkdir -p 내작업/day08
cp day08_기술통계_추론통계/*.ipynb 내작업/day08/
cp -r day08_기술통계_추론통계/data day08_기술통계_추론통계/images 내작업/day08/
```

> Windows: `mkdir 내작업\day08` → `copy day08_기술통계_추론통계\*.ipynb 내작업\day08\`
> 파일 탐색기에서 끌어다 복사해도 똑같습니다.
>
> **`data/` 와 `images/` 도 함께 복사하세요.** 노트북이 `data/` 에서 CSV 를 읽고,
> 설명 그림을 `images/` 에서 불러옵니다 — 빠뜨리면 표가 안 열리거나 그림이 깨집니다.

---

## 3. 새 자료 받기

```bash
git pull
uv sync      # 새 자료에 새 라이브러리가 필요할 수 있으니 함께 실행
```

### 잘 안 될 때

원본을 건드렸다면 아래 같은 메시지가 뜨면서 막힙니다.

```
error: Your local changes would be overwritten by merge
```

이때만 복구 도우미를 실행하세요.

```bash
uv run 업데이트.py
```

배포 원본을 되돌려 충돌을 없애고 새 자료를 받아옵니다.
`내작업/` 폴더와 여러분이 만든 파일은 **건드리지 않고**, 되돌리기 전 내용은 `.백업/` 에 보관합니다.

---

## 4. 폴더 구성

```
enkoa-practice-data-analysis/
├── pyproject.toml · uv.lock   ← 환경 정의 (uv sync 가 이걸 읽어 설치)
├── day06_판다스_기초/          ← 배포 원본 (읽기 전용)
├── day07_EDA_시각화/
├── day08_기술통계_추론통계/
│   ├── 교안_01, 교안_02        수업 중 함께 진행
│   ├── 과제_LV1 / LV2 / LV3    기초 · 응용 · 통합
│   ├── 실습_가이드.md           그날의 진행 체크리스트
│   ├── data/                  실습용 CSV
│   └── images/                교안에 들어가는 설명 그림
├── day09_가설검정_회귀분석/     (구성 동일 + 참고_AB테스트 · 참고_다중공선성)
├── day10_데이터분석_종합실습/   ← 여기는 구성이 다릅니다
│   ├── 01 · 02 · 03           번호가 곧 실행 순서 (전처리 → EDA → 통계)
│   ├── 실습_가이드.md           진행 체크리스트
│   └── data/hm/               H&M 고객·거래·상품 3개 CSV
├── day11_텍스트전처리_분석/
│   ├── 교안_01, 교안_02        정규표현식·형태소 → TF-IDF·연관 분석
│   ├── 과제_LV1 / LV2 / LV3    기초 · 응용 · 통합
│   ├── 실습_가이드.md
│   ├── data/                  영화·뉴스·상품 리뷰와 불용어
│   └── images/                개념도·완성 그래프
├── 내작업/                    ← 여기서 실습 (GitHub 에 안 올라감)
└── 업데이트.py                ← git pull 이 막혔을 때만
```

과제의 `# [자가채점]` 셀은 답을 쓴 뒤 실행해 에러가 없으면 통과입니다.
