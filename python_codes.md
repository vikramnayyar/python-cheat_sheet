1. Get Rank in Python
```
# Compute different types of ranking
df['rank_min'] = df['values'].rank(method='min')
df['rank_max'] = df['values'].rank(method='max')
df['rank_avg'] = df['values'].rank(method='average')
df['rank_dense'] = df['values'].rank(method='dense')


```
