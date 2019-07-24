# Apriori algorithm
: 거래가 빈번히 일어나는 아이템의 빈도를 구하는 알고리즘이며, 아이템들이 함께 거래될 빈도도 확인하는 할 수 있다.

Item(`I`), Dataset(`D`), Transanction(`T`), Support(`S`), Confidence(`C`)

## Item
: 거래에 사용되는 품목들. `I={i1,i2,...,in}`

## Dataset
: 거래가 일어나는 품목들의 집합. `D={d1,d2,...,dm}`

## Support
: 상품들(`X`)이 거래될 확률. `P(S)=N(X)/N(D)`

## Confidence
:  상품(`X`)이 선택된 뒤, 다른 상품(`Y`)이 선택될 확률

예)
di| subset
-|-
d1|{i1,i3}
d2|{i1,i4}
d3|{i2,i4,i5}
d4|{i3,i5,i6}
d5|{i2,i4,i7}
d6|{i3,i5,i7}

