# Basic statistics
```
from scipy import stats 
```
## T-test
두 집단간의 평균 차이가 유의미한지 확인할 때 사용.

1. 두 집단은 독립적일 것.
> - 독립이 아니면 Pared t-test.
2. 데이터가 정규분포를 따르는가.
> - 시각적 : Q-Q plot
> - 정량적 : Shapiro-Wilk normality test. H0=데이터가 정규분포를 따른다. alpha=0.05.
> - 정규분포를 따르지 않으면 Wilcoxon test.
3. 집단이 둘인지.
> - 두 집단을 넘으면 ANOVA 시행.

> - T-score = (mA-mB)/[SAB(1/nA + 1/nB)] : 
> - SAB = sqrt([(nA-1)SA^2 + (nB-1)SB^2]/(nA+nB-2))

```
# T-test
stats.ttest_ind(group1, group2, equal_var=False) # Default equal_var=True
# 분산이 같다고 가정할지, 아닐지 결정

# Shapiro-Wilk test
stats.shapiro(group1)

# 
```
## kolmogorov-Smirnov test
연속형 데이터가 정규분포를 따르는지 확인할때 쓰는 검정방법.
