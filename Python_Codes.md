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

5. Replace Multiple Values with a val in df, using apply and lambda
```
# Define a replacement function
def replace_values(x):
    return {
        1: 10,
        2: 20,
        3: 30
    }.get(x, x)  # Return x if it is not in the replacement dictionary

# Apply the replacement function to the entire DataFrame
df_replaced = df.applymap(replace_values)

print(df_replaced)

```

6. pd.factorize()

7. 0 > np.nan (less or greater is always False)

8. I have classes 1 to 3 in a df ---> return class that has all students with marks less than 70. how to do this with Pandas

9. A df has columns student, physics, maths cols
filter df for student with highest marks in physics and lowest marks in maths (2nd priority)

10. count the number of marks cols that have non-zero marks in a row and add in a col

11. I have 100+ cols
of them Name Roll_No Class have to be cols 1, 2, 3. how to do this?

12. print name of students that have 0 marks in all rows. There are multiple marks cols, check only in marks1 cols

13. why is this not removing updating values in df
   for i, r in non_nans_count.iterrows(): 
    r[0] = df.shape[0] - r[0]

