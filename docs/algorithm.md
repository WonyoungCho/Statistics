# Apriori algorithm
: 거래가 빈번히 일어나는 아이템의 빈도를 구하는 알고리즘이며, 아이템들이 함께 거래될 빈도도 확인하는 할 수 있다.

Item(`I`), Dataset(`D`), Transanction(`T`), Support(`S`), Confidence(`C`), Lift(`L')

## Item
: 거래에 사용되는 품목들. `I={i1,i2,...,in}`

## Dataset
: 거래가 일어나는 품목들의 집합. `D={d1,d2,...,dm}`

## Support (지지도)
: 상품들(`X`)이 거래될 확률. `P(S)=N(X)/N(D)`

## Confidence (신뢰도)
:  상품(`X`)이 선택된 뒤, 다른 상품(`Y`)이 선택될 확률.

예)

|D| subset|
|-|-|
|d1|i1, i3|
|d2|i2, i4|
|d3|i2, i4, i5|
|d4|i3, i5, i6|
|d5|i2, i4, i7|
|d6|i3, i5, i7|

X={i2, i4} 일때, 빈번 확률
> P(X) = n(d2,d3,d5)/n(D) = 3/6 = 0.5. 즉, Support = 0.5 (50%).

X={i2, i4} 를 선택하고 Y={i5} 를 선택할 활률
> P(Y|X) = n(X∪Y)/n(X) = n(d3)/n(d2,d3,d5) = 1/3 = 0.33. 즉, Confidence = 0.33 (33%).

## Lift (향상도)
: 상품 `Y` 를 살 확률 대비, 상품 `X`를 샀을 때 상품 `Y` 를 살 확률.

Y={i5} 를 살 확률 대비, X={i2, i4} 를 선택하고 Y={i5} 를 선택할 활률이다.

1이면 X와 Y는 관계없다. 1보다 크면 X를 사면 Y를 살 확률이 크다. 1보다 작으면 X만 산다.

P(L) = Confidence/Expected_Confidence = [n(X∪Y)/n(X)]/[n(d3,d4,d6)/n(D)] = (1/3)/(1/2) = 0.67.
