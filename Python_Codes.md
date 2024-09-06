1. Get Rank in Python
```
# Compute different types of ranking
df['rank_min'] = df['values'].rank(method='min')        # [10, 10, 10, 20] will min rank as [1, 1, 1, 4] (not dense)
df['rank_max'] = df['values'].rank(method='max')        # [10, 10, 10, 20] will min rank as [3, 3, 3, 4] will rank as max rank (not dense)
df['rank_avg'] = df['values'].rank(method='average')    # [10, 10, 10, 20] will avg rank 10s as [2, 2, 2, 4] will rank as max rank (not dense)
df['rank_dense'] = df['values'].rank(method='dense')    # 

```

2. GroupBy with Concat - Remember that col goes to **INDEX** when GroupBy is done

```
df = pd.concat([fb_eu_energy, fb_asia_energy, fb_na_energy], axis=0)

df = df.groupby('date')[['consumption']].sum()

df['date'] = df.index

df.head()

max_energy = max(df['consumption'])
print(max_energy)
```

3. Merge and Remove Duplicates
```
df = airbnb_hosts.merge(
                airbnb_guests,    
                left_on= ['nationality', 'gender'], 
                right_on = ['nationality', 'gender'], 
                how='left')

df = df[['host_id', 'guest_id']]

df = df[~df.duplicated()]
```

4. Use agg with GroupBy
```
import pandas as pd
import numpy as np

facebook_complaints['processed'] = facebook_complaints['processed'].astype(int)
grouped = facebook_complaints.groupby(['type']).agg({'processed':'sum','complaint_id':'size'}).reset_index()    # size might be replaced with count
grouped['processed_rate'] =grouped['processed']/grouped['complaint_id']
result = grouped[['type','processed_rate']]
```