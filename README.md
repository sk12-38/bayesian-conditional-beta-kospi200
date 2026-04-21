# Bayesian Conditional Beta for Korean ETF Market Regimes

## 한국어

이 저장소는 한국 주식형 ETF의 시간가변 시장 beta를 Bayesian conditional beta 모형과 2국면 Markov switching 모형으로 추정한 연구 프로젝트입니다. VKOSPI로 측정한 시장 불확실성이 ETF의 beta 노출과 국면 전환 확률에 어떤 영향을 주는지 분석합니다.

### 연구 질문

시장 불확실성은 한국 섹터 ETF의 conditional beta에 영향을 주는가? 또한 VKOSPI는 안정 국면과 위기 국면 사이의 전환을 설명하는 데 도움이 되는가?

### 방법론

- 고정 beta 기준 모형으로 static CAPM 추정
- 빈도론적 시간가변 beta 비교를 위한 rolling-window CAPM
- Normal 오차를 사용한 Bayesian conditional beta 모형
- Student-t 오차를 사용한 Bayesian conditional beta 모형
- 2국면 Bayesian Markov switching 모형
- VKOSPI 표준화 변수를 이용한 국면 전환 방정식
- MCMC posterior sampling 및 posterior interval 분석

### 주요 결과

Markov switching 모형은 표본을 저불확실성 국면과 고불확실성 국면으로 구분합니다.

- 저불확실성 국면 beta: `1.1176`, 95% 구간 `[1.0863, 1.1501]`
- 고불확실성 국면 beta: `0.8741`, 95% 구간 `[0.7736, 0.9695]`
- 저불확실성 국면 변동성: `0.011352`
- 고불확실성 국면 변동성: `0.025585`
- 고불확실성 국면 지속성에 대한 VKOSPI 효과: `1.1758`, 95% 구간 `[0.4446, 1.9070]`

### 주요 파일

- `notebooks/Bayesian_Conditional_Beta_MS.ipynb`: 데이터 로딩, 모형 추정, MCMC sampling, 국면 분석, 결과 저장을 수행하는 메인 노트북
- `notebooks/Bayesian_Results_Analysis.ipynb`: 저장된 결과를 이용해 그림과 요약 분석을 재생성하는 보조 노트북
- `paper/Bayesian_Conditional_Beta_Term_Paper.pdf`: 최종 보고서
- `results/figures/`: 보고용 그림
- `results/tables/`: 국면 parameter와 전환 효과 요약 표

### 데이터

원천 시장 데이터는 라이선스와 재배포 제약 때문에 포함하지 않았습니다. 메인 노트북을 다시 실행하려면 `Data/merged_data.csv` 경로에 날짜, ETF 초과수익률, KOSPI200 초과수익률, VKOSPI 열을 포함한 병합 데이터를 준비해야 합니다.

## English

This repository estimates time-varying market beta for a Korean equity ETF using Bayesian conditional beta models and a two-regime Markov switching framework. The analysis focuses on whether market uncertainty, proxied by VKOSPI, changes beta exposure and regime transition dynamics.

### Research Question

Does market uncertainty affect the conditional beta of a Korean sector ETF, and does VKOSPI help explain transitions between calm and crisis regimes?

### Methodology

- Static CAPM for a fixed-beta baseline
- Rolling-window CAPM for frequentist time-varying beta estimates
- Bayesian conditional beta model with Normal errors
- Bayesian conditional beta model with Student-t errors
- Two-regime Bayesian Markov switching model
- VKOSPI-standardized transition equation for regime dynamics
- MCMC posterior sampling and posterior interval analysis

### Key Results

The Markov switching model separates the sample into low-uncertainty and high-uncertainty regimes.

- Low-uncertainty regime beta: `1.1176`, 95% interval `[1.0863, 1.1501]`
- High-uncertainty regime beta: `0.8741`, 95% interval `[0.7736, 0.9695]`
- Low-uncertainty regime volatility: `0.011352`
- High-uncertainty regime volatility: `0.025585`
- VKOSPI effect on high-uncertainty persistence: `1.1758`, 95% interval `[0.4446, 1.9070]`

### Main Files

- `notebooks/Bayesian_Conditional_Beta_MS.ipynb`: Main notebook for data loading, model estimation, MCMC sampling, regime analysis, and result export
- `notebooks/Bayesian_Results_Analysis.ipynb`: Supplementary notebook for regenerating figures and summary analysis from saved results
- `paper/Bayesian_Conditional_Beta_Term_Paper.pdf`: Final report
- `results/figures/`: Exported figures used for reporting
- `results/tables/`: Compact result tables for regime parameters and transition effects

### Data

Raw market data is excluded because of data licensing and redistribution constraints. To rerun the main notebook, prepare `Data/merged_data.csv` with date, ETF excess return, KOSPI200 excess return, and VKOSPI columns.
