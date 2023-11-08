```python
%sql
CREATE SCHEMA IF NOT EXISTS amazon_reviews;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr></tr></thead><tbody></tbody></table></div>



```python
%sql
DESCRIBE SCHEMA EXTENDED amazon_reviews;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>database_description_item</th><th>database_description_value</th></tr></thead><tbody><tr><td>Catalog Name</td><td>hive_metastore</td></tr><tr><td>Namespace Name</td><td>amazon_reviews</td></tr><tr><td>Comment</td><td></td></tr><tr><td>Location</td><td>dbfs:/user/hive/warehouse/amazon_reviews.db</td></tr><tr><td>Owner</td><td>root</td></tr><tr><td>Properties</td><td></td></tr></tbody></table></div>



```python
%sql
USE amazon_reviews;
CREATE OR REPLACE TEMPORARY VIEW temp_table USING csv
OPTIONS(PATH = 's3://reviews-amazon/Data_source/amazon_reviews.csv',
header = "true",
mode= "PERMISSIVE"
);

CREATE OR REPLACE TABLE reviews AS 
SELECT * FROM temp_table;

SELECT * FROM reviews LIMIT 10;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>id0</th><th>name</th><th>asins</th><th>brand</th><th>categories</th><th>keys</th><th>manufacturer</th><th>date</th><th>dateAdded</th><th>dateSeen</th><th>didPurchase</th><th>doRecommend</th><th>id12</th><th>numHelpful</th><th>rating</th><th>sourceURLs</th><th>text</th><th>title</th><th>userCity</th><th>userProvince</th><th>username</th></tr></thead><tbody><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-13T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=166</td><td>This product so far has not disappointed. My children love to use it and I like the ability to monitor control what content they see with ease.</td><td>Kindle</td><td>null</td><td>null</td><td>Adapter</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-13T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>great for beginner or experienced person. Bought as a gift and she loves it</td><td>very fast</td><td>null</td><td>null</td><td>truman</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-13T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>Inexpensive tablet for him to use and learn on, step up from the NABI. He was thrilled with it, learn how to Skype on it already...</td><td>Beginner tablet for our 9 year old son.</td><td>null</td><td>null</td><td>DaveZ</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-13T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>4</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>I've had my Fire HD 8 two weeks now and I love it. This tablet is a great value.We are Prime Members and that is where this tablet SHINES. I love being able to easily access all of the Prime content as well as movies you can download and watch laterThis has a 1280/800 screen which has some really nice look to it its nice and crisp and very bright infact it is brighter then the ipad pro costing $900 base model. The build on this fire is INSANELY AWESOME running at only 7.7mm thick and the smooth glossy feel on the back it is really amazing to hold its like the futuristic tab in ur hands.</td><td>Good!!!</td><td>null</td><td>null</td><td>Shacks</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-12T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>I bought this for my grand daughter when she comes over to visit. I set it up with her as the user, entered her age and name and now Amazon makes sure that she only accesses sites and content that are appropriate to her age. Simple to do and she loves the capabilities. I also bought and installed a 64gig SD card which gives this little tablet plenty of storage. For the price I think this tablet is best one out there. You can spend hundreds of dollars more for additional speed and capacity but when it comes to the basics this tablets does everything that most people will ever need at a fraction of the cost.</td><td>Fantastic Tablet for kids</td><td>null</td><td>null</td><td>explore42</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-12T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>This amazon fire 8 inch tablet is the perfect size. I purchased it for my husband so that he has a bigger screen than just his phone. He had gotten me one a few years ago so I knew it would be a good purchase.</td><td>Just what we expected</td><td>null</td><td>null</td><td>tklit</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-12T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>4</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>Great for e-reading on the go, nice and light weight, and for the price point given, definitely worth the purchase.</td><td>great e-reader tablet</td><td>null</td><td>null</td><td>Droi</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-12T00:00:00.000Z</td><td>2017-07-03T23:33:15Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:45:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=200,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=167</td><td>I gave this as a Christmas gift to my inlaws, husband and uncle. They loved it and how easy they are to use with fantastic features!</td><td>Great for gifts</td><td>null</td><td>null</td><td>Kacy</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-23T00:00:00.000Z</td><td>2017-07-03T23:28:24Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:44:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=154,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=120</td><td>Great as a device to read books. I like that it links with my borrowed library e-books. Switched from another popular tablet brand and I am happy with the choice I made. It took some time to get books from my previous non-Kindle reader, but finally figured out a way!</td><td>Great for reading</td><td>null</td><td>null</td><td>Weebee</td></tr><tr><td>AVqkIhwDv8e3D1O-lebb</td><td>All-New Fire HD 8 Tablet, 8 HD Display, Wi-Fi, 16 GB - Includes Special Offers, Magenta</td><td>B01AHB9CN2</td><td>Amazon</td><td>Electronics,iPad & Tablets,All Tablets,Fire Tablets,Tablets,Computers & Tablets</td><td>841667104676,amazon/53004484,amazon/b01ahb9cn2,0841667104676,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/5620406,allnewfirehd8tablet8hddisplaywifi16gbincludesspecialoffersmagenta/b01ahb9cn2</td><td>Amazon</td><td>2017-01-23T00:00:00.000Z</td><td>2017-07-03T23:28:24Z</td><td>2017-06-07T09:04:00.000Z,2017-04-30T00:44:00.000Z</td><td>null</td><td>TRUE</td><td>null</td><td>0</td><td>5</td><td>http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=154,http://reviews.bestbuy.com/3545/5620406/reviews.htm?format=embedded&page=121</td><td>I love ordering books and reading them with the reader.</td><td>Great and lightweight reader</td><td>null</td><td>null</td><td>RoboBob</td></tr></tbody></table></div>



```python
%sql
describe detail reviews;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>format</th><th>id</th><th>name</th><th>description</th><th>location</th><th>createdAt</th><th>lastModified</th><th>partitionColumns</th><th>clusteringColumns</th><th>numFiles</th><th>sizeInBytes</th><th>properties</th><th>minReaderVersion</th><th>minWriterVersion</th><th>tableFeatures</th><th>statistics</th></tr></thead><tbody><tr><td>delta</td><td>9961657c-5a68-4f95-8a9f-9f9a32e30f23</td><td>hive_metastore.amazon_reviews.reviews</td><td>null</td><td>dbfs:/user/hive/warehouse/amazon_reviews.db/reviews</td><td>2023-11-08T04:59:42.974Z</td><td>2023-11-08T04:59:57Z</td><td>List()</td><td>List()</td><td>4</td><td>4371123</td><td>Map()</td><td>2</td><td>5</td><td>List(appendOnly, changeDataFeed, checkConstraints, columnMapping, generatedColumns, invariants)</td><td>Map()</td></tr></tbody></table></div>



```python
%sql
DESCRIBE reviews;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>col_name</th><th>data_type</th><th>comment</th></tr></thead><tbody><tr><td>id0</td><td>string</td><td>null</td></tr><tr><td>name</td><td>string</td><td>null</td></tr><tr><td>asins</td><td>string</td><td>null</td></tr><tr><td>brand</td><td>string</td><td>null</td></tr><tr><td>categories</td><td>string</td><td>null</td></tr><tr><td>keys</td><td>string</td><td>null</td></tr><tr><td>manufacturer</td><td>string</td><td>null</td></tr><tr><td>date</td><td>string</td><td>null</td></tr><tr><td>dateAdded</td><td>string</td><td>null</td></tr><tr><td>dateSeen</td><td>string</td><td>null</td></tr><tr><td>didPurchase</td><td>string</td><td>null</td></tr><tr><td>doRecommend</td><td>string</td><td>null</td></tr><tr><td>id12</td><td>string</td><td>null</td></tr><tr><td>numHelpful</td><td>string</td><td>null</td></tr><tr><td>rating</td><td>string</td><td>null</td></tr><tr><td>sourceURLs</td><td>string</td><td>null</td></tr><tr><td>text</td><td>string</td><td>null</td></tr><tr><td>title</td><td>string</td><td>null</td></tr><tr><td>userCity</td><td>string</td><td>null</td></tr><tr><td>userProvince</td><td>string</td><td>null</td></tr><tr><td>username</td><td>string</td><td>null</td></tr></tbody></table></div>



```python
%sql
SELECT count(*),count(id0),
count(name),
count(asins),
count(brand),
count(categories),
count(keys),
count(manufacturer),
count(date),
count(dateAdded),
count(dateSeen),
count(didPurchase),
count(doRecommend),
count(id12),
count(numHelpful),
count(rating),
count(sourceURLs),
count(text),
count(title),
count(userCity),
count(userProvince),
count(username) FROM reviews
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>count(1)</th><th>count(id0)</th><th>count(name)</th><th>count(asins)</th><th>count(brand)</th><th>count(categories)</th><th>count(keys)</th><th>count(manufacturer)</th><th>count(date)</th><th>count(dateAdded)</th><th>count(dateSeen)</th><th>count(didPurchase)</th><th>count(doRecommend)</th><th>count(id12)</th><th>count(numHelpful)</th><th>count(rating)</th><th>count(sourceURLs)</th><th>count(text)</th><th>count(title)</th><th>count(userCity)</th><th>count(userProvince)</th><th>count(username)</th></tr></thead><tbody><tr><td>41421</td><td>41421</td><td>28046</td><td>28029</td><td>34645</td><td>34532</td><td>34532</td><td>34660</td><td>34628</td><td>30751</td><td>34644</td><td>960</td><td>34253</td><td>719</td><td>33795</td><td>28593</td><td>33944</td><td>34441</td><td>33952</td><td>7057</td><td>6941</td><td>28597</td></tr></tbody></table></div>


# Creating Table which represents Gold data


```python
%sql
create table reviews_gold as
select * from reviews;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>num_affected_rows</th><th>num_inserted_rows</th></tr></thead><tbody></tbody></table></div>


# Removing Non Relevant Columns


```python
%sql
ALTER TABLE reviews_gold
DROP column userCity;
```


<style scoped>
  .ansiout {
    display: block;
    unicode-bidi: embed;
    white-space: pre-wrap;
    word-wrap: break-word;
    word-break: break-all;
    font-family: "Menlo", "Monaco", "Consolas", "Ubuntu Mono", "Source Code Pro", monospace;
    font-size: 13px;
    color: #555;
    margin-left: 4px;
    line-height: 19px;
  }
</style>
com.databricks.backend.common.rpc.SparkDriverExceptions$SQLExecutionException: com.databricks.sql.transaction.tahoe.DeltaAnalysisException: DROP COLUMN is not supported for your Delta table. 
Please enable Column Mapping on your Delta table with mapping mode 'name'.
You can use one of the following commands.

If your table is already on the required protocol version:
ALTER TABLE table_name SET TBLPROPERTIES ('delta.columnMapping.mode' = 'name')

If your table is not on the required protocol version and requires a protocol upgrade:
ALTER TABLE table_name SET TBLPROPERTIES (
   'delta.columnMapping.mode' = 'name',
   'delta.minReaderVersion' = '2',
   'delta.minWriterVersion' = '5')
Refer to table versioning at https://docs.databricks.com/delta/versioning.html



```python
%sql
ALTER TABLE reviews_gold SET TBLPROPERTIES (
   'delta.columnMapping.mode' = 'name',
   'delta.minReaderVersion' = '2',
   'delta.minWriterVersion' = '5');
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr></tr></thead><tbody></tbody></table></div>



```python
%sql
ALTER TABLE reviews_gold
DROP COLUMN userCity;

```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr></tr></thead><tbody></tbody></table></div>



```python
%sql
ALTER TABLE reviews_gold
DROP COLUMN userProvince;
ALTER TABLE reviews_gold
DROP COLUMN id12;
ALTER TABLE reviews_gold
DROP COLUMN didPurchase;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr></tr></thead><tbody></tbody></table></div>



```python
%sql
describe reviews_gold
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>col_name</th><th>data_type</th><th>comment</th></tr></thead><tbody><tr><td>id0</td><td>string</td><td>null</td></tr><tr><td>name</td><td>string</td><td>null</td></tr><tr><td>asins</td><td>string</td><td>null</td></tr><tr><td>brand</td><td>string</td><td>null</td></tr><tr><td>categories</td><td>string</td><td>null</td></tr><tr><td>keys</td><td>string</td><td>null</td></tr><tr><td>manufacturer</td><td>string</td><td>null</td></tr><tr><td>date</td><td>string</td><td>null</td></tr><tr><td>dateAdded</td><td>string</td><td>null</td></tr><tr><td>dateSeen</td><td>string</td><td>null</td></tr><tr><td>doRecommend</td><td>string</td><td>null</td></tr><tr><td>numHelpful</td><td>string</td><td>null</td></tr><tr><td>rating</td><td>string</td><td>null</td></tr><tr><td>sourceURLs</td><td>string</td><td>null</td></tr><tr><td>text</td><td>string</td><td>null</td></tr><tr><td>title</td><td>string</td><td>null</td></tr><tr><td>username</td><td>string</td><td>null</td></tr></tbody></table></div>


# Removing Null Values


```python
%sql
delete from reviews_gold where text is null;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>num_affected_rows</th></tr></thead><tbody><tr><td>6980</td></tr></tbody></table></div>



```python
%sql
select count(*) from reviews_gold
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>count(1)</th></tr></thead><tbody><tr><td>34441</td></tr></tbody></table></div>


# Deduplication


```python
%sql
select count(*) from 
(select distinct * from reviews_gold) t;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>count(1)</th></tr></thead><tbody><tr><td>32476</td></tr></tbody></table></div>



```python
%sql
CREATE OR REPLACE TABLE reviews_gold as
SELECT DISTINCT * FROM reviews_gold;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>num_affected_rows</th><th>num_inserted_rows</th></tr></thead><tbody></tbody></table></div>



```python
%sql
SELECT count(*) FROM reviews_gold;
```


<style scoped>
  .table-result-container {
    max-height: 300px;
    overflow: auto;
  }
  table, th, td {
    border: 1px solid black;
    border-collapse: collapse;
  }
  th, td {
    padding: 5px;
  }
  th {
    text-align: left;
  }
</style><div class='table-result-container'><table class='table-result'><thead style='background-color: white'><tr><th>count(1)</th></tr></thead><tbody><tr><td>32476</td></tr></tbody></table></div>



```python

```
