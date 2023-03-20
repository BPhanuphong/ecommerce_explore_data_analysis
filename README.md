# ecommerce_explore_data_analysis
This is one of Dads 5001 mini project that will explore data on ecommerce platform 


```python
import pandas as pd
import numpy as np
from datetime import datetime
import matplotlib.pyplot as plt
import seaborn as sns
```


```python
df = pd.read_csv('Ecommerce_mini_project.csv')
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 316949 entries, 0 to 316948
    Data columns (total 84 columns):
     #   Column                                  Non-Null Count   Dtype  
    ---  ------                                  --------------   -----  
     0   item_type                               316949 non-null  int64  
     1   discount                                303991 non-null  object 
     2   price_min                               316949 non-null  int64  
     3   item_has_video                          316949 non-null  object 
     4   userid                                  316949 non-null  int64  
     5   liked                                   316949 non-null  object 
     6   is_pre_order                            316949 non-null  object 
     7   is_adult                                316949 non-null  object 
     8   scraped_datetime                        316949 non-null  object 
     9   model_name                              289103 non-null  object 
     10  price                                   316949 non-null  int64  
     11  is_infant_milk_formula_product          316949 non-null  object 
     12  ctime                                   316949 non-null  object 
     13  should_show_amp_tag                     316949 non-null  object 
     14  stock                                   316949 non-null  int64  
     15  price_min_before_discount               304653 non-null  float64
     16  brand                                   309731 non-null  object 
     17  is_service_by_shopee                    316949 non-null  object 
     18  image                                   316949 non-null  object 
     19  price_before_discount                   316949 non-null  int64  
     20  is_preferred_plus_seller                316949 non-null  object 
     21  show_official_shop_label_in_title       316949 non-null  object 
     22  cod_flag                                316949 non-null  int64  
     23  modelid                                 316949 non-null  int64  
     24  price_max_before_discount               304653 non-null  float64
     25  label_ids                               316502 non-null  object 
     26  is_official_shop                        316949 non-null  object 
     27  global_sold                             203029 non-null  float64
     28  show_shopee_verified_label              316949 non-null  object 
     29  item_status                             316949 non-null  object 
     30  brand_id                                316949 non-null  int64  
     31  cb_option                               316949 non-null  int64  
     32  condition                               316949 non-null  int64  
     33  shipping_icon_type                      316949 non-null  int64  
     34  cmt_count                               316949 non-null  int64  
     35  name                                    316949 non-null  object 
     36  reference_item_id                       0 non-null       float64
     37  shopid                                  316949 non-null  int64  
     38  show_best_price_guarantee               316949 non-null  object 
     39  shopee_verified                         316949 non-null  object 
     40  estimated_days                          316949 non-null  int64  
     41  has_low_fulfillment_rate                316949 non-null  object 
     42  price_max                               316949 non-null  int64  
     43  has_lowest_price_guarantee              316949 non-null  object 
     44  status                                  316949 non-null  int64  
     45  bundle_deal_id                          316949 non-null  int64  
     46  is_alcohol_product                      316949 non-null  object 
     47  show_discount                           316949 non-null  int64  
     48  liked_count                             316949 non-null  int64  
     49  flag                                    316949 non-null  int64  
     50  welcome_package_type                    316949 non-null  int64  
     51  can_use_bundle_deal                     316949 non-null  object 
     52  is_non_cc_installment_payment_eligible  316829 non-null  float64
     53  is_prescription_item                    316949 non-null  object 
     54  normal_stock                            316949 non-null  int64  
     55  min_purchase_limit                      316949 non-null  int64  
     56  itemid                                  316949 non-null  int64  
     57  catid                                   316949 non-null  int64  
     58  show_recycling_info                     316949 non-null  object 
     59  is_mart                                 316949 non-null  object 
     60  item_has_post                           316949 non-null  object 
     61  historical_sold                         316949 non-null  int64  
     62  shop_location                           316949 non-null  object 
     63  current_promotion_reserved_stock        316949 non-null  int64  
     64  scraped_start_date                      316949 non-null  object 
     65  is_cc_installment_payment_eligible      316829 non-null  float64
     66  class_name                              316949 non-null  object 
     67  sold                                    316949 non-null  int64  
     68  discount_stock                          316949 non-null  int64  
     69  show_free_shipping                      316949 non-null  object 
     70  other_stock                             316949 non-null  int64  
     71  show_original_guarantee                 316949 non-null  object 
     72  raw_discount                            316949 non-null  int64  
     73  promotionid                             316949 non-null  int64  
     74  url                                     316949 non-null  object 
     75  badge_icon_type                         316949 non-null  int64  
     76  can_use_wholesale                       316949 non-null  object 
     77  is_partial_fulfilled                    316949 non-null  object 
     78  current_promotion_has_reserve_stock     316949 non-null  object 
     79  upcoming_flash_sale                     22274 non-null   object 
     80  bundle_deal_info                        45186 non-null   object 
     81  flash_sale                              11240 non-null   object 
     82  exclusive_price_info                    5158 non-null    object 
     83  ingest_date                             316949 non-null  object 
    dtypes: float64(6), int64(34), object(44)
    memory usage: 203.1+ MB
    


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>item_type</th>
      <th>price_min</th>
      <th>userid</th>
      <th>price</th>
      <th>stock</th>
      <th>price_min_before_discount</th>
      <th>price_before_discount</th>
      <th>cod_flag</th>
      <th>modelid</th>
      <th>price_max_before_discount</th>
      <th>...</th>
      <th>catid</th>
      <th>historical_sold</th>
      <th>current_promotion_reserved_stock</th>
      <th>is_cc_installment_payment_eligible</th>
      <th>sold</th>
      <th>discount_stock</th>
      <th>other_stock</th>
      <th>raw_discount</th>
      <th>promotionid</th>
      <th>badge_icon_type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>316949.0</td>
      <td>316949.000000</td>
      <td>316949.0</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>304653.000000</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>3.169490e+05</td>
      <td>304653.000000</td>
      <td>...</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>316829.000000</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>316949.000000</td>
      <td>3.169490e+05</td>
      <td>316949.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>0.0</td>
      <td>5826.871629</td>
      <td>0.0</td>
      <td>6842.930992</td>
      <td>231.559229</td>
      <td>8929.532304</td>
      <td>8110.809812</td>
      <td>0.682763</td>
      <td>1.168458e+11</td>
      <td>10908.731698</td>
      <td>...</td>
      <td>100215.086799</td>
      <td>5087.556067</td>
      <td>6.562964</td>
      <td>0.390766</td>
      <td>221.332684</td>
      <td>2589.093356</td>
      <td>173.168989</td>
      <td>39.384343</td>
      <td>4.862378e+14</td>
      <td>0.233470</td>
    </tr>
    <tr>
      <th>std</th>
      <td>0.0</td>
      <td>7304.720851</td>
      <td>0.0</td>
      <td>8015.321658</td>
      <td>804.860872</td>
      <td>12014.080406</td>
      <td>12023.332042</td>
      <td>0.465401</td>
      <td>4.989618e+10</td>
      <td>13552.015133</td>
      <td>...</td>
      <td>290.707979</td>
      <td>13890.012883</td>
      <td>48.039579</td>
      <td>0.487923</td>
      <td>538.543273</td>
      <td>6834.859107</td>
      <td>1520.610166</td>
      <td>17.383550</td>
      <td>2.981477e+14</td>
      <td>1.430638</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.0</td>
      <td>131.000000</td>
      <td>0.0</td>
      <td>131.000000</td>
      <td>0.000000</td>
      <td>230.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>3.471427e+09</td>
      <td>230.000000</td>
      <td>...</td>
      <td>100001.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000e+00</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.0</td>
      <td>1359.000000</td>
      <td>0.0</td>
      <td>1699.000000</td>
      <td>1.000000</td>
      <td>1999.000000</td>
      <td>1899.000000</td>
      <td>0.000000</td>
      <td>8.036762e+10</td>
      <td>2990.000000</td>
      <td>...</td>
      <td>100010.000000</td>
      <td>219.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>12.000000</td>
      <td>51.000000</td>
      <td>0.000000</td>
      <td>26.000000</td>
      <td>1.141186e+14</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>0.0</td>
      <td>3489.000000</td>
      <td>0.0</td>
      <td>4499.000000</td>
      <td>23.000000</td>
      <td>5990.000000</td>
      <td>3499.000000</td>
      <td>1.000000</td>
      <td>1.231928e+11</td>
      <td>6999.000000</td>
      <td>...</td>
      <td>100013.000000</td>
      <td>1168.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>45.000000</td>
      <td>234.000000</td>
      <td>0.000000</td>
      <td>44.000000</td>
      <td>6.677588e+14</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>0.0</td>
      <td>7610.000000</td>
      <td>0.0</td>
      <td>9490.000000</td>
      <td>194.000000</td>
      <td>9999.000000</td>
      <td>9999.000000</td>
      <td>1.000000</td>
      <td>1.526733e+11</td>
      <td>13086.000000</td>
      <td>...</td>
      <td>100631.000000</td>
      <td>3976.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>142.000000</td>
      <td>811.000000</td>
      <td>0.000000</td>
      <td>54.000000</td>
      <td>6.802253e+14</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>0.0</td>
      <td>114642.000000</td>
      <td>0.0</td>
      <td>122842.000000</td>
      <td>67029.000000</td>
      <td>125310.000000</td>
      <td>134274.000000</td>
      <td>1.000000</td>
      <td>2.307300e+11</td>
      <td>134274.000000</td>
      <td>...</td>
      <td>100637.000000</td>
      <td>102765.000000</td>
      <td>1179.000000</td>
      <td>1.000000</td>
      <td>3719.000000</td>
      <td>263871.000000</td>
      <td>31439.000000</td>
      <td>94.000000</td>
      <td>7.089141e+14</td>
      <td>9.000000</td>
    </tr>
  </tbody>
</table>
<p>8 rows × 40 columns</p>
</div>



# Understand and prepare Data


```python
''' 
itemid = id of product in 1 link
modelid = option of product in itemid 
itemid can have many modelid
''' 
df[['itemid','modelid']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>itemid</th>
      <th>modelid</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13374366434</td>
      <td>134017795683</td>
    </tr>
    <tr>
      <th>1</th>
      <td>13374366434</td>
      <td>134017795684</td>
    </tr>
    <tr>
      <th>2</th>
      <td>11385534326</td>
      <td>134017787145</td>
    </tr>
    <tr>
      <th>3</th>
      <td>11385534326</td>
      <td>134017787146</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4950629721</td>
      <td>58328468873</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>316944</th>
      <td>9723579733</td>
      <td>142390562339</td>
    </tr>
    <tr>
      <th>316945</th>
      <td>9723579733</td>
      <td>142390562340</td>
    </tr>
    <tr>
      <th>316946</th>
      <td>9723579733</td>
      <td>48355102339</td>
    </tr>
    <tr>
      <th>316947</th>
      <td>9723579733</td>
      <td>48355102340</td>
    </tr>
    <tr>
      <th>316948</th>
      <td>9723579733</td>
      <td>48355102341</td>
    </tr>
  </tbody>
</table>
<p>316949 rows × 2 columns</p>
</div>



We focusing on flash sale

Shopee's API return flash sale flag by itemid.

Modelid that in same itemid will be flag flash sale even through that modelid didn't flash sale, We have to filter itemid that has only 1 modelid.


```python
unique_id = []
for i in df['itemid'].unique().tolist():
    if len(df[df['itemid']==i]['modelid'].unique()) == 1:
#         print(i)
        unique_id.append(i)
df['brand'] = df['brand'].replace('Petkit(เพ็ทคิต)','Petkit(เพ็ทคิท)')
df = df[df['itemid'].isin(unique_id)].reset_index(drop=True)
df = df.sort_values(by=['ingest_date'],ascending=True)
df = df.drop_duplicates()
```


```python
def extract_date_hour(row):
    date = datetime.strptime(row, '%Y-%m-%d %H:%M:%S')
    return date.strftime('%d-%H')

def extract_mega_sale(row):
    date = datetime.strptime(row, '%Y-%m-%d %H:%M:%S')
    if date.strftime('%m') == date.strftime('%d'):
        return True
    else:
        return False
    
def extract_year(row):
    date = datetime.strptime(row, '%Y-%m-%d %H:%M:%S')
    return date.strftime('%Y')

```


```python
df['year'] = df['ingest_date'].apply(extract_year)
df['day_hour'] = df['ingest_date'].apply(extract_date_hour)
df['mega_sale'] = df['ingest_date'].apply(extract_mega_sale)
```

Check patterns of data by year


```python
df['year'].unique()
```




    array(['2022', '2023'], dtype=object)




```python
print(len(df[df['year']=='2022']))
df[df['year']=='2022'][['itemid','modelid','ingest_date','day_hour']].sort_values(by=['itemid','ingest_date'])[:10]
```

    30679
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>itemid</th>
      <th>modelid</th>
      <th>ingest_date</th>
      <th>day_hour</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2987</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 10:00:01</td>
      <td>07-10</td>
    </tr>
    <tr>
      <th>4622</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 12:00:01</td>
      <td>07-12</td>
    </tr>
    <tr>
      <th>6063</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 13:00:02</td>
      <td>07-13</td>
    </tr>
    <tr>
      <th>7668</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 14:00:01</td>
      <td>07-14</td>
    </tr>
    <tr>
      <th>11112</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 15:00:01</td>
      <td>07-15</td>
    </tr>
    <tr>
      <th>13232</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 16:00:02</td>
      <td>07-16</td>
    </tr>
    <tr>
      <th>18257</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 17:00:01</td>
      <td>07-17</td>
    </tr>
    <tr>
      <th>22276</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 18:00:02</td>
      <td>07-18</td>
    </tr>
    <tr>
      <th>16966</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 19:00:01</td>
      <td>07-19</td>
    </tr>
    <tr>
      <th>18085</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2022-10-07 20:00:02</td>
      <td>07-20</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(len(df[df['year']=='2023']))
df[df['year']=='2023'][['itemid','modelid','ingest_date','day_hour']].sort_values(by=['itemid','ingest_date'])[:10]
```

    1194
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>itemid</th>
      <th>modelid</th>
      <th>ingest_date</th>
      <th>day_hour</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>36417</th>
      <td>845016064</td>
      <td>42157405015</td>
      <td>2023-01-19 09:21:47</td>
      <td>19-09</td>
    </tr>
    <tr>
      <th>36419</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-19 09:21:47</td>
      <td>19-09</td>
    </tr>
    <tr>
      <th>28899</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-19 12:00:01</td>
      <td>19-12</td>
    </tr>
    <tr>
      <th>24336</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-19 15:00:05</td>
      <td>19-15</td>
    </tr>
    <tr>
      <th>24339</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-20 09:00:08</td>
      <td>20-09</td>
    </tr>
    <tr>
      <th>26153</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-20 12:00:07</td>
      <td>20-12</td>
    </tr>
    <tr>
      <th>24573</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-20 15:00:07</td>
      <td>20-15</td>
    </tr>
    <tr>
      <th>24389</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-23 15:00:01</td>
      <td>23-15</td>
    </tr>
    <tr>
      <th>32660</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-23 18:00:02</td>
      <td>23-18</td>
    </tr>
    <tr>
      <th>32666</th>
      <td>2177325629</td>
      <td>22934228784</td>
      <td>2023-01-23 21:00:01</td>
      <td>23-21</td>
    </tr>
  </tbody>
</table>
</div>



We wil drop row that has value year=2023 because 2023, each transaction is 3 hours apart. While 2022, the volume of data is higher (96%) and there are transactions every 1 hour.


```python
print(len(df),len(df[df['year']!='2023']))

df = df[df['year']!='2023']
```

    31873 30679
    

# Filter only transaction that have flash sale


```python
df['flash_sale'].unique()
```




    array([nan,
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 100, 'promotionid': 107390517342208, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662656400, 'promo_overlay_image': 'f85173f31d3776172d6999ad5a8d39e4', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1499000000, 'stock': 100}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 30, 'promotionid': 674535842344547, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 50, 'promotionid': 108652700917760, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1150000000, 'stock': 50}",
           "{'price_before_discount': 1890000000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 40, 'promotionid': 108652700917760, 'lowest_past_price': None, 'promo_images': ['61a2ee81dd0020fa6fdce5b3e2b7cef5'], 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1400000000, 'stock': 40}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 30, 'promotionid': 107390517342208, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 50, 'promotionid': 108652700917760, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1150000000, 'stock': 34}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 30, 'promotionid': 107390517342208, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 6}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 100, 'promotionid': 107390517342208, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662656400, 'promo_overlay_image': 'f85173f31d3776172d6999ad5a8d39e4', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1499000000, 'stock': 63}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 10, 'promotionid': 674491900713811, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 9}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1662706800, 'flash_sale_stock': 30, 'promotionid': 107393006641152, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1662699600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1075000000, 'stock': 30}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1662706800, 'flash_sale_stock': 40, 'promotionid': 108652770123776, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1662699600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1190000000, 'stock': 40}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1662706800, 'flash_sale_stock': 40, 'promotionid': 108652770123776, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1662699600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1190000000, 'stock': 37}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1662706800, 'flash_sale_stock': 30, 'promotionid': 107393006641152, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1662699600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1075000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1662721200, 'flash_sale_stock': 100, 'promotionid': 107393545662464, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1662714000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1150000000, 'stock': 100}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662721200, 'flash_sale_stock': 20, 'promotionid': 107393545662464, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1662714000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 20}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1662721200, 'flash_sale_stock': 30, 'promotionid': 108652864495616, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1662714000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1662721200, 'flash_sale_stock': 100, 'promotionid': 107393545662464, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1662714000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1150000000, 'stock': 97}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662721200, 'flash_sale_stock': 20, 'promotionid': 107393545662464, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1662714000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 16}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1662721200, 'flash_sale_stock': 30, 'promotionid': 108652864495616, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1662714000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 28}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1662732000, 'flash_sale_stock': 300, 'promotionid': 108652877066240, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1662721200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 300}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662732000, 'flash_sale_stock': 20, 'promotionid': 108652877066240, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662721200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662732000, 'flash_sale_stock': 20, 'promotionid': 108652877066240, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662721200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 16}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1662732000, 'flash_sale_stock': 300, 'promotionid': 108652877066240, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1662721200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 296}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662732000, 'flash_sale_stock': 20, 'promotionid': 108652877066240, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662721200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 12}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1662732000, 'flash_sale_stock': 300, 'promotionid': 108652877066240, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1662721200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 294}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662742800, 'flash_sale_stock': 20, 'promotionid': 108652891770880, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662732000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662742800, 'flash_sale_stock': 20, 'promotionid': 108652891770880, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662732000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 17}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662742800, 'flash_sale_stock': 20, 'promotionid': 108652891770880, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662732000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 15}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1662958800, 'flash_sale_stock': 40, 'promotionid': 109177605414912, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1662915600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1190000000, 'stock': 40}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1662958800, 'flash_sale_stock': 30, 'promotionid': 109177605414912, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1662915600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 25}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1663131600, 'flash_sale_stock': 30, 'promotionid': 109187512373248, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1663088400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 849000000, 'stock': 28}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663153200, 'flash_sale_stock': 30, 'promotionid': 111212784549888, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663131600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 28}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663182000, 'flash_sale_stock': 30, 'promotionid': 111213965238273, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663174800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663182000, 'flash_sale_stock': 10, 'promotionid': 675611247201107, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1663174800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1663182000, 'flash_sale_stock': 300, 'promotionid': 111213965238273, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1663174800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 300}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1663182000, 'flash_sale_stock': 300, 'promotionid': 111213965238273, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1663174800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 298}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663182000, 'flash_sale_stock': 30, 'promotionid': 111213965238273, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663174800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 27}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1663207200, 'flash_sale_stock': 30, 'promotionid': 111213979914240, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1663182000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1150000000, 'stock': 30}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663207200, 'flash_sale_stock': 30, 'promotionid': 111213979914240, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663182000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1190000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1663207200, 'flash_sale_stock': 30, 'promotionid': 111213979914240, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1663182000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1150000000, 'stock': 29}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663207200, 'flash_sale_stock': 30, 'promotionid': 111213979914240, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663182000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1190000000, 'stock': 29}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663207200, 'flash_sale_stock': 30, 'promotionid': 111213979914240, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663182000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1190000000, 'stock': 27}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1663225200, 'flash_sale_stock': 20, 'promotionid': 109193044643840, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1663218000, 'promo_overlay_image': '4b6ef2f677ceb5d4aa58709ed81417e5', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1075000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663225200, 'flash_sale_stock': 30, 'promotionid': 111214003019777, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663218000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663225200, 'flash_sale_stock': 30, 'promotionid': 111214003019777, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663218000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 28}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1663225200, 'flash_sale_stock': 20, 'promotionid': 109193044643840, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1663218000, 'promo_overlay_image': '4b6ef2f677ceb5d4aa58709ed81417e5', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1075000000, 'stock': 17}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663250400, 'flash_sale_stock': 40, 'promotionid': 109193755611136, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663239600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1029000000, 'stock': 40}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663250400, 'flash_sale_stock': 20, 'promotionid': 675779440932484, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1663239600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1111100000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663250400, 'flash_sale_stock': 40, 'promotionid': 109193755611136, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663239600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1029000000, 'stock': 38}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663250400, 'flash_sale_stock': 40, 'promotionid': 109193755611136, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663239600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1029000000, 'stock': 37}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1663261200, 'flash_sale_stock': 5, 'promotionid': 675742640078884, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1663250400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 5}",
           "{'price_before_discount': None, 'hidden_price_display': None, 'end_time': 1663261200, 'flash_sale_stock': None, 'promotionid': 111214055391233, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663250400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': None, 'stock': None}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1663261200, 'flash_sale_stock': 30, 'promotionid': 111214055391233, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1663250400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663261200, 'flash_sale_stock': 30, 'promotionid': 111214055391233, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663250400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 28}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663261200, 'flash_sale_stock': 30, 'promotionid': 111214055391233, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663250400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 27}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663390800, 'flash_sale_stock': 30, 'promotionid': 112249442410497, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1663347600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1190000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1663390800, 'flash_sale_stock': 30, 'promotionid': 112249442410497, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1663347600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1150000000, 'stock': 29}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1663477200, 'flash_sale_stock': 30, 'promotionid': 111562572636160, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1663434000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 28}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1663477200, 'flash_sale_stock': 5, 'promotionid': 676094680585043, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1663434000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1663563600, 'flash_sale_stock': 200, 'promotionid': 111562763530241, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1663520400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 220000000, 'stock': 199}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1663736400, 'flash_sale_stock': 30, 'promotionid': 109922608214017, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1663693200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1663736400, 'flash_sale_stock': 20, 'promotionid': 109922608214017, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1663693200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1663941600, 'flash_sale_stock': 30, 'promotionid': 112466149543938, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1663930800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1663941600, 'flash_sale_stock': 5, 'promotionid': 677214937222180, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1663930800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1220000000, 'stock': 5}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1663941600, 'flash_sale_stock': 30, 'promotionid': 112466149543938, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1663930800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 29}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1663995600, 'flash_sale_stock': 100, 'promotionid': 109942241751040, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1663952400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 220000000, 'stock': 100}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 5, 'promotionid': 677365166733139, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 677370118099555, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 677367945464737, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 109943164456960, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 677367945464737, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 677367945464737, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 18}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 109943164456960, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 19}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 677367945464737, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 17}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664082000, 'flash_sale_stock': 20, 'promotionid': 677367945464737, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664038800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 16}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1664103600, 'flash_sale_stock': 5, 'promotionid': 677368981440548, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664082000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664114400, 'flash_sale_stock': 20, 'promotionid': 109943701315584, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664103600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664114400, 'flash_sale_stock': 20, 'promotionid': 109943701315584, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664103600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664114400, 'flash_sale_stock': 20, 'promotionid': 109943701315584, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664103600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664190000, 'flash_sale_stock': 30, 'promotionid': 111192574230528, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664168400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664190000, 'flash_sale_stock': 30, 'promotionid': 111192574230528, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664168400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 25}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664190000, 'flash_sale_stock': 30, 'promotionid': 111192574230528, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664168400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 24}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664190000, 'flash_sale_stock': 30, 'promotionid': 111192574230528, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664168400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 22}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664190000, 'flash_sale_stock': 30, 'promotionid': 111192574230528, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664168400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 21}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664254800, 'flash_sale_stock': 30, 'promotionid': 112849005576193, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664211600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664254800, 'flash_sale_stock': 30, 'promotionid': 112849005576193, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664211600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 29}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664254800, 'flash_sale_stock': 30, 'promotionid': 112849005576193, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664211600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 28}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664254800, 'flash_sale_stock': 30, 'promotionid': 112849005576193, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664211600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 27}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1664341200, 'flash_sale_stock': 200, 'promotionid': 113874391293953, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1664298000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664341200, 'flash_sale_stock': 20, 'promotionid': 113874391293953, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664298000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 16}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1664514000, 'flash_sale_stock': 5, 'promotionid': 678097699826724, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664470800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 5}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664535600, 'flash_sale_stock': 20, 'promotionid': 113875194503168, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1664514000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664535600, 'flash_sale_stock': 20, 'promotionid': 113875194503168, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664514000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664535600, 'flash_sale_stock': 20, 'promotionid': 678466683268707, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664514000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664535600, 'flash_sale_stock': 20, 'promotionid': 113875194503168, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1664514000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 18}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664535600, 'flash_sale_stock': 20, 'promotionid': 113875194503168, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1664514000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 17}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664535600, 'flash_sale_stock': 20, 'promotionid': 113875194503168, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664514000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 18}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664546400, 'flash_sale_stock': 10, 'promotionid': 678446298909523, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664535600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664557200, 'flash_sale_stock': 20, 'promotionid': 111380376276993, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664546400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664557200, 'flash_sale_stock': 20, 'promotionid': 111380376276993, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664546400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 16}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664557200, 'flash_sale_stock': 20, 'promotionid': 111380376276993, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664546400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 14}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664600400, 'flash_sale_stock': 30, 'promotionid': 112293650337792, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664557200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664600400, 'flash_sale_stock': 30, 'promotionid': 112293650337792, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664557200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 29}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664600400, 'flash_sale_stock': 30, 'promotionid': 112293650337792, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664557200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 27}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664600400, 'flash_sale_stock': 30, 'promotionid': 112293650337792, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664557200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1149000000, 'stock': 25}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664632800, 'flash_sale_stock': 20, 'promotionid': 112294363348992, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664622000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664632800, 'flash_sale_stock': 20, 'promotionid': 112294363348992, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664622000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1664686800, 'flash_sale_stock': 200, 'promotionid': 114094017671169, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1664643600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1664686800, 'flash_sale_stock': 200, 'promotionid': 114094017671169, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1664643600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 199}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664708400, 'flash_sale_stock': 20, 'promotionid': 678692519265185, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1664686800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 20, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664816400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 30, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664816400, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 30, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664816400, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 26}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 20, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664816400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 17}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 30, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664816400, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 25}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 30, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664816400, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 24}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 20, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664816400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 16}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 30, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664816400, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 23}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 30, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1664816400, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664859600, 'flash_sale_stock': 20, 'promotionid': 112299792879616, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664816400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 15}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1664881200, 'flash_sale_stock': 5, 'promotionid': 679191935004708, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664859600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664881200, 'flash_sale_stock': 20, 'promotionid': 112301011341314, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1664859600, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1059000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664902800, 'flash_sale_stock': 40, 'promotionid': 112301638406144, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664892000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1150000000, 'stock': 40}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1664902800, 'flash_sale_stock': 30, 'promotionid': 112301638406144, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1664892000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 801000000, 'stock': 30}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1664902800, 'flash_sale_stock': 30, 'promotionid': 112301638406144, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1664892000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 801000000, 'stock': 29}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664902800, 'flash_sale_stock': 40, 'promotionid': 112301638406144, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664892000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1150000000, 'stock': 39}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1664902800, 'flash_sale_stock': 30, 'promotionid': 112301638406144, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1664892000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 801000000, 'stock': 28}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1664902800, 'flash_sale_stock': 40, 'promotionid': 112301638406144, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1664892000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1150000000, 'stock': 38}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1664967600, 'flash_sale_stock': 10, 'promotionid': 679352153236307, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1664946000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664978400, 'flash_sale_stock': 20, 'promotionid': 114116190855171, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664967600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1664978400, 'flash_sale_stock': 20, 'promotionid': 114116190855171, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1664967600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665032400, 'flash_sale_stock': 20, 'promotionid': 112428690120704, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1664989200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665032400, 'flash_sale_stock': 20, 'promotionid': 112428690120704, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1664989200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 19}",
           "{'price_before_discount': None, 'hidden_price_display': None, 'end_time': 1665075600, 'flash_sale_stock': None, 'promotionid': 679598237221793, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665064800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': None, 'stock': None}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665075600, 'flash_sale_stock': 50, 'promotionid': 679598237221793, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665064800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 50}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665140400, 'flash_sale_stock': 10, 'promotionid': 679713794516819, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665118800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1665140400, 'flash_sale_stock': 391, 'promotionid': 679715757475876, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665118800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 391}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665140400, 'flash_sale_stock': 20, 'promotionid': 112429755527168, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665118800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665140400, 'flash_sale_stock': 10, 'promotionid': 679713794516819, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665118800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 9}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665140400, 'flash_sale_stock': 20, 'promotionid': 112429755527168, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665118800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665140400, 'flash_sale_stock': 20, 'promotionid': 112429755527168, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665118800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 519000000, 'hidden_price_display': None, 'end_time': 1665151200, 'flash_sale_stock': 10, 'promotionid': 679776237193949, 'lowest_past_price': None, 'promo_images': ['865b5c2978670e1d1eb728d08d54c9db'], 'start_time': 1665140400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 329900000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665151200, 'flash_sale_stock': 20, 'promotionid': 112429946343425, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1665140400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 20}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665205200, 'flash_sale_stock': 150, 'promotionid': 114797056393216, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665162000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 150}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665205200, 'flash_sale_stock': 100, 'promotionid': 114797056393216, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665162000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 100}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665205200, 'flash_sale_stock': 100, 'promotionid': 114797056393216, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665162000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 99}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665205200, 'flash_sale_stock': 100, 'promotionid': 114797056393216, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665162000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 98}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665226800, 'flash_sale_stock': 10, 'promotionid': 679544522892397, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665205200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 10}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1665291600, 'flash_sale_stock': 50, 'promotionid': 114800055316480, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665248400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 282000000, 'stock': 49}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665291600, 'flash_sale_stock': 20, 'promotionid': 112431361912832, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665248400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1665291600, 'flash_sale_stock': 50, 'promotionid': 114800055316480, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665248400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 282000000, 'stock': 48}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1665291600, 'flash_sale_stock': 50, 'promotionid': 114800055316480, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665248400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 282000000, 'stock': 47}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 20, 'promotionid': 115216442753024, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 659000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 100, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665334800, 'promo_overlay_image': 'd2ecb72a3ac6ae096457957f67b79a96', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1499000000, 'stock': 96}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 250, 'promotionid': 115216442753024, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 249}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 400, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665334800, 'promo_overlay_image': 'd2ecb72a3ac6ae096457957f67b79a96', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 459000000, 'stock': 400}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 50, 'promotionid': 115216442753024, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 48}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 20, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 40, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 40}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 50, 'promotionid': 115216442753024, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 0}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 100, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665334800, 'promo_overlay_image': 'd2ecb72a3ac6ae096457957f67b79a96', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1499000000, 'stock': 69}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 250, 'promotionid': 115216442753024, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 243}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 20, 'promotionid': 115216442753024, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 659000000, 'stock': 16}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 400, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665334800, 'promo_overlay_image': 'd2ecb72a3ac6ae096457957f67b79a96', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 459000000, 'stock': 350}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 40, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 38}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665342000, 'flash_sale_stock': 20, 'promotionid': 112432211247105, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1665334800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1119000000, 'stock': 19}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665367200, 'flash_sale_stock': 30, 'promotionid': 679595582229923, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1665342000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 669900000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665367200, 'flash_sale_stock': 30, 'promotionid': 679595582229923, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1665342000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 669900000, 'stock': 28}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665367200, 'flash_sale_stock': 30, 'promotionid': 679595582229923, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1665342000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 669900000, 'stock': 27}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665367200, 'flash_sale_stock': 30, 'promotionid': 679595582229923, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1665342000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 669900000, 'stock': 24}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665378000, 'flash_sale_stock': 150, 'promotionid': 115216474185728, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665367200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 150}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665378000, 'flash_sale_stock': 30, 'promotionid': 115216474185728, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1665367200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665378000, 'flash_sale_stock': 150, 'promotionid': 115216474185728, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665367200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 149}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665378000, 'flash_sale_stock': 30, 'promotionid': 115216474185728, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1665367200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 24}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665378000, 'flash_sale_stock': 30, 'promotionid': 115216474185728, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1665367200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 22}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665378000, 'flash_sale_stock': 150, 'promotionid': 115216474185728, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665367200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 148}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665385200, 'flash_sale_stock': 50, 'promotionid': 115216488902656, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665378000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 49}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1665385200, 'flash_sale_stock': 20, 'promotionid': 112432754393088, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1665378000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 659000000, 'stock': 20}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1665385200, 'flash_sale_stock': 70, 'promotionid': 112432754393088, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1665378000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 312000000, 'stock': 70}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1665385200, 'flash_sale_stock': 5, 'promotionid': 680257015617572, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665378000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 5}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665385200, 'flash_sale_stock': 50, 'promotionid': 115216488902656, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665378000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 41}",
           "{'price_before_discount': 1799000000, 'hidden_price_display': None, 'end_time': 1665392400, 'flash_sale_stock': 20, 'promotionid': 115216501473281, 'lowest_past_price': None, 'promo_images': ['1cdab576ea5a1c6fee7eb5546c532439'], 'start_time': 1665385200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1499900000, 'stock': 20}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1665392400, 'flash_sale_stock': 30, 'promotionid': 115216501473281, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1665385200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 799000000, 'stock': 30}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1665392400, 'flash_sale_stock': 30, 'promotionid': 115216501473281, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1665385200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 799000000, 'stock': 29}",
           "{'price_before_discount': 1799000000, 'hidden_price_display': None, 'end_time': 1665392400, 'flash_sale_stock': 20, 'promotionid': 115216501473281, 'lowest_past_price': None, 'promo_images': ['1cdab576ea5a1c6fee7eb5546c532439'], 'start_time': 1665385200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1499900000, 'stock': 17}",
           "{'price_before_discount': 1890000000, 'hidden_price_display': None, 'end_time': 1665399600, 'flash_sale_stock': 80, 'promotionid': 679924203866485, 'lowest_past_price': None, 'promo_images': ['61a2ee81dd0020fa6fdce5b3e2b7cef5'], 'start_time': 1665392400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 80}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665399600, 'flash_sale_stock': 300, 'promotionid': 115216518250496, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665392400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 300}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665399600, 'flash_sale_stock': 300, 'promotionid': 115216518250496, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665392400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 215000000, 'stock': 298}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 20, 'promotionid': 112433469521920, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 20, 'promotionid': 115216539189248, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 659000000, 'stock': 19}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 30, 'promotionid': 680315847009891, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 30, 'promotionid': 115216539189248, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 29}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 20, 'promotionid': 112433469521920, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 30, 'promotionid': 115216539189248, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 22}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665421200, 'flash_sale_stock': 30, 'promotionid': 115216539189248, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665410400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665550800, 'flash_sale_stock': 20, 'promotionid': 116084193943552, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665507600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665572400, 'flash_sale_stock': 40, 'promotionid': 680623648082973, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665550800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 499900000, 'stock': 40}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665572400, 'flash_sale_stock': 10, 'promotionid': 680617176280915, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665550800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665572400, 'flash_sale_stock': 40, 'promotionid': 680623648082973, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665550800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 220000000, 'stock': 40}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665572400, 'flash_sale_stock': 20, 'promotionid': 113723941535744, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665550800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665572400, 'flash_sale_stock': 20, 'promotionid': 113723941535744, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665550800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665572400, 'flash_sale_stock': 40, 'promotionid': 680623648082973, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665550800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 499900000, 'stock': 38}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1665745200, 'flash_sale_stock': 5, 'promotionid': 680993870906404, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665723600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665745200, 'flash_sale_stock': 20, 'promotionid': 116085236178945, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665723600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665766800, 'flash_sale_stock': 20, 'promotionid': 116085393461248, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665756000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665766800, 'flash_sale_stock': 20, 'promotionid': 116085393461248, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665756000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1665774000, 'flash_sale_stock': 20, 'promotionid': 116478057910272, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1665766800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 659000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1665774000, 'flash_sale_stock': 50, 'promotionid': 116478057910272, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665766800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 292000000, 'stock': 49}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665774000, 'flash_sale_stock': 50, 'promotionid': 681059683794531, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665766800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665774000, 'flash_sale_stock': 50, 'promotionid': 116478057910272, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665766800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 48}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665774000, 'flash_sale_stock': 50, 'promotionid': 116478057910272, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665766800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 45}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1665774000, 'flash_sale_stock': 50, 'promotionid': 116478057910272, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665766800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 292000000, 'stock': 48}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665799200, 'flash_sale_stock': 30, 'promotionid': 116478160670720, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665774000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1665799200, 'flash_sale_stock': 30, 'promotionid': 116478160670720, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1665774000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1665799200, 'flash_sale_stock': 20, 'promotionid': 680687892234659, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1665774000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 669900000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665799200, 'flash_sale_stock': 30, 'promotionid': 116478160670720, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665774000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 29}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665799200, 'flash_sale_stock': 30, 'promotionid': 116478160670720, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665774000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 28}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1665810000, 'flash_sale_stock': 100, 'promotionid': 116478196318208, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1665799200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 140000000, 'stock': 100}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665810000, 'flash_sale_stock': 200, 'promotionid': 116478196318208, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665799200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1665810000, 'flash_sale_stock': 200, 'promotionid': 116478196318208, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1665799200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 199}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665817200, 'flash_sale_stock': 20, 'promotionid': 116478211059712, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665810000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1665831600, 'flash_sale_stock': 20, 'promotionid': 113734477639680, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665817200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1665842400, 'flash_sale_stock': 20, 'promotionid': 113734668484610, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1665831600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 349000000, 'stock': 20}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1665842400, 'flash_sale_stock': 20, 'promotionid': 113734668484610, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1665831600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 349000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665853200, 'flash_sale_stock': 20, 'promotionid': 116478294896640, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1665842400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1119000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665853200, 'flash_sale_stock': 30, 'promotionid': 116478294896640, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665842400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1665853200, 'flash_sale_stock': 20, 'promotionid': 116478294896640, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1665842400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 659000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665853200, 'flash_sale_stock': 30, 'promotionid': 116478294896640, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665842400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 28}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1665853200, 'flash_sale_stock': 30, 'promotionid': 116478294896640, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1665842400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 26}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1665939600, 'flash_sale_stock': 30, 'promotionid': 117346291425280, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1665928800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1150000000, 'stock': 30}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665982800, 'flash_sale_stock': 100, 'promotionid': 117346769604608, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665939600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 100}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665982800, 'flash_sale_stock': 100, 'promotionid': 117346769604608, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665939600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 99}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665982800, 'flash_sale_stock': 100, 'promotionid': 117346769604608, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665939600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 98}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665982800, 'flash_sale_stock': 100, 'promotionid': 117346769604608, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665939600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 97}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665982800, 'flash_sale_stock': 100, 'promotionid': 117346769604608, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665939600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 96}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1665982800, 'flash_sale_stock': 100, 'promotionid': 117346769604608, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1665939600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 95}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 5, 'promotionid': 681532409112612, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 519000000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 10, 'promotionid': 681541558948573, 'lowest_past_price': None, 'promo_images': ['865b5c2978670e1d1eb728d08d54c9db'], 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 329900000, 'stock': 10}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 10, 'promotionid': 681542861290605, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 10}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 25, 'promotionid': 681541558948573, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 25}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 10, 'promotionid': 681522854444883, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 519000000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 10, 'promotionid': 681541558948573, 'lowest_past_price': None, 'promo_images': ['865b5c2978670e1d1eb728d08d54c9db'], 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 329900000, 'stock': 9}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666004400, 'flash_sale_stock': 25, 'promotionid': 681541558948573, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1665982800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 24}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666026000, 'flash_sale_stock': 30, 'promotionid': 681573964139549, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666015200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 220000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666026000, 'flash_sale_stock': 20, 'promotionid': 681591079027617, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666015200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666026000, 'flash_sale_stock': 20, 'promotionid': 117346803130368, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666015200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666026000, 'flash_sale_stock': 20, 'promotionid': 117346803130368, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666015200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666026000, 'flash_sale_stock': 20, 'promotionid': 117346803130368, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666015200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 17}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666090800, 'flash_sale_stock': 10, 'promotionid': 681566183691683, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1666069200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666101600, 'flash_sale_stock': 30, 'promotionid': 116471779028992, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666090800, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666101600, 'flash_sale_stock': 30, 'promotionid': 116471779028992, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666090800, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 27}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666112400, 'flash_sale_stock': 20, 'promotionid': 116471911088128, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666101600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666112400, 'flash_sale_stock': 20, 'promotionid': 116471911088128, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666101600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666155600, 'flash_sale_stock': 10, 'promotionid': 681772071642756, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666112400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666177200, 'flash_sale_stock': 5, 'promotionid': 681884682387283, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666155600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666177200, 'flash_sale_stock': 40, 'promotionid': 681763055937565, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666155600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 220000000, 'stock': 40}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1666188000, 'flash_sale_stock': 20, 'promotionid': 681914388519965, 'lowest_past_price': None, 'promo_images': ['f1c86bd6fa4aa20ee489b22d98071e76'], 'start_time': 1666177200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 699900000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666188000, 'flash_sale_stock': 100, 'promotionid': 116472240398338, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666177200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1090000000, 'stock': 100}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666188000, 'flash_sale_stock': 100, 'promotionid': 116472240398338, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666177200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1090000000, 'stock': 96}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666188000, 'flash_sale_stock': 100, 'promotionid': 116472240398338, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666177200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1090000000, 'stock': 95}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666242000, 'flash_sale_stock': 25, 'promotionid': 116472448016384, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666198800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 25}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666242000, 'flash_sale_stock': 25, 'promotionid': 116472448016384, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666198800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 24}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666242000, 'flash_sale_stock': 25, 'promotionid': 116472448016384, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666198800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 23}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666242000, 'flash_sale_stock': 25, 'promotionid': 116472448016384, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666198800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 22}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666263600, 'flash_sale_stock': 10, 'promotionid': 681885785517475, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1666242000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679000000, 'stock': 10}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1666350000, 'flash_sale_stock': 5, 'promotionid': 682269012779044, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666328400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666350000, 'flash_sale_stock': 5, 'promotionid': 682065547041619, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666328400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666350000, 'flash_sale_stock': 10, 'promotionid': 682258766052461, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666328400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666350000, 'flash_sale_stock': 5, 'promotionid': 682065547041619, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666328400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 4}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666360800, 'flash_sale_stock': 50, 'promotionid': 682085312752669, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666350000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 220000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666360800, 'flash_sale_stock': 10, 'promotionid': 682310890788484, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666350000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 10}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666360800, 'flash_sale_stock': 50, 'promotionid': 117363295141888, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1666350000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 292000000, 'stock': 49}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666371600, 'flash_sale_stock': 30, 'promotionid': 682135673752481, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666360800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666371600, 'flash_sale_stock': 30, 'promotionid': 682135673752481, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666360800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 29}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666436400, 'flash_sale_stock': 10, 'promotionid': 682266181577123, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1666414800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666447200, 'flash_sale_stock': 30, 'promotionid': 117364031234049, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666436400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666447200, 'flash_sale_stock': 30, 'promotionid': 117364031234049, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666436400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 29}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666458000, 'flash_sale_stock': 10, 'promotionid': 682259783182445, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666447200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 10}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 100, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 499900000, 'stock': 100}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 120}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 100, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 499900000, 'stock': 99}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 119}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 116}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 115}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 113}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 100, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 499900000, 'stock': 98}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 111}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1666501200, 'flash_sale_stock': 120, 'promotionid': 116104005619712, 'lowest_past_price': None, 'promo_images': ['85309e59b9e09fd8fdaae6ecbf456f61'], 'start_time': 1666458000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 107}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666522800, 'flash_sale_stock': 200, 'promotionid': 116104160825344, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666501200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 199900000, 'stock': 200}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666522800, 'flash_sale_stock': 10, 'promotionid': 682071050023763, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666501200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666522800, 'flash_sale_stock': 200, 'promotionid': 116104160825344, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666501200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 199900000, 'stock': 199}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1666533600, 'flash_sale_stock': 30, 'promotionid': 116104334868481, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1666522800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 349000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666544400, 'flash_sale_stock': 25, 'promotionid': 117366396841985, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666533600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 25}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666544400, 'flash_sale_stock': 25, 'promotionid': 117366396841985, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666533600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 24}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 20, 'promotionid': 682828241431971, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 30, 'promotionid': 115330687131649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 30, 'promotionid': 115330687131649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 27}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 30, 'promotionid': 115330687131649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 26}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 30, 'promotionid': 115330687131649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 25}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 30, 'promotionid': 115330687131649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 24}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666674000, 'flash_sale_stock': 30, 'promotionid': 115330687131649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666630800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 23}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666695600, 'flash_sale_stock': 5, 'promotionid': 682972041036627, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666674000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666695600, 'flash_sale_stock': 50, 'promotionid': 115331173691392, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1666674000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 292000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666695600, 'flash_sale_stock': 20, 'promotionid': 115331173691392, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666674000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1060000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666695600, 'flash_sale_stock': 50, 'promotionid': 115331173691392, 'lowest_past_price': None, 'promo_images': ['416c03d70d90acfda026e6145c0dba4d'], 'start_time': 1666674000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 292000000, 'stock': 49}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666695600, 'flash_sale_stock': 20, 'promotionid': 115331173691392, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666674000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1060000000, 'stock': 18}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666695600, 'flash_sale_stock': 20, 'promotionid': 115331173691392, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666674000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1060000000, 'stock': 17}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666706400, 'flash_sale_stock': 20, 'promotionid': 115331905581056, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666695600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1666717200, 'flash_sale_stock': 30, 'promotionid': 683051290324897, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1666706400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 30}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666803600, 'flash_sale_stock': 50, 'promotionid': 683224873696161, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1666792800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 50}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666846800, 'flash_sale_stock': 20, 'promotionid': 682831898814883, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1666803600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 10, 'promotionid': 683163687188589, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 10}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 10, 'promotionid': 683357258470109, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 30, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 200, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 10, 'promotionid': 683335162896211, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 200, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 220000000, 'stock': 199}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 30, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 29}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 30, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 28}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 10, 'promotionid': 683357258470109, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 9}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 200, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 220000000, 'stock': 198}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 10, 'promotionid': 683357258470109, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 7}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 30, 'promotionid': 115337987321856, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 27}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1666868400, 'flash_sale_stock': 10, 'promotionid': 683335162896211, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1666846800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 9}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666933200, 'flash_sale_stock': 10, 'promotionid': 683379916104324, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666890000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666933200, 'flash_sale_stock': 10, 'promotionid': 683379916104324, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666890000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 9}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1666933200, 'flash_sale_stock': 10, 'promotionid': 683379916104324, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1666890000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 8}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666965600, 'flash_sale_stock': 30, 'promotionid': 118808367091713, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666954800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 30}",
           "{'price_before_discount': 519000000, 'hidden_price_display': None, 'end_time': 1666965600, 'flash_sale_stock': 10, 'promotionid': 683579296561885, 'lowest_past_price': None, 'promo_images': ['865b5c2978670e1d1eb728d08d54c9db'], 'start_time': 1666954800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 329000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666965600, 'flash_sale_stock': 30, 'promotionid': 118808367091713, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666954800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 29}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1666965600, 'flash_sale_stock': 30, 'promotionid': 118808367091713, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1666954800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1149000000, 'stock': 27}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1666976400, 'flash_sale_stock': 100, 'promotionid': 118808465657856, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1666965600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 100}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1666976400, 'flash_sale_stock': 200, 'promotionid': 118808465657856, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1666965600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1666976400, 'flash_sale_stock': 100, 'promotionid': 118808465657856, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1666965600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 99}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 80, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 264000000, 'stock': 80}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 10, 'promotionid': 683521215914093, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 20, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 20, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 20, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 80, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 264000000, 'stock': 79}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 80, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 264000000, 'stock': 75}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 20, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 17}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 80, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 264000000, 'stock': 74}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 80, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 264000000, 'stock': 73}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667019600, 'flash_sale_stock': 20, 'promotionid': 115341332271104, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1666976400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 16}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 683741683189665, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 5, 'promotionid': 683741620314963, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 5}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 115341707673600, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 683741683189665, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 29}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 683741683189665, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 28}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 115341707673600, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1084000000, 'stock': 26}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 683741683189665, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 27}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667052000, 'flash_sale_stock': 30, 'promotionid': 683741683189665, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667041200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 29}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1667062800, 'flash_sale_stock': 5, 'promotionid': 683741215556644, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1667052000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 5}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667127600, 'flash_sale_stock': 10, 'promotionid': 683550917887395, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1667106000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679000000, 'stock': 10}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1667149200, 'flash_sale_stock': 30, 'promotionid': 115343599280128, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1667138400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667149200, 'flash_sale_stock': 20, 'promotionid': 115343599280128, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1667138400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 829300000, 'stock': 20}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1667149200, 'flash_sale_stock': 30, 'promotionid': 115343599280128, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1667138400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 849000000, 'stock': 29}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667149200, 'flash_sale_stock': 20, 'promotionid': 115343599280128, 'lowest_past_price': None, 'promo_images': ['203d98e69b73681e61b97b669c785f40'], 'start_time': 1667138400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 829300000, 'stock': 19}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 100, 'promotionid': 118809688281088, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 100}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683763975915107, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 29}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 100, 'promotionid': 118809688281088, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 97}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 29}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 100, 'promotionid': 118809688281088, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 95}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 100, 'promotionid': 118809688281088, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 92}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 28}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 100, 'promotionid': 118809688281088, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 91}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 28}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 30, 'promotionid': 683743073646497, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 27}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1667192400, 'flash_sale_stock': 100, 'promotionid': 118809688281088, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1667149200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 90}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667214000, 'flash_sale_stock': 80, 'promotionid': 115344175988737, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1667192400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 285000000, 'stock': 80}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667214000, 'flash_sale_stock': 5, 'promotionid': 684065105994579, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1667192400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 5}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1667214000, 'flash_sale_stock': 200, 'promotionid': 118809782673409, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1667192400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667214000, 'flash_sale_stock': 80, 'promotionid': 115344175988737, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1667192400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 285000000, 'stock': 79}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1667214000, 'flash_sale_stock': 200, 'promotionid': 118809782673409, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1667192400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 199}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667214000, 'flash_sale_stock': 80, 'promotionid': 115344175988737, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1667192400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 285000000, 'stock': 78}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667538000, 'flash_sale_stock': 10, 'promotionid': 684625217528452, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1667494800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 9}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667559600, 'flash_sale_stock': 20, 'promotionid': 119147038306305, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667538000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667570400, 'flash_sale_stock': 20, 'promotionid': 116112027242496, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667559600, 'promo_overlay_image': '529efd5fe7cf5d2fa8a96a5ff2abf57c', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 837200000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667570400, 'flash_sale_stock': 20, 'promotionid': 116112027242496, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667559600, 'promo_overlay_image': '529efd5fe7cf5d2fa8a96a5ff2abf57c', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 837200000, 'stock': 18}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667581200, 'flash_sale_stock': 5, 'promotionid': 684784313764691, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1667570400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667624400, 'flash_sale_stock': 20, 'promotionid': 116112396382208, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1667581200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667646000, 'flash_sale_stock': 20, 'promotionid': 684786905842083, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1667624400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 689000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667656800, 'flash_sale_stock': 50, 'promotionid': 119386772115456, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1667646000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 289000000, 'stock': 50}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1667667600, 'flash_sale_stock': 50, 'promotionid': 685031322633121, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1667656800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667710800, 'flash_sale_stock': 11, 'promotionid': 684658698589828, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1667667600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 11}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667732400, 'flash_sale_stock': 20, 'promotionid': 685031381384097, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667710800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667732400, 'flash_sale_stock': 10, 'promotionid': 684611531533421, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667710800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 9}",
           "{'price_before_discount': 519000000, 'hidden_price_display': None, 'end_time': 1667743200, 'flash_sale_stock': 10, 'promotionid': 684644513463005, 'lowest_past_price': None, 'promo_images': ['865b5c2978670e1d1eb728d08d54c9db'], 'start_time': 1667732400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 329900000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1667797200, 'flash_sale_stock': 150, 'promotionid': 119388827287553, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1667754000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 150}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1667797200, 'flash_sale_stock': 50, 'promotionid': 119388827287553, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1667754000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 699900000, 'stock': 50}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1667797200, 'flash_sale_stock': 150, 'promotionid': 119388827287553, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1667754000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 149}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667818800, 'flash_sale_stock': 10, 'promotionid': 684788193514915, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1667797200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 689000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1667883600, 'flash_sale_stock': 30, 'promotionid': 117514413748224, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1667840400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1150000000, 'stock': 30}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667883600, 'flash_sale_stock': 20, 'promotionid': 117514413748224, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667840400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1667905200, 'flash_sale_stock': 30, 'promotionid': 120123283533824, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1667883600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 799000000, 'stock': 28}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1667905200, 'flash_sale_stock': 30, 'promotionid': 120123283533824, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1667883600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 799000000, 'stock': 24}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667916000, 'flash_sale_stock': 20, 'promotionid': 117515030327296, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667905200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1667916000, 'flash_sale_stock': 20, 'promotionid': 120123296079872, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1667905200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 15}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667926800, 'flash_sale_stock': 30, 'promotionid': 117515445563392, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1667916000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 30}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1667991600, 'flash_sale_stock': 20, 'promotionid': 120123912654848, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1667970000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1667991600, 'flash_sale_stock': 20, 'promotionid': 685576263423395, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1667970000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 689000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1667991600, 'flash_sale_stock': 20, 'promotionid': 685519734692573, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1667970000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 18}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668013200, 'flash_sale_stock': 5, 'promotionid': 685764742813523, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668002400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1668056400, 'flash_sale_stock': 20, 'promotionid': 120124388671488, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1668013200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 51, 'promotionid': 117518211739649, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 311100000, 'stock': 43}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 20, 'promotionid': 117518211739649, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 18}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 50, 'promotionid': 120222101303296, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1111000000, 'stock': 50}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 120, 'promotionid': 117518211739649, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 139000000, 'stock': 103}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 100, 'promotionid': 120222101303296, 'lowest_past_price': None, 'promo_images': ['8e506c0dd957ee411b7d7dac94c8a7a7'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 96}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 20, 'promotionid': 120222101303296, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 990000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 100, 'promotionid': 117518211739649, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668099600, 'promo_overlay_image': '52b8cc2a4881716e9e32e1b012e58fae', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1399000000, 'stock': 69}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668106800, 'flash_sale_stock': 50, 'promotionid': 685739992274849, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1668099600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 42}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1668132000, 'flash_sale_stock': 80, 'promotionid': 117518457102337, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1668106800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 699900000, 'stock': 79}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1668132000, 'flash_sale_stock': 20, 'promotionid': 685393150548387, 'lowest_past_price': None, 'promo_images': ['7487eedc132cb36f2f6208b06fc828b0'], 'start_time': 1668106800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 679900000, 'stock': 17}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1668132000, 'flash_sale_stock': 80, 'promotionid': 117518457102337, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1668106800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 699900000, 'stock': 77}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1668142800, 'flash_sale_stock': 30, 'promotionid': 120222227116032, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1668132000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 29}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1668142800, 'flash_sale_stock': 200, 'promotionid': 120222227116032, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1668132000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668150000, 'flash_sale_stock': 25, 'promotionid': 117535601274880, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668142800, 'promo_overlay_image': '5a401bf5e4a25fe490b2c813f84b0315', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 908300000, 'stock': 25}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1668150000, 'flash_sale_stock': 20, 'promotionid': 117535601274880, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1668142800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 659000000, 'stock': 17}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1668150000, 'flash_sale_stock': 50, 'promotionid': 120222355079169, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1668142800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 499900000, 'stock': 33}",
           "{'price_before_discount': 1799000000, 'hidden_price_display': None, 'end_time': 1668150000, 'flash_sale_stock': 5, 'promotionid': 685898943813293, 'lowest_past_price': None, 'promo_images': ['1cdab576ea5a1c6fee7eb5546c532439'], 'start_time': 1668142800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1450000000, 'stock': 4}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1668157200, 'flash_sale_stock': 100, 'promotionid': 120222365564928, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1668150000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 699900000, 'stock': 96}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1668175200, 'flash_sale_stock': 50, 'promotionid': 120222409613312, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1668164400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1111000000, 'stock': 49}",
           "{'price_before_discount': 519000000, 'hidden_price_display': None, 'end_time': 1668175200, 'flash_sale_stock': 5, 'promotionid': 686096937981661, 'lowest_past_price': None, 'promo_images': ['865b5c2978670e1d1eb728d08d54c9db'], 'start_time': 1668164400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 327000000, 'stock': 4}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668175200, 'flash_sale_stock': 10, 'promotionid': 685896961954403, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668164400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668186000, 'flash_sale_stock': 100, 'promotionid': 117536140292096, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668175200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1415000000, 'stock': 99}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1668186000, 'flash_sale_stock': 20, 'promotionid': 117536140292096, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1668175200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668186000, 'flash_sale_stock': 25, 'promotionid': 117536140292096, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668175200, 'promo_overlay_image': '5a401bf5e4a25fe490b2c813f84b0315', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 908300000, 'stock': 24}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668186000, 'flash_sale_stock': 10, 'promotionid': 686125379605331, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668175200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 10}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1668186000, 'flash_sale_stock': 20, 'promotionid': 117536140292096, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1668175200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 349000000, 'stock': 19}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1668186000, 'flash_sale_stock': 20, 'promotionid': 117536140292096, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1668175200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 659000000, 'stock': 20}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1668250800, 'flash_sale_stock': 20, 'promotionid': 118805990961153, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1668229200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668272400, 'flash_sale_stock': 30, 'promotionid': 118806508937216, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668261600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668402000, 'flash_sale_stock': 10, 'promotionid': 686168444574340, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668358800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 10}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1668423600, 'flash_sale_stock': 20, 'promotionid': 686620500368093, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1668402000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 19}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668445200, 'flash_sale_stock': 20, 'promotionid': 686665865960353, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1668434400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1668452400, 'flash_sale_stock': 80, 'promotionid': 121308407160832, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1668445200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1090000000, 'stock': 80}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668452400, 'flash_sale_stock': 10, 'promotionid': 686660893661011, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668445200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1668452400, 'flash_sale_stock': 50, 'promotionid': 121308407160832, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1668445200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1129000000, 'stock': 49}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1668477600, 'flash_sale_stock': 100, 'promotionid': 119121528471552, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1668452400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 499900000, 'stock': 94}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1668477600, 'flash_sale_stock': 100, 'promotionid': 119121528471552, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1668452400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 499900000, 'stock': 92}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1668495600, 'flash_sale_stock': 20, 'promotionid': 119122023354368, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1668488400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 879000000, 'stock': 20}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1668495600, 'flash_sale_stock': 200, 'promotionid': 121308826607618, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1668488400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 599000000, 'hidden_price_display': None, 'end_time': 1668510000, 'flash_sale_stock': 150, 'promotionid': 119122218414081, 'lowest_past_price': None, 'promo_images': ['880e0ff4e303a6edcf9f9d213e4a84e4'], 'start_time': 1668495600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 329900000, 'stock': 146}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1668510000, 'flash_sale_stock': 50, 'promotionid': 121308946104321, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1668495600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 699900000, 'stock': 50}",
           "{'price_before_discount': 999000000, 'hidden_price_display': None, 'end_time': 1668510000, 'flash_sale_stock': 20, 'promotionid': 121308946104321, 'lowest_past_price': None, 'promo_images': ['7e57cbf5900076387da4da298ff931ec'], 'start_time': 1668495600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 659000000, 'stock': 20}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1668520800, 'flash_sale_stock': 50, 'promotionid': 686610417260573, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1668510000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 140000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668531600, 'flash_sale_stock': 20, 'promotionid': 121309231370241, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668520800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 990000000, 'stock': 20}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1668531600, 'flash_sale_stock': 30, 'promotionid': 121309231370241, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1668520800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 399000000, 'hidden_price_display': None, 'end_time': 1668531600, 'flash_sale_stock': 15, 'promotionid': 119122549747713, 'lowest_past_price': None, 'promo_images': ['de2af3edeabdbf5515f4d62c0287bee7'], 'start_time': 1668520800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 349000000, 'stock': 15}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668574800, 'flash_sale_stock': 20, 'promotionid': 120396211011585, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668531600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668574800, 'flash_sale_stock': 20, 'promotionid': 120396211011585, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668531600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668574800, 'flash_sale_stock': 20, 'promotionid': 120396211011585, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668531600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 18}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1668596400, 'flash_sale_stock': 20, 'promotionid': 686983890673373, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1668574800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1668596400, 'flash_sale_stock': 20, 'promotionid': 686983890673373, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1668574800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 17}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668618000, 'flash_sale_stock': 10, 'promotionid': 687025072495521, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1668607200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1668693600, 'flash_sale_stock': 30, 'promotionid': 120401403510785, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1668682800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1129000000, 'stock': 30}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1668693600, 'flash_sale_stock': 5, 'promotionid': 687161783687204, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668682800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668704400, 'flash_sale_stock': 10, 'promotionid': 687221403671379, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668693600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 10}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1668704400, 'flash_sale_stock': 30, 'promotionid': 120402076725248, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1668693600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1668780000, 'flash_sale_stock': 50, 'promotionid': 120402739421185, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1668769200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 499900000, 'stock': 50}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668790800, 'flash_sale_stock': 10, 'promotionid': 687379224846241, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1668780000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 10}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668834000, 'flash_sale_stock': 5, 'promotionid': 687199614213764, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668790800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668834000, 'flash_sale_stock': 5, 'promotionid': 687199614213764, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1668790800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 4}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1668866400, 'flash_sale_stock': 20, 'promotionid': 120403278372864, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1668855600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1668877200, 'flash_sale_stock': 5, 'promotionid': 687567614106660, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1668866400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 5}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1668920400, 'flash_sale_stock': 20, 'promotionid': 122578845044737, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1668877200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 699900000, 'stock': 20}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1668920400, 'flash_sale_stock': 200, 'promotionid': 122578845044737, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1668877200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 959000000, 'hidden_price_display': None, 'end_time': 1668920400, 'flash_sale_stock': 20, 'promotionid': 122578845044737, 'lowest_past_price': None, 'promo_images': ['b68671a9c8699b06e9dfd866925f2921'], 'start_time': 1668877200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 699900000, 'stock': 19}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1668942000, 'flash_sale_stock': 20, 'promotionid': 687554150391713, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1668920400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 20}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1668952800, 'flash_sale_stock': 30, 'promotionid': 122579092508673, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1668942000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669028400, 'flash_sale_stock': 30, 'promotionid': 120406107471872, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669006800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669028400, 'flash_sale_stock': 30, 'promotionid': 120406107471872, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669006800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 28}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669050000, 'flash_sale_stock': 10, 'promotionid': 687932482902945, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1669039200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669093200, 'flash_sale_stock': 30, 'promotionid': 120406841483265, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669050000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669093200, 'flash_sale_stock': 30, 'promotionid': 120406841483265, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669050000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 27}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669093200, 'flash_sale_stock': 30, 'promotionid': 120406841483265, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669050000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 25}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669093200, 'flash_sale_stock': 30, 'promotionid': 120406841483265, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669050000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 24}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1669114800, 'flash_sale_stock': 20, 'promotionid': 688064425172701, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1669093200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 20}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1669114800, 'flash_sale_stock': 20, 'promotionid': 688064425172701, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1669093200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 19}",
           "{'price_before_discount': 699900000, 'hidden_price_display': None, 'end_time': 1669125600, 'flash_sale_stock': 30, 'promotionid': 688112514961437, 'lowest_past_price': None, 'promo_images': ['77ea1e5671d8853acabaf9cb70778d2d'], 'start_time': 1669114800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 499900000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1669136400, 'flash_sale_stock': 10, 'promotionid': 688102324952993, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1669125600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669222800, 'flash_sale_stock': 10, 'promotionid': 688294998693793, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1669212000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 10}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669266000, 'flash_sale_stock': 30, 'promotionid': 120456013385728, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669222800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1129000000, 'stock': 30}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1669266000, 'flash_sale_stock': 40, 'promotionid': 688246632077341, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1669222800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 220000000, 'stock': 40}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1669287600, 'flash_sale_stock': 20, 'promotionid': 687201075976922, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1669266000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 849000000, 'stock': 18}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1669287600, 'flash_sale_stock': 20, 'promotionid': 687201075976922, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1669266000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 849000000, 'stock': 17}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1669309200, 'flash_sale_stock': 20, 'promotionid': 688464226226909, 'lowest_past_price': None, 'promo_images': ['8790407e23b43b2675f7952bc4f7cdd6'], 'start_time': 1669298400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 289000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669352400, 'flash_sale_stock': 10, 'promotionid': 688459423801171, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669309200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669352400, 'flash_sale_stock': 50, 'promotionid': 688468693209699, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669309200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669352400, 'flash_sale_stock': 5, 'promotionid': 688253053556356, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1669309200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 4}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669352400, 'flash_sale_stock': 5, 'promotionid': 688253053556356, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1669309200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 3}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669374000, 'flash_sale_stock': 50, 'promotionid': 688463643270049, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1669352400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 50}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669374000, 'flash_sale_stock': 30, 'promotionid': 123193253957632, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669352400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1549000000, 'stock': 29}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1669374000, 'flash_sale_stock': 50, 'promotionid': 688463643270049, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1669352400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1090000000, 'stock': 50}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1669384800, 'flash_sale_stock': 5, 'promotionid': 688601730241572, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669374000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1050000000, 'stock': 5}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669471200, 'flash_sale_stock': 30, 'promotionid': 123214307315712, 'lowest_past_price': None, 'promo_images': ['sg-11134201-22110-rqlicwaxz6jvdb'], 'start_time': 1669460400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1129000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669525200, 'flash_sale_stock': 20, 'promotionid': 120458257326080, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1669482000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 990000000, 'stock': 18}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669525200, 'flash_sale_stock': 20, 'promotionid': 120458257326080, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1669482000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 990000000, 'stock': 17}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1669546800, 'flash_sale_stock': 50, 'promotionid': 688833710858145, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1669525200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 50}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1669546800, 'flash_sale_stock': 50, 'promotionid': 688833710858145, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1669525200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 48}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669557600, 'flash_sale_stock': 30, 'promotionid': 120461742788610, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669546800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 30}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1669557600, 'flash_sale_stock': 30, 'promotionid': 123215318093825, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1669546800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 849000000, 'stock': 30}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1669633200, 'flash_sale_stock': 5, 'promotionid': 689144479420452, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669611600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 5}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1669644000, 'flash_sale_stock': 50, 'promotionid': 120462613118976, 'lowest_past_price': None, 'promo_images': ['82a15c99269e0bfbcf3d5c5ab37e7689'], 'start_time': 1669633200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 270400000, 'stock': 49}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669654800, 'flash_sale_stock': 20, 'promotionid': 689201647785889, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1669644000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 19}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669719600, 'flash_sale_stock': 30, 'promotionid': 120463162564608, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669698000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 30}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669719600, 'flash_sale_stock': 30, 'promotionid': 120463162564608, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669698000, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1078200000, 'stock': 26}",
           "{'price_before_discount': 1699000000, 'hidden_price_display': None, 'end_time': 1669730400, 'flash_sale_stock': 30, 'promotionid': 124048770338817, 'lowest_past_price': None, 'promo_images': ['bb637bbcfff75fb6ed60205b09fd0c00'], 'start_time': 1669719600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 799000000, 'stock': 30}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 20, 'promotionid': 120463833661440, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 20, 'promotionid': 689500158500451, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 20}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 10, 'promotionid': 689495572022099, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 970000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 20, 'promotionid': 689362363030433, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 20}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 30, 'promotionid': 689362363030433, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 970000000, 'stock': 30}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 30, 'promotionid': 689362363030433, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 970000000, 'stock': 23}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 20, 'promotionid': 689362363030433, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 19}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669806000, 'flash_sale_stock': 20, 'promotionid': 120463833661440, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669784400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1549000000, 'stock': 19}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1669816800, 'flash_sale_stock': 5, 'promotionid': 689198036491300, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1669806000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669827600, 'flash_sale_stock': 20, 'promotionid': 120464072712192, 'lowest_past_price': None, 'promo_images': ['60aaea4fe52b112fca2bf6c02bf52da8'], 'start_time': 1669816800, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1489500000, 'stock': 20}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1669870800, 'flash_sale_stock': 10, 'promotionid': 689510923178628, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1669827600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1669914000, 'flash_sale_stock': 200, 'promotionid': 124401148497920, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1669903200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 220000000, 'stock': 200}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669957200, 'flash_sale_stock': 50, 'promotionid': 124401769254913, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669914000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1129000000, 'stock': 50}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669957200, 'flash_sale_stock': 50, 'promotionid': 124401769254913, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669914000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1129000000, 'stock': 46}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1669957200, 'flash_sale_stock': 50, 'promotionid': 124401769254913, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1669914000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 1129000000, 'stock': 44}",
           "{'price_before_discount': 2600000000, 'hidden_price_display': None, 'end_time': 1669978800, 'flash_sale_stock': 5, 'promotionid': 689862120636525, 'lowest_past_price': None, 'promo_images': ['b8f5d6f3cfe31e7764b725dcc8614868'], 'start_time': 1669957200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 879000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1670043600, 'flash_sale_stock': 5, 'promotionid': 689892489502340, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1670000400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 5}",
           "{'price_before_discount': 1999900000, 'hidden_price_display': None, 'end_time': 1670043600, 'flash_sale_stock': 5, 'promotionid': 689892489502340, 'lowest_past_price': None, 'promo_images': ['553f9ee3347a361ed88d6e1dff363a83'], 'start_time': 1670000400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 990000000, 'stock': 4}",
           "{'price_before_discount': 2141400000, 'hidden_price_display': None, 'end_time': 1670065200, 'flash_sale_stock': 5, 'promotionid': 690062969082916, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1670043600, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 5}",
           "{'price_before_discount': 1700000000, 'hidden_price_display': None, 'end_time': 1670086800, 'flash_sale_stock': 10, 'promotionid': 690100774439841, 'lowest_past_price': None, 'promo_images': ['4be03248bfbc47be3234d3a451b79f25'], 'start_time': 1670076000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1150000000, 'stock': 10}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1670151600, 'flash_sale_stock': 10, 'promotionid': 690064401435475, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1670130000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 10}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1670151600, 'flash_sale_stock': 50, 'promotionid': 689865738230813, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1670130000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 209900000, 'stock': 50}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1670151600, 'flash_sale_stock': 5, 'promotionid': 690100600374177, 'lowest_past_price': None, 'promo_images': ['8c859232df55bbc4b2df09031fe3e0d1'], 'start_time': 1670130000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1180000000, 'stock': 5}",
           "{'price_before_discount': 269900000, 'hidden_price_display': None, 'end_time': 1670151600, 'flash_sale_stock': 50, 'promotionid': 689865738230813, 'lowest_past_price': None, 'promo_images': ['dac30dea362444b3186770eb5bd4df22'], 'start_time': 1670130000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 209900000, 'stock': 49}",
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1670151600, 'flash_sale_stock': 10, 'promotionid': 690064401435475, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1670130000, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 980000000, 'stock': 9}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1670216400, 'flash_sale_stock': 50, 'promotionid': 122444895735809, 'lowest_past_price': None, 'promo_images': ['82a15c99269e0bfbcf3d5c5ab37e7689'], 'start_time': 1670173200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 289000000, 'stock': 49}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1670216400, 'flash_sale_stock': 80, 'promotionid': 125155926134785, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1670173200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 80}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1670216400, 'flash_sale_stock': 80, 'promotionid': 125155926134785, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1670173200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 79}",
           "{'price_before_discount': 409000000, 'hidden_price_display': None, 'end_time': 1670216400, 'flash_sale_stock': 50, 'promotionid': 122444895735809, 'lowest_past_price': None, 'promo_images': ['82a15c99269e0bfbcf3d5c5ab37e7689'], 'start_time': 1670173200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 289000000, 'stock': 47}",
           "{'price_before_discount': 199000000, 'hidden_price_display': None, 'end_time': 1670216400, 'flash_sale_stock': 80, 'promotionid': 125155926134785, 'lowest_past_price': None, 'promo_images': ['d64b7f28c0174f976d5f9bc9ba112b2d'], 'start_time': 1670173200, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 1, 'price': 139900000, 'stock': 78}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1670302800, 'flash_sale_stock': 50, 'promotionid': 122446376275969, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1670259600, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1008200000, 'stock': 50}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1670302800, 'flash_sale_stock': 50, 'promotionid': 122446376275969, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1670259600, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1008200000, 'stock': 47}",
           "{'price_before_discount': 1499000000, 'hidden_price_display': None, 'end_time': 1670302800, 'flash_sale_stock': 50, 'promotionid': 122446376275969, 'lowest_past_price': None, 'promo_images': ['db1455ff51f4185d24ebdf8475dd1ecd'], 'start_time': 1670259600, 'promo_overlay_image': '9beb2804cf539d52301662af8f28965e', 'extra_discount_info': None, 'flash_sale_type': 0, 'price': 1008200000, 'stock': 45}"],
          dtype=object)




```python
flash_sale = df[df['flash_sale'].notnull()]
print('Number of records:',len(df))
print('Number of records after filter only flash sale:',len(flash_sale))
```

    Number of records: 30679
    Number of records after filter only flash sale: 1197
    


```python
flash_sale = df.drop_duplicates(subset=['flash_sale'])
fs_groupby_DH = flash_sale.groupby(['modelid','day_hour'])[['day_hour']].count()
```


```python
fs_groupby_DH = fs_groupby_DH.rename(columns = {'day_hour':'count_dh'})
```


```python
fs_groupby_DH = fs_groupby_DH.reset_index()
```


```python
fs_groupby_DH
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>modelid</th>
      <th>day_hour</th>
      <th>count_dh</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>21190966793</td>
      <td>05-00</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21190966793</td>
      <td>05-03</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21190966793</td>
      <td>05-09</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>21190966793</td>
      <td>10-00</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>21190966793</td>
      <td>10-01</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>515</th>
      <td>172837567688</td>
      <td>11-18</td>
      <td>1</td>
    </tr>
    <tr>
      <th>516</th>
      <td>172837567688</td>
      <td>15-00</td>
      <td>1</td>
    </tr>
    <tr>
      <th>517</th>
      <td>172837567688</td>
      <td>25-00</td>
      <td>2</td>
    </tr>
    <tr>
      <th>518</th>
      <td>172837567688</td>
      <td>30-12</td>
      <td>2</td>
    </tr>
    <tr>
      <th>519</th>
      <td>172837567688</td>
      <td>31-00</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>520 rows × 3 columns</p>
</div>




```python
most_flash_sale = fs_groupby_DH.groupby(['day_hour'])[['count_dh']].sum().reset_index()
```


```python
most_flash_sale
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>day_hour</th>
      <th>count_dh</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>01-00</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>01-04</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>01-09</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>01-10</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>01-18</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>276</th>
      <td>31-11</td>
      <td>2</td>
    </tr>
    <tr>
      <th>277</th>
      <td>31-12</td>
      <td>3</td>
    </tr>
    <tr>
      <th>278</th>
      <td>31-13</td>
      <td>1</td>
    </tr>
    <tr>
      <th>279</th>
      <td>31-14</td>
      <td>1</td>
    </tr>
    <tr>
      <th>280</th>
      <td>31-16</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>281 rows × 2 columns</p>
</div>




```python
most_flash_sale = most_flash_sale.sort_values(by=['count_dh'],ascending=False).reset_index()
most_flash_sale
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>day_hour</th>
      <th>count_dh</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>206</td>
      <td>25-00</td>
      <td>10</td>
    </tr>
    <tr>
      <th>1</th>
      <td>113</td>
      <td>15-00</td>
      <td>10</td>
    </tr>
    <tr>
      <th>2</th>
      <td>129</td>
      <td>15-21</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>263</td>
      <td>30-12</td>
      <td>9</td>
    </tr>
    <tr>
      <th>4</th>
      <td>93</td>
      <td>11-00</td>
      <td>8</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>276</th>
      <td>136</td>
      <td>16-15</td>
      <td>1</td>
    </tr>
    <tr>
      <th>277</th>
      <td>138</td>
      <td>17-00</td>
      <td>1</td>
    </tr>
    <tr>
      <th>278</th>
      <td>139</td>
      <td>17-01</td>
      <td>1</td>
    </tr>
    <tr>
      <th>279</th>
      <td>1</td>
      <td>01-04</td>
      <td>1</td>
    </tr>
    <tr>
      <th>280</th>
      <td>280</td>
      <td>31-16</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>281 rows × 3 columns</p>
</div>



## Top 10 flash sale frequency by day_hour


```python
fig = plt.figure(figsize = (10, 5))
freq = plt.bar(most_flash_sale['day_hour'][:10], most_flash_sale['count_dh'][:10], color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
fig.suptitle('Top 10 flash sale frequency by day_hour')
plt.xlabel('day_hour of flash sale')
plt.ylabel('count transaction of flash sale')
```




    Text(0, 0.5, 'count transaction of flash sale')




    
![png](output_27_1.png)
    


The most popular time to do a flash sale is the 15th of the month at 3pm, followed by the 15th day at midnight and the 15th is the middle of the month. Therefore, during the middle of the sale, it will be popular to do at the time. Midnight and 3pm.

As for PayDay sale (25th until the end of the month), it is popular to do flash sale during noon and midnight.

##  Compare 3 sales campaigns

Shopee have 3 sales campaigns
1. Mega sale: day = month
2. Mid month sale: Every 15th day of the month
3. Payday sale: Every 25th until the end of the month


```python
# Extract day and hour from day_hour
df['day'] = df['day_hour'].apply(lambda x : x.split('-')[0]).astype(int)
df['hour'] = df['day_hour'].apply(lambda x : x.split('-')[1]).astype(int)
```

### Create 3 new dataframe by sale campaign


```python
mega_sale_df = df[(df['mega_sale']==True)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').reset_index(drop=True)
mega_sale_fr = len(mega_sale_df)
mega_sale_fr
```




    98




```python
mid_month_sale_df = df[(df['day']==15)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').reset_index(drop=True)
mid_month_sale_fr = len(mid_month_sale_df)
mid_month_sale_fr
```




    60




```python
pay_day_sale_df = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').reset_index(drop=True)
pay_day_sale_fr = len(pay_day_sale_df)
pay_day_sale_fr
```




    151




```python
fig = plt.figure(figsize = (10, 5))
freq = plt.bar(['Mega campaign','Mid Month campaign','PayDay campaign'], [mega_sale_fr,mid_month_sale_fr,pay_day_sale_fr], color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
fig.suptitle('Frequency transaction product of each sales campaign', fontsize=17)
plt.xlabel('Sales campaigns', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```




    Text(0, 0.5, 'Count transaction of flash sale')




    
![png](output_35_1.png)
    


An overview of the campaigns that have a lot of flash sales are payday campaign (This campaign has several days, so there may be many transactions), followed by a mega sale campaign.

## Details of Payday campaign (Payday campaign has several campaign periods.)

###  Freqency by day and hour


```python
pay_day_sale = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').groupby(['day','hour'])[['hour']].count().rename(columns={'hour':'count'}).reset_index()
pay_day_sale['day_hour'] = pay_day_sale['day'].astype(str) +'-' +pay_day_sale['hour'].astype(str)
pay_day_sale = pay_day_sale.sort_values(by=['count'],ascending=False).reset_index()

fig = plt.figure(figsize = (10, 5))
freq = plt.bar(pay_day_sale['day_hour'][:10], pay_day_sale['count'][:10], color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
fig.suptitle('Frequency transaction product of PayDay sales campaign', fontsize=17)
plt.xlabel('Day and hour', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```




    Text(0, 0.5, 'Count transaction of flash sale')




    
![png](output_39_1.png)
    


### Freqency by hour


```python
pay_day_sale = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').groupby(['hour'])[['hour']].count().rename(columns={'hour':'count'}).reset_index()
pay_day_sale = pay_day_sale.sort_values(by=['count'],ascending=False).reset_index()
pay_day_sale

fig = plt.figure(figsize = (10, 5))
freq = plt.bar(pay_day_sale['hour'][:10], pay_day_sale['count'][:10], color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
_ = plt.xticks(pay_day_sale['hour'])
fig.suptitle('Frequency transaction product of PayDay sales campaign', fontsize=17)
plt.xlabel('Day and hour', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```




    Text(0, 0.5, 'Count transaction of flash sale')




    
![png](output_41_1.png)
    


### Freqency by day


```python
pay_day_sale = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').groupby(['day'])[['day']].count().rename(columns={'day':'count'}).reset_index()
pay_day_sale = pay_day_sale.sort_values(by=['count'],ascending=False).reset_index()
pay_day_sale

fig = plt.figure(figsize = (10, 5))
freq = plt.bar(pay_day_sale['day'][:10], pay_day_sale['count'][:10], color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
_ = plt.xticks(pay_day_sale['day'])
fig.suptitle('Frequency transaction product of PayDay sales campaign', fontsize=17)
plt.xlabel('Day and hour', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```




    Text(0, 0.5, 'Count transaction of flash sale')




    
![png](output_43_1.png)
    


PayDay sales campaign

1.1 Most popular hour to do flash sale is 12:00, 00:00, 18:00 and 15:00 respectively. Most sales behaviors are every three hours apart.

1.2 The date of the flash sale The highest during Payday is the 25th (First date of PayDay sales campaign).

1.3 The peak flash sale days and hour during Payday are 25th-00:00, 30th-12:00, 25th-12:00, 27th-12:00 respectively.

# Flash sale duration time 

The duration time of the flash sale divided by each campaign.


```python
def extract_duration(row):
    flash_sale_dict = eval(row)
    temp = datetime.fromtimestamp(flash_sale_dict['end_time']) - datetime.fromtimestamp(flash_sale_dict['start_time'])
    return temp.seconds//3600
```


```python
mega_sale_df['duration'] = mega_sale_df['flash_sale'].apply(extract_duration)
mega_sale_df['duration'].mean()
```




    2.693877551020408




```python
mid_month_sale_df['duration'] = mid_month_sale_df['flash_sale'].apply(extract_duration)
mid_month_sale_df['duration'].mean()
```




    3.5166666666666666




```python
pay_day_sale_df['duration'] = pay_day_sale_df['flash_sale'].apply(extract_duration)
pay_day_sale_df['duration'].mean()
```




    7.529801324503311




```python
fig = plt.figure(figsize = (10, 5))
freq = plt.bar(['Mega campaign','Mid month campaign','PayDay campaign'],
        [mega_sale_df['duration'].mean(),mid_month_sale_df['duration'].mean(),pay_day_sale_df['duration'].mean()], 
        color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
fig.suptitle('Duration times of Flash sale by sales campaign', fontsize=17)
plt.xlabel('Sales Campaigns', fontsize=15)
plt.ylabel('Duration time (Hours)', fontsize=15)
```




    Text(0, 0.5, 'Duration time (Hours)')




    
![png](output_50_1.png)
    


## Pattern of the flash sale hour of each campaign.


```python
def groupby_time_series(df):
    flash_hour_df= pd.DataFrame()
    hour = []
    modelid = []
    for i in range(len(df)) :
        fs_dict = eval(df['flash_sale'].loc[i])
        fs_dict['start_time']
        for h in range(int(datetime.fromtimestamp(fs_dict['start_time']).strftime('%H')),int(datetime.fromtimestamp(fs_dict['end_time']).strftime('%H'))+1):
            modelid.append(df['modelid'].loc[i])
            hour.append(h)
    flash_hour_df['modelid'] = modelid
    flash_hour_df['hour'] = hour
    flash_hour_groupby = flash_hour_df.groupby(['hour'])[['modelid']].count().reset_index()
    for i in range(0,24):
        if i not in flash_hour_groupby['hour'].unique().tolist():
#             print(i)
            flash_hour_groupby = flash_hour_groupby.append(pd.Series({'hour': i, 'modelid':0}),ignore_index=True)
    return flash_hour_groupby
```


```python
mega_sale_timeseries =  groupby_time_series(mega_sale_df)
mid_month_timeseries =  groupby_time_series(mid_month_sale_df)
pay_day_timeseries =  groupby_time_series(pay_day_sale_df)
```


```python
fig = plt.figure(figsize = (20, 10))
plt.plot(mega_sale_timeseries['hour'], mega_sale_timeseries['modelid'],label="Mega campaign")
plt.plot(mid_month_timeseries['hour'], mid_month_timeseries['modelid'],label="Mid month campaign")
plt.plot(pay_day_timeseries['hour'], pay_day_timeseries['modelid'],label="PayDay campaign")
_ = plt.xticks(mega_sale_timeseries['hour'])
plt.legend(loc="upper left",prop={'size':15})
    
fig.suptitle('The frequency of flash sales in each hour by sales campaign', fontsize=17)
plt.xlabel('Hours of the day', fontsize=15)
plt.ylabel('Number of transactions', fontsize=15)
```




    Text(0, 0.5, 'Number of transactions')




    
![png](output_54_1.png)
    


The overall picture of flash sales is popular during 02:00 (may have started flash sales since midnight or 1am), 9A.M., 12:00, 14:00, 16:00 , 18:00

By campaign: Mega Campaign and Mid month Campaign, There is a flash sale at each period that is similar. Is to focus on doing during the night. As for Payday campaign, there will be a different pattern. That is, there will be the most flash sales in the daytime at 12:00 and again at 18:00.

# Explore by Brand
Explore the discounting behavior of brands selling on the platform.


```python
# All brand in dataframe (Filter only transaction that flash sale)

brand = [i for i in df['brand'].dropna().unique().tolist()]

brand_count = [len(df[df['brand']==i]['itemid'].unique()) for i in brand]
brand_count
```




    [10, 4, 8, 1, 2, 4, 2, 1]




```python
df_brand = pd.DataFrame()
df_brand['brand'] = brand
df_brand['countd_itemid'] = [len(df[df['brand']==i]['itemid'].unique()) for i in brand]
df_brand['count_itemid']  = [len(df[df['brand']==i]['itemid']) for i in brand]
df_brand
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brand</th>
      <th>countd_itemid</th>
      <th>count_itemid</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>10</td>
      <td>11140</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Amazfit (อเมซฟิต)</td>
      <td>4</td>
      <td>4417</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Xiaomi(เสี่ยวมี่)</td>
      <td>8</td>
      <td>6529</td>
    </tr>
    <tr>
      <th>3</th>
      <td>iRobot(ไอโรบอท)</td>
      <td>1</td>
      <td>1082</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Pando(แพนโด้)</td>
      <td>2</td>
      <td>2234</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Haier(ไฮเออร์)</td>
      <td>4</td>
      <td>3027</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Ecovacs(อีโคแวคส์)</td>
      <td>2</td>
      <td>1493</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Mister Robot(มิสเตอร์โรบอต)</td>
      <td>1</td>
      <td>756</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig = plt.figure(figsize = (15, 10))
label = [i.split('(')[0]+' ('+str(brand_count[index])+')' for index,i in enumerate(brand)]

_ = plt.pie(brand_count, labels = label , autopct=lambda p: '{:.2f}%'.format(p), textprops={'fontsize': 10}, wedgeprops = { 'linewidth' : 1, 'edgecolor' : 'white' },colors=sns.color_palette('Set2'))
```


    
![png](output_59_0.png)
    


Compare between Mall official shop and unofficial shop (Not Mall)


```python
official = df[['brand','shopid','is_official_shop']].drop_duplicates()
official = official.groupby(['brand','is_official_shop'])[['is_official_shop']].count()
```


```python
official = official.rename(columns={'is_official_shop':'count_ofiicial'}).reset_index()
```


```python
official
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brand</th>
      <th>is_official_shop</th>
      <th>count_ofiicial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Amazfit (อเมซฟิต)</td>
      <td>f</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Amazfit (อเมซฟิต)</td>
      <td>t</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ecovacs(อีโคแวคส์)</td>
      <td>t</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Haier(ไฮเออร์)</td>
      <td>f</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Haier(ไฮเออร์)</td>
      <td>t</td>
      <td>2</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Mister Robot(มิสเตอร์โรบอต)</td>
      <td>t</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Pando(แพนโด้)</td>
      <td>t</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>f</td>
      <td>5</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>t</td>
      <td>4</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Xiaomi(เสี่ยวมี่)</td>
      <td>f</td>
      <td>1</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Xiaomi(เสี่ยวมี่)</td>
      <td>t</td>
      <td>2</td>
    </tr>
    <tr>
      <th>11</th>
      <td>iRobot(ไอโรบอท)</td>
      <td>t</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Fill null value of is_official_shop
for i in official['brand'].unique().tolist():
    if len(official[official['brand']==i]['is_official_shop']) < 2:
        if official[official['brand']==i]['is_official_shop'].values == 't':
            official = official.append(pd.Series({'brand': i, 'is_official_shop':'f','count_ofiicial':0}),ignore_index=True)
        else:
            official = official.append(pd.Series({'brand': i, 'is_official_shop':'t','count_ofiicial':0}),ignore_index=True)
```


```python
official = official.sort_values(by=['brand','is_official_shop'],ascending=True)
official
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brand</th>
      <th>is_official_shop</th>
      <th>count_ofiicial</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Amazfit (อเมซฟิต)</td>
      <td>f</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Amazfit (อเมซฟิต)</td>
      <td>t</td>
      <td>3</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Ecovacs(อีโคแวคส์)</td>
      <td>f</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ecovacs(อีโคแวคส์)</td>
      <td>t</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Haier(ไฮเออร์)</td>
      <td>f</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Haier(ไฮเออร์)</td>
      <td>t</td>
      <td>2</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Mister Robot(มิสเตอร์โรบอต)</td>
      <td>f</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Mister Robot(มิสเตอร์โรบอต)</td>
      <td>t</td>
      <td>1</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Pando(แพนโด้)</td>
      <td>f</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Pando(แพนโด้)</td>
      <td>t</td>
      <td>1</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>f</td>
      <td>5</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>t</td>
      <td>4</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Xiaomi(เสี่ยวมี่)</td>
      <td>f</td>
      <td>1</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Xiaomi(เสี่ยวมี่)</td>
      <td>t</td>
      <td>2</td>
    </tr>
    <tr>
      <th>15</th>
      <td>iRobot(ไอโรบอท)</td>
      <td>f</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>iRobot(ไอโรบอท)</td>
      <td>t</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
from matplotlib.pyplot import figure

figure(figsize=(20, 10), dpi=200)

x_labels = [i.split('(')[0] for i in official['brand'].unique().tolist()]

X_axis = np.arange(len(x_labels))

freq1 = plt.bar(X_axis - 0.2, official[official['is_official_shop']=='t']['count_ofiicial'], 0.4, label = 'Mall')
freq2 = plt.bar(X_axis + 0.2, official[official['is_official_shop']=='f']['count_ofiicial'], 0.4, label = 'Not Mall',color = 'orange')

for f in freq1:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')

for f in freq2:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
plt.title('Propotion of mall shop and not mall shop by brand', fontsize=17)
plt.xlabel('Brand', fontsize=15)
plt.ylabel('Number of shops', fontsize=15)

plt.xticks(X_axis,x_labels)
plt.legend()
plt.show()
```


    
![png](output_66_0.png)
    


## Campaign styles for each brand

### Official/Mall Brand


```python
count_overall_sale_mall = mega_sale_df[mega_sale_df['is_official_shop']=='t'].groupby(['brand'])[['brand']].count().rename(columns={'brand':'count_mega_sale'}).reset_index()
temp = mid_month_sale_df[mid_month_sale_df['is_official_shop']=='t'].groupby(['brand'])[['brand']].count().rename(columns={'brand':'count_mid_month'}).reset_index()
temp1 = pay_day_sale_df[pay_day_sale_df['is_official_shop']=='t'].groupby(['brand'])[['brand']].count().rename(columns={'brand':'count_pay_day'}).reset_index() 
count_overall_sale_mall = pd.concat([count_overall_sale_mall,temp['count_mid_month'],temp1['count_pay_day']],axis=1)
count_overall_sale_mall = pd.merge(count_overall_sale_mall,temp,how='left',on='brand').drop('count_mid_month_y',axis=1).rename(columns={'count_mid_month_x':'count_mid_month'})
count_overall_sale_mall = pd.merge(count_overall_sale_mall,temp1,how='left',on='brand').drop('count_pay_day_x',axis=1).rename(columns={'count_pay_day_y':'count_pay_day'})
count_overall_sale_mall = count_overall_sale_mall.fillna(0)
count_overall_sale_mall['count_pay_day'] = count_overall_sale_mall['count_pay_day'].astype(int)
```


```python
count_overall_sale_mall
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brand</th>
      <th>count_mega_sale</th>
      <th>count_mid_month</th>
      <th>count_pay_day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Amazfit (อเมซฟิต)</td>
      <td>18</td>
      <td>13</td>
      <td>27</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ecovacs(อีโคแวคส์)</td>
      <td>6</td>
      <td>2</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Haier(ไฮเออร์)</td>
      <td>4</td>
      <td>5</td>
      <td>15</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mister Robot(มิสเตอร์โรบอต)</td>
      <td>6</td>
      <td>3</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Pando(แพนโด้)</td>
      <td>14</td>
      <td>5</td>
      <td>21</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>24</td>
      <td>17</td>
      <td>50</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Xiaomi(เสี่ยวมี่)</td>
      <td>23</td>
      <td>12</td>
      <td>18</td>
    </tr>
  </tbody>
</table>
</div>




```python
figure(figsize=(20, 10), dpi=200)

label = [i.split('(')[0] for i in count_overall_sale_mall['brand']]
ax1 = plt.bar(label, count_overall_sale_mall['count_mega_sale'], color='lightsalmon', label='Mega sale campaign')
ax2 = plt.bar(label, count_overall_sale_mall['count_mid_month'], bottom=count_overall_sale_mall['count_mega_sale'], color='lightblue', label='Mid Month sale campaign')
ax3 = plt.bar(label, count_overall_sale_mall['count_pay_day'], bottom=count_overall_sale_mall['count_mega_sale']+count_overall_sale_mall['count_mid_month'], color='pink',label='PayDay sale campaign')
plt.title('Number of Items in Official Mall Brand', fontsize=17)
plt.xlabel('Brand', fontsize=15)
plt.ylabel('Number of items', fontsize=15)

for r1, r2, r3 in zip(ax1, ax2, ax3):
    h1 = r1.get_height()
    h2 = r2.get_height()
    h3 = r3.get_height()

    plt.text(r1.get_x() + r1.get_width() / 2., h1 / 2., "{0:.2f}%".format((h1/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    plt.text(r2.get_x() + r2.get_width() / 2., h1 + h2 / 2., "{0:.2f}%".format((h2/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    plt.text(r3.get_x() + r2.get_width() / 2., h1 + h2 + h3 / 2., "{0:.2f}%".format((h3/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)

plt.legend()

a = plt.show()
```


    
![png](output_70_0.png)
    


Campaign types are divided as follows

Popular brands doing sales in :
- Mega campaign (red): Ecovacs, Mister Robot, Xiaomi
- Mid month campaign (blue): -
- Payday campaign (green): Amazfit, Haier, Pandp, Petkit

### Unofficial/Not mall brand


```python
count_overall_sale_not_mall = mega_sale_df[mega_sale_df['is_official_shop']=='f'].groupby(['brand'])[['brand']].count().rename(columns={'brand':'count_mega_sale'}).reset_index()
temp = mid_month_sale_df[mid_month_sale_df['is_official_shop']=='f'].groupby(['brand'])[['brand']].count().rename(columns={'brand':'count_mid_month'}).reset_index()
temp1 = pay_day_sale_df[pay_day_sale_df['is_official_shop']=='f'].groupby(['brand'])[['brand']].count().rename(columns={'brand':'count_pay_day'}).reset_index() 
count_overall_sale_not_mall = pd.concat([count_overall_sale_not_mall,temp['count_mid_month'],temp1['count_pay_day']],axis=1)
count_overall_sale_not_mall = pd.merge(count_overall_sale_not_mall,temp,how='left',on='brand').drop('count_mid_month_y',axis=1).rename(columns={'count_mid_month_x':'count_mid_month'})
count_overall_sale_not_mall = pd.merge(count_overall_sale_not_mall,temp1,how='left',on='brand').drop('count_pay_day_x',axis=1).rename(columns={'count_pay_day_y':'count_pay_day'})
count_overall_sale_not_mall = count_overall_sale_not_mall.fillna(0)
count_overall_sale_not_mall['count_pay_day'] = count_overall_sale_not_mall['count_pay_day'].astype(int)
```


```python
count_overall_sale_not_mall
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brand</th>
      <th>count_mega_sale</th>
      <th>count_mid_month</th>
      <th>count_pay_day</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>3</td>
      <td>3</td>
      <td>15</td>
    </tr>
  </tbody>
</table>
</div>




```python
figure(figsize=(5, 5))

label = [i.split('(')[0] for i in count_overall_sale_not_mall['brand']]
ax1 = plt.bar(label, count_overall_sale_not_mall['count_mega_sale'], color='lightsalmon', label = 'Mega sale campaign')
ax2 = plt.bar(label, count_overall_sale_not_mall['count_mid_month'], bottom=count_overall_sale_not_mall['count_mega_sale'], color='lightblue', label = 'Mid month sale campaign')
ax3 = plt.bar(label, count_overall_sale_not_mall['count_pay_day'], bottom=count_overall_sale_not_mall['count_mega_sale']+count_overall_sale_not_mall['count_mid_month'], color='pink', label = 'PayDay sale campaign')
plt.title('Number of Items in Unofficial/Not mall Brand', fontsize=17)
plt.xlabel('Brand', fontsize=15)
plt.ylabel('Number of items', fontsize=15)

for r1, r2, r3 in zip(ax1, ax2, ax3):
    h1 = r1.get_height()
    h2 = r2.get_height()
    h3 = r3.get_height()

    plt.text(r1.get_x() + r1.get_width() / 2., h1 / 2., "{0:.2f}%".format((h1/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    plt.text(r2.get_x() + r2.get_width() / 2., h1 + h2 / 2., "{0:.2f}%".format((h2/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    plt.text(r3.get_x() + r2.get_width() / 2., h1 + h2 + h3 / 2., "{0:.2f}%".format((h3/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)

plt.legend()
a = plt.show()
```


    
![png](output_75_0.png)
    


There is only one unofficial brand = Petkit, which has the most Payday campaigns.

# Relationship between discount and sales


```python
df = pd.read_csv('shopee_project.csv')
unique_id = []
for i in df['itemid'].unique().tolist():
    if len(df[df['itemid']==i]['modelid'].unique()) == 1:
#         print(i)
        unique_id.append(i)
df['brand'] = df['brand'].replace('Petkit(เพ็ทคิต)','Petkit(เพ็ทคิท)')
df = df[df['itemid'].isin(unique_id)].reset_index(drop=True)
```


```python
def extract_year(row):
    date = datetime.strptime(row, '%Y-%m-%d %H:%M:%S')
    return date.strftime('%Y')
```


```python
df['year'] = df['ingest_date'].apply(extract_year)
df = df[df['year']=='2022']
```


```python
# Preview dataframe before calculate sales, stock ,discount, duration of flashsale
df[df['flash_sale'].notnull()][['modelid','ingest_date','stock','flash_sale','price']][:10]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>modelid</th>
      <th>ingest_date</th>
      <th>stock</th>
      <th>flash_sale</th>
      <th>price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>56</th>
      <td>115174576667</td>
      <td>2022-09-09 01:00:00</td>
      <td>6</td>
      <td>{'price_before_discount': 1499000000, 'hidden_...</td>
      <td>11490</td>
    </tr>
    <tr>
      <th>57</th>
      <td>91345241895</td>
      <td>2022-09-09 01:00:00</td>
      <td>9</td>
      <td>{'price_before_discount': 2141900000, 'hidden_...</td>
      <td>11900</td>
    </tr>
    <tr>
      <th>58</th>
      <td>172837567688</td>
      <td>2022-09-09 01:00:00</td>
      <td>30</td>
      <td>{'price_before_discount': 2141900000, 'hidden_...</td>
      <td>11900</td>
    </tr>
    <tr>
      <th>179</th>
      <td>91345241895</td>
      <td>2022-10-17 12:00:01</td>
      <td>10</td>
      <td>{'price_before_discount': 2141900000, 'hidden_...</td>
      <td>10900</td>
    </tr>
    <tr>
      <th>180</th>
      <td>91345241895</td>
      <td>2022-10-17 12:00:01</td>
      <td>10</td>
      <td>{'price_before_discount': 2141900000, 'hidden_...</td>
      <td>10900</td>
    </tr>
    <tr>
      <th>215</th>
      <td>171396661950</td>
      <td>2022-09-09 00:00:00</td>
      <td>50</td>
      <td>{'price_before_discount': 1700000000, 'hidden_...</td>
      <td>11500</td>
    </tr>
    <tr>
      <th>217</th>
      <td>90444301281</td>
      <td>2022-09-09 00:00:00</td>
      <td>40</td>
      <td>{'price_before_discount': 1890000000, 'hidden_...</td>
      <td>14000</td>
    </tr>
    <tr>
      <th>239</th>
      <td>61970382186</td>
      <td>2022-10-04 15:00:01</td>
      <td>20</td>
      <td>{'price_before_discount': 1999900000, 'hidden_...</td>
      <td>10590</td>
    </tr>
    <tr>
      <th>242</th>
      <td>44602375718</td>
      <td>2022-10-04 15:00:01</td>
      <td>5</td>
      <td>{'price_before_discount': 2141400000, 'hidden_...</td>
      <td>11900</td>
    </tr>
    <tr>
      <th>267</th>
      <td>124955024348</td>
      <td>2022-09-09 13:00:01</td>
      <td>37</td>
      <td>{'price_before_discount': 2141900000, 'hidden_...</td>
      <td>11900</td>
    </tr>
  </tbody>
</table>
</div>




```python
sale_diff = pd.DataFrame(columns=['sale_stock','price_diff','hour_duration','modelid'])
for m_id in df[df['flash_sale'].notnull()]['modelid'].unique().tolist():
#     print('modelid:',modelid)
    modelid = m_id
    temp = df[df['modelid']==modelid].sort_values(['ingest_date'])[['modelid','ingest_date','stock','flash_sale','price']].reset_index(drop=True)
    n = 0

    sale_stock = []
    price_diff = []
    hour_duration = []
    for i in temp[temp['flash_sale'].notnull()].index.tolist():
#         print('current index',i)
        if n == 0:
            n+=1
            start_index = i
            start_stock = temp['stock'].loc[i]
            start_price = temp['price'].loc[i]
#             last_index = i
            hour = 1
        elif i - last_index > 1 or i == temp[temp['flash_sale'].notnull()].index.tolist()[-1]:
            if repeat == True:
                start_index = i
                start_stock = temp['stock'].loc[i]
                start_price = temp['price'].loc[i]
                last_index = i
                hour = 1
            else:
#                 print('---------------')
#                 print('start_index',start_index)
#                 print('last_index',last_index)
#                 print('start_stock ',start_stock,'last_stock ',last_stock)
#                 print(start_stock - last_stock)
                if start_index == 0:
                    pass
                else:
#                     print(temp['price'].loc[start_index - 1])
#                     print(start_price)
#                     print('hour_duration',hour)
#                     print('---------------')
                    sale_stock.append(start_stock - last_stock)
                    price_diff.append((temp['price'].loc[start_index - 1]-start_price)/temp['price'].loc[start_index - 1]*100)
                    hour_duration.append(hour)

                    start_index = i
                    start_stock = temp['stock'].loc[i]
                    start_price = temp['price'].loc[i]
                    last_index = i
                    hour = 1

            repeat = True

        else:
            repeat = False
            last_index = i
            last_stock = temp['stock'].loc[i]
            hour +=1

    temp_df = pd.DataFrame()
    temp_df['sale_stock'] = sale_stock
    temp_df['price_diff'] = price_diff
    temp_df['hour_duration'] = hour_duration
    temp_df['modelid'] = modelid
    
    sale_diff = sale_diff.append(temp_df)
```


```python
sale_diff['sale_stock'] =  sale_diff['sale_stock']//sale_diff['hour_duration']
```


```python
sale_diff = sale_diff[(sale_diff['price_diff']>=0) & (sale_diff['sale_stock']>=0)]
```


```python
figure(figsize=(15, 10), dpi=200)
plt.scatter(sale_diff['price_diff'], sale_diff['sale_stock'])
plt.title('Scatter plot between %discount and product sales', fontsize=17)
plt.xlabel('% Discount', fontsize=15)
plt.ylabel('Number of product sales', fontsize=15)
# _ = plt.xticks(range(0,70,1))

```




    Text(0, 0.5, 'Number of product sales')




    
![png](output_85_1.png)
    



```python
sale_diff = sale_diff[(sale_diff['price_diff']>=0) & (sale_diff['sale_stock']>=0) & (sale_diff['price_diff']<50)]
```


```python
figure(figsize=(15, 10), dpi=200)
plt.scatter(sale_diff['price_diff'], sale_diff['sale_stock'])
plt.title('Scatter plot between %discount and product sales', fontsize=17)
plt.xlabel('% Discount', fontsize=15)
plt.ylabel('Number of product sales', fontsize=15)
_ = plt.xticks(range(0,25,1))

```


    
![png](output_87_0.png)
    


The % of discount in the range of 8-10% affects the sales of the product, causing the product to sell 2-3 times more than usual.

The percentage discount on other range has not effect much on the number of products sold.


```python

```


```python

```


```python

```

