# Log

One entry for each recipe, selection or Track B model you train, newest at
the bottom. The numbers come from `experiments.csv`. "Why" and "what it means"
are in your own words: your agent asks you for them and does not make them up.
End the log with your plan for what to try next.

<!-- The form of an entry:

## <date> <tag> (Track A or B)
- changed: what is different from the run before
- why: your reason
- validation: 0.000 (before: 0.000)
- what it means: what you think the result says
-->

## 2026-11-10 baseline (Track A)
- changed: nothing; the starter recipe, trained with seed 0 and seed 1
- why: 기준점. seed만 바꿨을 때 점수가 운으로 얼마나 움직이는지 보려고
- validation: seed 0 0.4981, seed 1 0.4924 (차이 0.0057)

## 2026-11-10 baseline mistakes (curate.py mistakes, Track A)
- what I saw: 글자가 안 보이는 사진, 전통 건물, 고속도로를 잘 구별하지 못하는 듯

## 2026-11-10 no_flip (Track A)
- changed: removed T.RandomHorizontalFlip() from train_transform
- why: 글자가 중요한 단서일 것 같은데, 한글, 일본어, 한자는 뒤집으면 다른 글자가 되니까 구별이 잘 안 될 것 같아.
- validation: 0.4933 (before: baseline seed 0 0.4981, seed 1 0.4924)
- what it means: 모델이 글자보다 건물 모양, 색감, 도로 같은 다른 단서를 더 많이 쓰고 있을 수 있다. 그리고 같은 나라 끼리라서 헷갈리는 듯 (busan -> seoul, osaka -> tokyo)

## 2026-11-10 b1 (Track B)
- changed: mobilenet_v3_large (IMAGENET1K_V2) at 320, 6 epochs, every city drawn equally often (--balance), starter training photos
- why: 도시별로 고르게 뽑자고 한 이유는, 한 도시만 많으면 그 도시에 편향될 줄 알았다.
- validation: 0.554 (Track A baseline: 0.4981)
- what it means: 지금 생각해보면 그 도시에 대한 정확성은 좀 오르지 않았을까... 그리고 그래도 글자의 영향이 있었기 때문에 높게 나온 듯
