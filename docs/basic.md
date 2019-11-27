# Basic statistics
```
from scipy import stats 
import seaborn as sns
import matplotlib.pyplot as plt
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

```
```
fig=sns.distplot(group1, kde=False, fit=stats.norm, label='G1')
fig=sns.distplot(group2, kde=False, fit=stats.norm, label='G2')
fig.lines[0].set_linestyle(":")
plt.title('G1: '+str(stats.shapiro(group1)[1])+', G2: '+str(stats.shapiro(group2)[1]))
plt.grid(ls='--',alpha=0.4)
plt.legend()
plt.savefig('dist',dpi=300)
```
## kolmogorov-Smirnov test
연속형 데이터가 정규분포를 따르는지 확인할때 쓰는 검정방법.

## Statistical error
1. Reporting measurements with unnecessary precision.
> - the smallest P value that need be reported is P < 0.001.
2. Dividing continuous data into ordinal categories without explaining who or how.
> - For exmaple, Height cm to ‘short, normal, and tall’. why you choose, how the boundaries are determined.
3. Reporting group means for paired data without reporting within-pair changes.
4. Using descriptive statistics incorrectly.
> - In markedly non-normal distributions, the mean and standard deviation do not communicate the shape of the distribution well. Instead, the median is recommended.
5. Using the standard error of the mean as a descriptive statistic or as a measure of precision for an estimate.
> - the mean and standard deviation are the preferred summary statistics for (normally distributed) data, and the mean and 95% confidence interval are preferred for reporting an estimate and its measure of precision. (95% CI = 2 SEM)
> - e.g. “The mean value was 72kg (95% CI = 70.4 to 73.6kg).
