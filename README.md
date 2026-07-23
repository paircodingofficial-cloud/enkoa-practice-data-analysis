# 데이터 분석 실습자료

엔코아 AI캠퍼스 「데이터 분석 & AI 머신러닝 캠프」 **데이터 분석(pandas)** 실습용 주피터 노트북입니다.
수업 진도에 맞춰 자료가 추가됩니다.

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
| **openpyxl** | 엑셀(.xlsx) 읽기·쓰기 |
| **jupyterlab** · **ipykernel** | 주피터 노트북 실행 |

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
# (다른 터미널에서) 오늘 자료를 내작업으로 복사
mkdir -p 내작업/day06
cp day06_판다스_기초/*.ipynb 내작업/day06/
cp -r day06_판다스_기초/data 내작업/day06/
```

> Windows: `mkdir 내작업\day06` → `copy day06_판다스_기초\*.ipynb 내작업\day06\`
> 파일 탐색기에서 끌어다 복사해도 똑같습니다.

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
│   ├── 교안_01, 교안_02        수업 중 함께 진행
│   ├── 과제_LV1 / LV2 / LV3    기초 · 응용 · 통합
│   └── data/                  실습용 CSV
├── 내작업/                    ← 여기서 실습 (GitHub 에 안 올라감)
└── 업데이트.py                ← git pull 이 막혔을 때만
```

과제의 `# [자가채점]` 셀은 답을 쓴 뒤 실행해 에러가 없으면 통과입니다.
