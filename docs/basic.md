# Basic statistics

## T-test
두 집단간의 평균 차이가 유의미한지 확인할 때 사용.
- 두 집단은 독립적일 것.
> - 독립이 아니면 Pared t-test.
- 데이터가 정규분포를 따르는가.
> - 시각적 : Q-Q plot
> - 정량적 : Shapiro-Wilk normality test. H0=데이터가 정규분포를 따른다. alpha=0.05.
> - 정규분포를 따르지 않으면 Wilcoxon test.
- 집단이 둘인지.
> - 두 집단을 넘으면 ANOVA 시행.
