1. Get Rank in Python
```
# Compute different types of ranking
df['rank_min'] = df['values'].rank(method='min')        # [10, 10, 10, 20] will min rank as [1, 1, 1, 4] (not dense)
df['rank_max'] = df['values'].rank(method='max')        # [10, 10, 10, 20] will min rank as [3, 3, 3, 4] will rank as max rank (not dense)
df['rank_avg'] = df['values'].rank(method='average')    # [10, 10, 10, 20] will avg rank 10s as [2, 2, 2, 4] will rank as max rank (not dense)
df['rank_dense'] = df['values'].rank(method='dense')    # 


```
