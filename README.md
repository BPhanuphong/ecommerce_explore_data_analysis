# E-commerce-Mini-Project

### ผู้จัดทำ
#### - 6510400004 Unyawee Phanburananont         
#### - 6510400003 Phanuphong Siriphongwatana 

### ข้อมูล
ชุดข้อมูลเป็น Transaction ของข้อมูลสินค้าบนแพลตฟอร์ม E-commerce ที่เก็บเป็นรายชั่วโมง มีข้อมูลเกี่ยวกับ %ส่วนลด, ราคาสินค้า, ยี่ห้อสินค้า, การทำแฟลชเซล(Flash sale), จำนวนสินค้าในคลังสินค้า(Stock) เป็นต้น

ระยะเวลาของข้อมูล: 2022-09 ถึง 2023-03


### คำถาม

สำรวจเกี่ยวกับการทำแฟลชเซลของสินค้า  แคมเปญการขาย สินค้าแต่ละเเบรนด์ และการลดราคากับสต็อกสินค้า

1. วันและเวลา 10 อันดับแรกที่มีการทำแฟลชเซลบ่อยที่สุด
2. เปรียบเทียบ 3 แคมเปญลดราคาสินค้า ว่าแคมเปญไหนมีการทำแฟลชเซลบ่อยที่สุด
3. PayDay แคมเปญมีระยะเวลาที่จัดแคมเปญหลายวันกว่าแคมเปญอื่นๆ จึงดูเพิ่มว่า ช่วงวันและเวลาไหนที่นิยมทำแฟลชเซล
4. แต่ละแคมเปญส่วนมากทำแฟลชเซลกี่ชั่วโมงโดยเฉลี่ย
5. แต่ละแคมเปญมีพฤติกรรมการทำแฟลชเซลช่วงเวลาไหนเท่าไหร่บ้าง
6. สำรวจแบรนด์สินค้าที่เป็นร้านค้าทางการเทียบกับร้านค้าไม่ทางการว่ามีพฤติกรรมการลดราคาในแต่ละแคมเปญแตกต่างกันหรือไม่
7. ความสัมพันธ์ของการลดราคากับจำนวนสินค้าที่ขายได้


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



## 3 Type campaign

campaign คือมหกรรมการลดราคาของ platform ที่การให้โค้ดส่วนลดมากมายและการทำ flash sale ของร้านค้า

Shopee มีทั้งหมด 3 แคมเปญหลักๆ ดังนี้

### 1. Mega Sale
วันที่ วันกับเดือนตรงกัน เช่น 11.11 , 12.12 เป็นต้น

<img src="https://user-images.githubusercontent.com/113247700/226548955-c9736eb0-eae5-408c-8a22-8b540f50970a.jpg" alt= “” width="500" height="300">

### 2. Mid Month Sale
แคมเปญทุกกลางเดือน จัดทุกวันที่ 15 ของเดือน

<img src="https://user-images.githubusercontent.com/113247700/226549185-6bc123d0-835f-451d-aafe-55e5e67b15b2.jpg" alt= “” width="500" height="300">

### 3. Pay Day Sale
แคมเปญปลายเดือน ส่วนมากจะจัดหลายวันตั้งแต่วันที่ 25-สิ้นเดือน

<img src="https://user-images.githubusercontent.com/113247700/226549360-91daf89c-dabf-4266-8a37-e995791f5dd0.jpg" alt= “” width="500" height="350">

ทุกเดือนจะทำทั้ง 3 campaign แตกต่างกันที่วันที่ และจะมีร้านค้าการทำ flash sale ร่วมด้วย (Flash sale ไม่จำเป็นต้องทำภายใน 3 campaign นี้แต่สามารถทำได้ตลอดเวลาและทุกๆวัน)

# Understand and prepare Data Part

itemid = id ของสินค้าใน 1 url สินค้า

modelid = id ของตัวเลือกสินค้าใน itemid

itemid มีได้หลาย modelid เพราะ 1 สินค้าสามารถมีได้หลายตัวเลือกสินค้า 


```python
df[['itemid','modelid']]
```




<div>
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



จากคำถามเราต้องการวิเคราะห์เกี่ยวกับการทำแฟลชเซลสินค้า เนื่องจาก API ของ Shopee มีการ return ค่าของแฟลชเซลออกมาตาม itemid ทำให้ ทุก modelid จะถูกเหมาะรวมว่าทำแฟลชเซลถึงแม้ modelid นั้นจะไม่ได้มีการทำแฟลชเซลก็ตาม 
ดังนั้นเราจึงทำการเลือกเฉพาะข้อมูล itemid ที่มีเฉพาะ modelid เดียวมาทำการวิเคราะห์ต่อเท่านั้น


```python
list(df.sort_values(['brand'])['brand'].unique())
```




    ['Amazfit (อเมซฟิต)',
     'Baseus(เบซิอัส)',
     'Ecovacs(อีโคแวคส์)',
     'Haier(ไฮเออร์)',
     'Life Space (ไลฟ์สเปซ)',
     'Mister Robot(มิสเตอร์โรบอต)',
     'Pando(แพนโด้)',
     'Papifeed(ปาปิฟีด)',
     'Petkit(เพ็ทคิต)',
     'Petkit(เพ็ทคิท)',
     'Redmi(เรดมี่)',
     'Roborock(โรโบร็อค)',
     'Xiaomi(เสี่ยวมี่)',
     'iRobot(ไอโรบอท)',
     nan]




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

def extract_year(row):
    date = datetime.strptime(row, '%Y-%m-%d %H:%M:%S')
    return date.strftime('%Y')

def extract_mega_sale(row):
    date = datetime.strptime(row, '%Y-%m-%d %H:%M:%S')
    if date.strftime('%m') == date.strftime('%d'):
        return True
    else:
        return False
```


```python
df['year'] = df['ingest_date'].apply(extract_year)
df['day_hour'] = df['ingest_date'].apply(extract_date_hour)
df['mega_sale'] = df['ingest_date'].apply(extract_mega_sale)
```

ตรวจจสอบพฤติกรรมของข้อมูลในแต่ละปี เพื่อดูคุณภาพของข้อมูลก่อนการทำไปวิเคราะห์


```python
df['year'].unique()
```




    array(['2022', '2023'], dtype=object)




```python
print(len(df[df['year']=='2022']))
df[df['year']=='2022'][['itemid','modelid','ingest_date','day_hour']].sort_values(by=['itemid','ingest_date'])[:10]
```

    30679
    





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



จากการดูแยกปี 2022 กับ 2023 จะพบว่า 2022 มี transaction ทุกๆ1 ชั่วโมง ส่วน 2023 จะเป็น transaction ทุกๆ3ชั่วโมง
ทำให้ข้อมูลปี 2023 อาจจะข้ามช่วงเวลาการทำแฟลชเซลไปอาจจะทำให้ข้อมูลคลาดเคลื่อนกันของทั้ง2ปี
เราจึงเลือกที่จะตัดข้อมูลของปี 2023 ออกเนื่องจากเราต้องการนำแฟลชเซลมาวิเคราะห์ถึงระยะเวลาและจำนวน trnsasction ที่เกิดขึ้น


```python
fig = plt.figure(figsize = (15, 7))
freq = plt.bar(['All data','After removing 2023'], [len(df),len(df[df['year']!='2023'])], color =['c','green'])

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height/2),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom', fontsize=15,color='white', weight='bold')
    
fig.suptitle('Number of data Before and After remove 2023', fontsize=15)
plt.ylabel('Count row of data', fontsize=15)
```





![output_18_1](https://user-images.githubusercontent.com/113247700/226550878-4a295ca1-ed88-463b-a81d-418583a7384f.png)


    



```python
df = df[df['year']!='2023']
```

## 1.Top 10 flash sale frequency by day_hour
วันและเวลา 10 อันดับแรกใดที่มีการทำแฟลชเซลบ่อยที่สุด

#### Filter only transaction that have flash sale
เตรียมข้อมูลเพื่อวิเคราะห์สินค้าที่ทำแฟลชเซล โดยสินค้าที่มีการทำแฟลชเซล ดูจากคอลัมน์ Flash_sale ที่ค่าไม่ใช่ค่าว่าง


```python
df['flash_sale'].unique()[:10]
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
           "{'price_before_discount': 2141900000, 'hidden_price_display': None, 'end_time': 1662663600, 'flash_sale_stock': 10, 'promotionid': 674491900713811, 'lowest_past_price': None, 'promo_images': None, 'start_time': 1662656400, 'promo_overlay_image': None, 'extra_discount_info': None, 'flash_sale_type': 2, 'price': 1190000000, 'stock': 9}"],
          dtype=object)



เราจะเลือกเฉพาะ Transaction ที่มีการทำแฟลชเซล


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
most_flash_sale = fs_groupby_DH.groupby(['day_hour'])[['count_dh']].sum().reset_index()
```


```python
most_flash_sale = most_flash_sale.sort_values(by=['count_dh'],ascending=False).reset_index()
most_flash_sale
```




<div>
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




```python
fig = plt.figure(figsize = (15, 6))
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



![output_30_1](https://user-images.githubusercontent.com/113247700/226550835-19494da9-f8eb-45bc-a0d3-f535fe84998a.png)


    


วันและเวลาที่มีการทำแฟลชเซลบ่อยที่สุดโดยนับจาก Transaction ของสินค้าที่มีการทำแฟลชเซล คือวันที่ 25 เที่ยงคืนกับ 15 เที่ยงคืน (เนื่องจาก 25 เป็นวันที่จัด PayDay campaign และ 15 เป็นวันที่จัด Mid month campaign)

##  2. Compare 3 sales campaigns

เปรียบเทียบ 3 แคมเปญลดราคาสินค้า หาว่าแคมเปญไหนมีการทำแฟลชเซลบ่อยที่สุด


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
fig = plt.figure(figsize = (15, 6))
freq = plt.bar(['Mega campaign','Mid Month campaign','PayDay campaign'], [mega_sale_fr,mid_month_sale_fr,pay_day_sale_fr], color ='c',
        width = 0.4)
all_freq = 0   #mega_sale_fr+mid_month_sale_fr+pay_day_sale_fr
for i in freq:
    height = i.get_height()
#     print(height)
    all_freq+= height
    
# print(all_freq)
for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.0f}',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
    plt.annotate(f'{((height)/all_freq*100):.0f}%',
                xy=(f.get_x() + f.get_width() / 2, height/2),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
fig.suptitle('Frequency transaction product of each sales campaign', fontsize=17)
plt.xlabel('Sales campaigns', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```





![output_38_1](https://user-images.githubusercontent.com/113247700/226550753-d90c8605-0057-45dc-bca2-30398894b6d4.png)

    

    


ภาพรวมของแต่ละแคมเปญที่มีการทำแฟลชเซล Payday แคมเปญมีการทำแฟลชเซลเยอะที่สุดเนื่องจากมีการจัดแคมเปญหลายวัน รองลงมาคือ Mega sale แคมเปญ

## 3. Details of Payday campaign (Payday campaign has several campaign periods.)
PayDay แคมเปญมีระยะเวลาที่จัดแคมเปญหลายวันกว่าแคมเปญอื่นๆ จึงดูเพิ่มว่าช่วงวันและเวลาไหนที่นิยมทำแฟลชเซล

### 3.1 Frequency by hour


```python
pay_day_sale = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').groupby(['hour'])[['hour']].count().rename(columns={'hour':'count'}).reset_index()
pay_day_sale = pay_day_sale.sort_values(by=['count'],ascending=False).reset_index()
pay_day_sale

fig = plt.figure(figsize = (15, 6))
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
plt.xlabel('Hour', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```




![output_42_1](https://user-images.githubusercontent.com/113247700/226550714-e670d7cf-2b41-4fde-a59e-ef6b31ec814a.png)

    

    


### 3.2 Frequency by day


```python
pay_day_sale = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').groupby(['day'])[['day']].count().rename(columns={'day':'count'}).reset_index()
pay_day_sale = pay_day_sale.sort_values(by=['count'],ascending=False).reset_index()
pay_day_sale

fig = plt.figure(figsize = (15, 6))
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
plt.xlabel('Day', fontsize=15)
plt.ylabel('Count transaction of flash sale', fontsize=15)
```





![output_44_1](https://user-images.githubusercontent.com/113247700/226550680-cb6bc66c-0ace-4ceb-9720-ef8e86fca238.png)


    


###  3.3 Frequency by day and hour


```python
pay_day_sale = df[(df['day']>=25)&(df['flash_sale'].notna())].drop_duplicates(subset=['flash_sale'],keep='first').groupby(['day','hour'])[['hour']].count().rename(columns={'hour':'count'}).reset_index()
pay_day_sale['day_hour'] = pay_day_sale['day'].astype(str) +'-' +pay_day_sale['hour'].astype(str)
pay_day_sale = pay_day_sale.sort_values(by=['count'],ascending=False).reset_index()

fig = plt.figure(figsize = (15, 6))
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





![output_46_1](https://user-images.githubusercontent.com/113247700/226550655-3b744d36-d635-48d0-9dee-a5af414f928f.png)

    


แคมเปญการขาย PayDay

3.1 ชั่วโมงที่นิยมทำแฟลชเซลคือ 12:00 น. 00:00 น. 18:00 น. และ 15:00 น. ตามลำดับ พฤติกรรมการขายส่วนใหญ่จะห่างกันทุกสามชั่วโมง

3.2 วันที่ขายแฟลชสูงสุดในช่วง Payday คือวันที่ 25 (วันแรกของแคมเปญการขาย PayDay), 30, 27 ตามลำดับ

3.3 วันและชั่วโมงการขายแฟลชสูงสุดในช่วง Payday คือ 25-00:00 น., 30-12:00 น., 25-12:00 น., 27-12:00 น. ตามลำดับ

# 4. Flash sale duration time 

แต่ละแคมเปญส่วนมากทำแฟลชเซลกี่ชั่วโมงโดยเฉลี่ย


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
fig = plt.figure(figsize = (15, 6))
freq = plt.bar(['Mega campaign','Mid month campaign','PayDay campaign'],
        [mega_sale_df['duration'].mean(),mid_month_sale_df['duration'].mean(),pay_day_sale_df['duration'].mean()], 
        color ='c',
        width = 0.4)

for f in freq:
    height = f.get_height()
    plt.annotate(f'{height:.2f} Hour',
                xy=(f.get_x() + f.get_width() / 2, height),
                xytext=(0, 3),
                textcoords="offset points",
                ha='center', va='bottom')
    
fig.suptitle('Duration times of Flash sale by sales campaign', fontsize=17)
plt.xlabel('Sales Campaigns', fontsize=15)
plt.ylabel('Duration time (Hours)', fontsize=15)
```






![output_53_1](https://user-images.githubusercontent.com/113247700/226550631-fb8518c5-2357-414f-9709-55ed8e38b9da.png)

    

    


PayDay มีการทำแฟลชเซลระยะเวลานานที่สุดคือประมาณ 8 ชั่วโมงต่อการทำแฟลชเซล1ครั้ง
รองลงมาด้วย Mid month แคมเปญ คือ4 ชั่วโมงและ Mega 3ชั่วโมง

จากการสำรวจข้อมูลพบว่า Mega sale จะแฟลชเซลในระยะสั้นกว่าและมีจำนวนการแฟลชเซลบ่อยกว่า Mid month sale

## 5. Pattern of the flash sale hour of each campaign.
แต่ละแคมเปญมีพฤติกรรมการทำแฟลชเซลช่วงเวลาไหนเท่าไหร่บ้าง


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









 
![output_58_1](https://user-images.githubusercontent.com/113247700/226550606-3de5425c-5dcb-4331-a87a-02bab47a046f.png)


ภาพรวมของการขายแฟลชเป็นที่นิยมในช่วงเวลา 02:00 น. (อาจเริ่มขายแฟลชเซลตั้งแต่เที่ยงคืนหรือ 01.00 น.) รองลงมาคือ 9.00 น., 12.00 น., 14.00 น., 16.00 น., 18.00 น. ตามลำดับ 

ตามแคมเปญ Mega Campaign และ Mid month Campaign จะมี flash sale ในแต่ละช่วงใกล้เคียงกันและเน้นทำแฟลชเซลช่วงกลางคืน. 
สำหรับแคมเปญ Payday จะมีรูปแบบที่แตกต่างไปคือจะมีการขายแฟลชมากที่สุดในตอนกลางวัน ที่เวลา 12:00 น. และอีกครั้งเวลา 18:00 น.

# 6. Explore by Brand 
สำรวจแบรนด์สินค้าที่เป็น Official เทียบกับแบรนด์ Unofficial ว่ามีพฤติกรรมการลดราคาในแต่ละแคมเปญแตกต่างกันหรือไม่


Explore the discounting behavior of brands selling on the platform.


```python
brand = [i for i in df['brand'].dropna().unique().tolist()]

brand_count = [len(df[df['brand']==i]['shopid'].unique()) for i in brand]
brand_count
```




    [9, 4, 3, 1, 1, 3, 2, 1]




```python
df_brand = pd.DataFrame()
df_brand['brand'] = brand
df_brand['countd_shopid'] = [len(df[df['brand']==i]['shopid'].unique()) for i in brand]
df_brand['count_shopid']  = [len(df[df['brand']==i]['shopid']) for i in brand]
df_brand
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>brand</th>
      <th>countd_shopid</th>
      <th>count_shopid</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Petkit(เพ็ทคิท)</td>
      <td>9</td>
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
      <td>3</td>
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
      <td>1</td>
      <td>2234</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Haier(ไฮเออร์)</td>
      <td>3</td>
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


    
![output_63_0](https://user-images.githubusercontent.com/113247700/226550429-6ac3ffb8-9909-4811-ba87-96a9bf628cfb.png)



แบรนด์ Petkit มีจำนวนร้านค้ามากที่สุด (มีการแข่งขันที่สูง) รองลงมาคือ Amazfit 

###  Compare between official shop and unofficial shop


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

figure(figsize=(15, 6), dpi=200)

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

![output_71_0](https://user-images.githubusercontent.com/113247700/226550260-57d633ab-7f58-402a-a71b-ffea258d41b4.png)

    


ในข้อมูลที่เรามีจะมีแบรนด์ Petkit ที่มีจำนวน official Mall และ Unofficial Mallที่พอๆกัน นอกจากนั้นจำนวนร้านส่วนใหญ่ในแต่ละแบรนด์จะเป็น official mall ส่วนใหญ่

## Campaign styles for each brand

#### Official Brand


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



#### Unofficial brand


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
# figure(figsize=(20, 10), dpi=200)

fig, (a1, a2) = plt.subplots(1, 2,sharey=True,figsize=(20, 15), dpi=200,gridspec_kw={'width_ratios': [3, 0.5]})
a2.yaxis.set_tick_params(which='both', labelbottom=True)

label = [i.split('(')[0] for i in count_overall_sale_mall['brand']]
ax1 = a1.bar(label, count_overall_sale_mall['count_mega_sale'], color='lightsalmon', label='Mega sale campaign')
ax2 = a1.bar(label, count_overall_sale_mall['count_mid_month'], bottom=count_overall_sale_mall['count_mega_sale'], color='lightblue', label='Mid Month sale campaign')
ax3 = a1.bar(label, count_overall_sale_mall['count_pay_day'], bottom=count_overall_sale_mall['count_mega_sale']+count_overall_sale_mall['count_mid_month'], color='pink',label='PayDay sale campaign')
a1.set_title('Number of Items in Official Mall Brand', size=20)
a1.set_xlabel('Brand', size=20)
a1.set_ylabel('Number of items', size=20)

for r1, r2, r3 in zip(ax1, ax2, ax3):
    h1 = r1.get_height()
    h2 = r2.get_height()
    h3 = r3.get_height()

    a1.text(r1.get_x() + r1.get_width() / 2., h1 / 2., "{0:.2f}%".format((h1/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    a1.text(r2.get_x() + r2.get_width() / 2., h1 + h2 / 2., "{0:.2f}%".format((h2/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    a1.text(r3.get_x() + r2.get_width() / 2., h1 + h2 + h3 / 2., "{0:.2f}%".format((h3/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)

a1.legend(prop={'size': 15})

# a = plt.show()


label = [i.split('(')[0] for i in count_overall_sale_not_mall['brand']]
ax1 = a2.bar(label, count_overall_sale_not_mall['count_mega_sale'], color='lightsalmon', label = 'Mega sale campaign')
ax2 = a2.bar(label, count_overall_sale_not_mall['count_mid_month'], bottom=count_overall_sale_not_mall['count_mega_sale'], color='lightblue', label = 'Mid month sale campaign')
ax3 = a2.bar(label, count_overall_sale_not_mall['count_pay_day'], bottom=count_overall_sale_not_mall['count_mega_sale']+count_overall_sale_not_mall['count_mid_month'], color='pink', label = 'PayDay sale campaign')
a2.set_title('Number of Items in Unofficial/Not mall Brand', size=20)
a2.set_xlabel('Brand', size=20)
a2.set_ylabel('Number of items', size=20)

for r1, r2, r3 in zip(ax1, ax2, ax3):
    h1 = r1.get_height()
    h2 = r2.get_height()
    h3 = r3.get_height()

    a2.text(r1.get_x() + r1.get_width() / 2., h1 / 2., "{0:.2f}%".format((h1/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    a2.text(r2.get_x() + r2.get_width() / 2., h1 + h2 / 2., "{0:.2f}%".format((h2/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)
    a2.text(r3.get_x() + r2.get_width() / 2., h1 + h2 + h3 / 2., "{0:.2f}%".format((h3/(h1+h2+h3))*100), ha="center", va="center", color="black", fontsize=14)

a2.legend(prop={'size': 15})

a1.tick_params(axis='both', labelsize=15)
a2.tick_params(axis='both', labelsize=15)
# plt.setp(a2.get_yticklabels(), visible=True)

# a = plt.show()
```



![output_79_0](https://user-images.githubusercontent.com/113247700/226550121-09fdd931-5df7-4bb5-b834-78119d63b142.png)


การเข้าร่วม campaign ทั้ง 3 สามารถบอกได้ดังนี้
- Payday ที่การทำ Flash sale สูงที่สุดเนื่องจากมีจำนวนวันในการทำและมีระยะเวลาในการทำสูงที่สุด (ข้อ 4)
- แบรนด์ที่การเข้าร่วม campaign คือ Petkit รองลงมาคือ Amazfit และ Xiaomi
- ร้านค้าที่ไม่เป็น official mall จะมีการเข้าร่วมเพียงหนึ่งแบรนด์ คือ Petkit และ ทำ flash sale ใน pay day เยอะที่สุด

ร้านค้าส่วนใหญ่ที่เข้าร่วมทั้ง 3 campaign จะเป็น official mall และ pay day จะมีการทำ flash sale สูงที่สุด

# 7. Relationship between discount and sales
ความสัมพันธ์ของการลดราคากับจำนวนสินค้าที่ขายได้


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








    

![png](https://user-images.githubusercontent.com/113247700/226549977-65648eb0-ef95-42a3-8a7f-28207953facb.png)




ตัด outliner ที่เป็นข้อมูลที่ไม่มีความสำคัญออก เพื่อให้สามารถขยายกราฟให้ใหญ่มากขึ้นได้


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


    
![output_92_0](https://user-images.githubusercontent.com/113247700/226547290-f87433f2-9483-4988-a764-8812e3c6434d.png)
    


ส่วนลดในช่วง 8-10% มีผลต่อยอดขายสินค้า ทำให้สินค้าขายได้มากกว่าปกติ 2-3 เท่า
ส่วนลดเป็นเปอร์เซ็นต์ในช่วงอื่นไม่ได้มีผลกับจำนวนสินค้าที่ขายมากนัก

# Summary

1. วันที่ทำ Flash Sale บ่อยที่สุด 25 เที่ยงคืน 15 เที่ยงคืน
2. แคมเปญที่ทำแฟลชเซลบ่อยที่สุดคือ PayDay
3. วันและเวลาที่ทำแฟลชเซลบ่อยของ PayDay - 25-00, 30-12, 25-12, 27-12
4. Mega sale จะทำแฟลชเซลบ่อยกว่า Midmonth Sale แต่จำนวนชั่วโมงในการแฟลชเซลน้อยกว่า Midmonth 
5. PayDay นิยมทำแฟลชเซลในช่วงเวลากลางวัน 12, 18 ส่วน Mega, Midmonth ทำแฟลชเซลคล้ายๆกัน นิยมทำในช่วงเวลากลางคืน 00:00-02:00
6. Official Brand ส่วนมากจะนิยมทำแฟลชเซลในแคมเปญ Mega sale และ PayDay มากกว่า Midmonth
7. ส่วนลด 8-10% มีผลกับยอดขายมากที่สุด
