# tianchi

import pandas as pd
from pandas import Series,DataFrame

train_user=pd.read_csv('/python/tianchi/tianchi_fresh_comp_train_user.csv')
#len(train_user['user_id'].unique()) #2万去重人数

#计算user_item pairs
aa=train_user.groupby(['user_id','item_id']).count()
aa=aa['time'].count()

#计算user_item_purchased pairs
train_new=train_user.loc[train_user['behavior_type']==4]     #对列字段进行筛选
bb=train_new.groupby(['user_id','item_id','behavior_type']).count()
bb=bb['time'].count()
cc=float(bb/aa)
records=len(train_user)
userid=len(train_user['user_id'].unique())
"""
print records    23291027
print userid     20000
print aa         8858710
print bb         199819
print cc         0.0226
"""
