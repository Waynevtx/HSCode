## Introduction to Reference Data in Vortexa Python SDK

When working with Vortexa’s Python SDK, one of the foundational components you'll encounter is reference data. But what exactly is reference data, and why is it crucial for your analytics and data manipulation tasks?

### What is Reference Data?

Reference data, also known as master data, encompasses the core datasets that define and categorize the entities within Vortexa’s ecosystem. These datasets are used to standardize and provide context to the event data you’ll be working with. In essence, reference data acts as the backbone for ensuring consistency, accuracy, and reliability in your data operations.

### Three main Reference Data in Vortexa
**1. Geographies**: Detailed information about various locations, such as ports, terminals, and regions. This allows you to accurately track and analyze movements and activities related to these locations.

**2. Vessels**: Comprehensive data about vessels, including their names, types, sizes, and other attributes. This is essential for tracking vessel movements, understanding fleet compositions, and analyzing shipping trends.

**3. Products**: Information about different types of products, their classifications, and hierarchies. This helps in analyzing trade flows, market dynamics, and commodity-specific trends.

## Import Libraries


```python
import vortexasdk as v
import pandas as pd
```

To start with, let's explore what you could extract from Geographies endpoint.


```python
# To load all geographies
all_geographies = v.Geographies().load_all().to_df()

# To load all geographies with a specific type (e.g. country)
country_list = v.Geographies().search(filter_layer=['country']).to_df()

# To load all geographies with a name containing 'China'
china_list = v.Geographies().search(term='China').to_df()
```

    2024-07-23 13:31:07,189 vortexasdk.client — WARNING — You are using vortexasdk version 0.72.5, however version 0.72.6 is available.
    You should consider upgrading via the 'pip install vortexasdk --upgrade' command.
    


```python
all_geographies.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>layer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0eb7b43e3d4e62db74e187bc4eadadfb878a210201e14a...</td>
      <td>21st Century Shipbuilding</td>
      <td>[terminal]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>b27430b57d617a855d44f91fb70441bae69c19a3c0deb4...</td>
      <td>2x1 Holding Cape Midia Shipyard</td>
      <td>[terminal]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>d38a8f7bf8ed422b439ad5270be65b60b964bed9568936...</td>
      <td>A Pobra Do Caraminal [ES]</td>
      <td>[port]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3ebcf6f2e43e3a8b06e9b0ae31df3d87f3fbc8d032b72d...</td>
      <td>A and P Group Falmouth Shipyard</td>
      <td>[terminal]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0c8a30f40639257e5352e2c6ac52af2f93b2c6bfed7187...</td>
      <td>A and P Group Tees Shipyard</td>
      <td>[terminal]</td>
    </tr>
  </tbody>
</table>
</div>




```python
country_list.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>layer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1cd3c07221f9e9b3296c859d0bcd3da17ac6072bfdcc84...</td>
      <td>Afghanistan</td>
      <td>[country]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5e4e7b5040b933b5a0f0d2357ed27ebec432c749b9d63a...</td>
      <td>Albania</td>
      <td>[country]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>87269b28eaea324d2c35e97b0ecc837ebc9a244faf94e2...</td>
      <td>Algeria</td>
      <td>[country]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>f4435d4fffa5b2ba7a340e3a8e7d421f619d9f7832fa0c...</td>
      <td>American Samoa</td>
      <td>[country]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>db3cb74043b8fd438087a3e0e04e3e498b78c3c9790fce...</td>
      <td>Andorra</td>
      <td>[country]</td>
    </tr>
  </tbody>
</table>
</div>




```python
china_list.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>layer</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>934c47f36c16a58d68ef5e007e62a23f5f036ee3f3d1f5...</td>
      <td>China</td>
      <td>[country]</td>
    </tr>
    <tr>
      <th>1</th>
      <td>781cacc7033f877caa4b4106d096b74afe006a96391bf5...</td>
      <td>South China</td>
      <td>[alternative_region]</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a63890260e29d859390fd1a23c690181afd4bd152943a0...</td>
      <td>North China</td>
      <td>[alternative_region]</td>
    </tr>
    <tr>
      <th>3</th>
      <td>d1d5a3d3666d6ebb65a1b53e626b07f6b8540e8048a524...</td>
      <td>Shipyard Nansha China</td>
      <td>[terminal]</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ae0f224030f7337d0ffe5a54d290a9f0bd029f636eaf12...</td>
      <td>China Yangfan Group</td>
      <td>[terminal]</td>
    </tr>
  </tbody>
</table>
</div>



This shows how you could extract the ids, which may be required from other endpoints. In addition, to extract more information about the locations such as centroids, hierarchies etc, we can do .to_df(columns = 'all) method.


```python
china_list_enhanced = v.Geographies().search(term='China').to_df(columns = 'all')
china_list_enhanced.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>layer</th>
      <th>leaf</th>
      <th>parent</th>
      <th>exclusion_rule</th>
      <th>ref_type</th>
      <th>hierarchy</th>
      <th>pos</th>
      <th>aliases</th>
      <th>tags</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>934c47f36c16a58d68ef5e007e62a23f5f036ee3f3d1f5...</td>
      <td>China</td>
      <td>[country]</td>
      <td>False</td>
      <td>[{'name': 'Far East', 'layer': ['alternative_r...</td>
      <td>[{'name': 'China', 'layer': ['country'], 'id':...</td>
      <td>geography</td>
      <td>[{'label': 'China', 'layer': 'country', 'id': ...</td>
      <td>[105.4525116754, 35.4496039032]</td>
      <td>[]</td>
      <td>{'importProductTags': [], 'exportProductTags':...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>781cacc7033f877caa4b4106d096b74afe006a96391bf5...</td>
      <td>South China</td>
      <td>[alternative_region]</td>
      <td>False</td>
      <td>[{'name': 'China (excl. HK &amp; Macau)', 'layer':...</td>
      <td>[{'name': 'South China', 'layer': ['alternativ...</td>
      <td>geography</td>
      <td>[{'id': 'b5fafce6e20de2dc307fb7e0b89978ee91a49...</td>
      <td>[106.3418341843, 28.1283930445]</td>
      <td>[]</td>
      <td>{'importProductTags': [], 'exportProductTags':...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>a63890260e29d859390fd1a23c690181afd4bd152943a0...</td>
      <td>North China</td>
      <td>[alternative_region]</td>
      <td>False</td>
      <td>[{'name': 'China (excl. HK &amp; Macau)', 'layer':...</td>
      <td>[{'name': 'North China', 'layer': ['alternativ...</td>
      <td>geography</td>
      <td>[{'id': 'b5fafce6e20de2dc307fb7e0b89978ee91a49...</td>
      <td>[104.7737174548, 40.9901656588]</td>
      <td>[]</td>
      <td>{'importProductTags': [], 'exportProductTags':...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>d1d5a3d3666d6ebb65a1b53e626b07f6b8540e8048a524...</td>
      <td>Shipyard Nansha China</td>
      <td>[terminal]</td>
      <td>True</td>
      <td>[{'name': 'Nansha [CN]', 'layer': ['port', 'st...</td>
      <td>[{'name': 'Shipyard Nansha China', 'layer': ['...</td>
      <td>geography</td>
      <td>[{'label': 'Shipyard Nansha China', 'layer': '...</td>
      <td>[113.5214914215, 22.7496639804]</td>
      <td>[]</td>
      <td>{'importProductTags': [], 'exportProductTags':...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ae0f224030f7337d0ffe5a54d290a9f0bd029f636eaf12...</td>
      <td>China Yangfan Group</td>
      <td>[terminal]</td>
      <td>True</td>
      <td>[{'name': 'Zhoushan [CN]', 'layer': ['port', '...</td>
      <td>[{'name': 'China Yangfan Group', 'layer': ['te...</td>
      <td>geography</td>
      <td>[{'label': 'China Yangfan Group', 'layer': 'te...</td>
      <td>[122.2921859199, 29.9282176371]</td>
      <td>[]</td>
      <td>{'importProductTags': [], 'exportProductTags':...</td>
    </tr>
  </tbody>
</table>
</div>



Now we have demonstrated how to extract reference data via Geographies. Similarly, the methodology works for Products & Vessels endpoint as well.


```python
# To load all products
products = v.Products().load_all().to_df()
products.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>layer.0</th>
      <th>parent.0.name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>887940a6cf2d527a20d82a5f163ecce502878ceb1cd59f...</td>
      <td>0.005 / 50ppm</td>
      <td>grade</td>
      <td>Gasoil</td>
    </tr>
    <tr>
      <th>1</th>
      <td>8bb096fb847f92af86235002b2a78ca0437543722cdb8c...</td>
      <td>0.05 / 500ppm</td>
      <td>grade</td>
      <td>Gasoil</td>
    </tr>
    <tr>
      <th>2</th>
      <td>35f8222ff81fe5befafee9c64c1d76618e4cc53e74021a...</td>
      <td>0.1 / 1000ppm</td>
      <td>grade</td>
      <td>Gasoil</td>
    </tr>
    <tr>
      <th>3</th>
      <td>881be476857ff08dcf6a8708a2fc279d26770cecf245f7...</td>
      <td>0.1+ / 1000ppm Plus (HS)</td>
      <td>grade</td>
      <td>Gasoil</td>
    </tr>
    <tr>
      <th>4</th>
      <td>a6ef13d2f3145a1b67a81300c1cfa4f21874f24fab4f8f...</td>
      <td>180 CST</td>
      <td>grade</td>
      <td>High Sulphur Fuel Oil</td>
    </tr>
  </tbody>
</table>
</div>




```python
# To load Gasoil only
gasoil = v.Products().search(term='Gasoil').to_df()
gasoil.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>layer.0</th>
      <th>parent.0.name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>b2034f1ad3a4ac269e962f00b9914d6b909923cf904d99...</td>
      <td>Gasoil</td>
      <td>category</td>
      <td>Diesel/Gasoil</td>
    </tr>
    <tr>
      <th>1</th>
      <td>deda35eb9ca56b54e74f0ff370423f9a8c61cf6a3796fc...</td>
      <td>Diesel/Gasoil</td>
      <td>group_product</td>
      <td>Clean Petroleum Products</td>
    </tr>
    <tr>
      <th>2</th>
      <td>e06296595e1d554008a70172440d5582c923bdb8182af5...</td>
      <td>Coker Gasoil</td>
      <td>grade</td>
      <td>Dirty Feedstocks</td>
    </tr>
    <tr>
      <th>3</th>
      <td>feb8190865392ab6caecd7709077a58645ec4828c23d94...</td>
      <td>Marine Gasoil</td>
      <td>grade</td>
      <td>Gasoil</td>
    </tr>
  </tbody>
</table>
</div>




```python
# To load all vessels
vessels = v.Vessels().load_all().to_df()
vessels.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>imo</th>
      <th>vessel_class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>62f3f3c1f5a663d621fe6cf9537c7d936b547497932f5d...</td>
      <td>\tATHINEA</td>
      <td>9291248.0</td>
      <td>oil_lr2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>e6b259c04da30a57db353665e7e61f67a0a3222b96c457...</td>
      <td>\tBORA</td>
      <td>9276004.0</td>
      <td>oil_mr2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>f351708121bce4d357ac5fad967cb1bf7fe5072773f05a...</td>
      <td>0051-04</td>
      <td></td>
      <td>oil_coastal</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1761da4fb069cd6ce153b6ad1c48e15cdb994eb386e4aa...</td>
      <td>058</td>
      <td></td>
      <td>oil_coastal</td>
    </tr>
    <tr>
      <th>4</th>
      <td>c817b5994efe14621949533d6777b22ce11db1c6bf9e48...</td>
      <td>1011</td>
      <td></td>
      <td>oil_coastal</td>
    </tr>
  </tbody>
</table>
</div>




```python
# To load all vessels with a name containing 'Maersk' (currently named or previously named)
maersk_vessels = v.Vessels().search(term='Maersk').to_df()
maersk_vessels.head(5)
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
      <th>id</th>
      <th>name</th>
      <th>imo</th>
      <th>vessel_class</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>00d89be99f08890c9122c326aa32c83ae6d557629bc124...</td>
      <td>VS REMLIN</td>
      <td>9252307</td>
      <td>oil_mr1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>03c191caf28a554c8c1adfc11ff2a7a08ad5fa21a83892...</td>
      <td>SOUTH LOYALTY</td>
      <td>9537769</td>
      <td>oil_vlcc</td>
    </tr>
    <tr>
      <th>2</th>
      <td>07e562b509f2617c18f9e848c51bdec8e97488c4a41bbc...</td>
      <td>HENRIETTE MAERSK</td>
      <td>9399349</td>
      <td>oil_mr1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>085ab83b592713e314070620a8cb9f4d795a2b486075f4...</td>
      <td>VS</td>
      <td>9252292</td>
      <td>oil_mr1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>09332aaa6067574eac586030b5b81cf5554337c4f48d17...</td>
      <td>BULL SULAWESI</td>
      <td>9180920</td>
      <td>oil_lr2</td>
    </tr>
  </tbody>
</table>
</div>



## Conclusion

In this tutorial, we covered the essentials of working with reference data using the Vortexa Python SDK. We began by discussing the importance of reference data and its role in supporting accurate and consistent data operations. Through various examples, including locations, vessels, and products, we demonstrated how reference data can be effectively applied in your analyses.

You’ve learned how to query and retrieve reference data based on different criteria such as name or type. Mastering the use of reference data enables you to drive more accurate insights, improve data consistency, and enhance your understanding of the energy markets.


