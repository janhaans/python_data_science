
# Clean & Analyse used cars <br/>
Dataset = eBay Kleinanzeigen ([see more](https://data.world/data-society/used-cars-data))


```python
import numpy as np
import pandas as pd
```


```python
autos = pd.read_csv('autos.csv', encoding='ISO-8859-1')
```


```python
autos
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
      <th>dateCrawled</th>
      <th>name</th>
      <th>seller</th>
      <th>offerType</th>
      <th>price</th>
      <th>abtest</th>
      <th>vehicleType</th>
      <th>yearOfRegistration</th>
      <th>gearbox</th>
      <th>powerPS</th>
      <th>model</th>
      <th>odometer</th>
      <th>monthOfRegistration</th>
      <th>fuelType</th>
      <th>brand</th>
      <th>notRepairedDamage</th>
      <th>dateCreated</th>
      <th>nrOfPictures</th>
      <th>postalCode</th>
      <th>lastSeen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016-03-26 17:47:46</td>
      <td>Peugeot_807_160_NAVTECH_ON_BOARD</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,000</td>
      <td>control</td>
      <td>bus</td>
      <td>2004</td>
      <td>manuell</td>
      <td>158</td>
      <td>andere</td>
      <td>150,000km</td>
      <td>3</td>
      <td>lpg</td>
      <td>peugeot</td>
      <td>nein</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>79588</td>
      <td>2016-04-06 06:45:54</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016-04-04 13:38:56</td>
      <td>BMW_740i_4_4_Liter_HAMANN_UMBAU_Mega_Optik</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$8,500</td>
      <td>control</td>
      <td>limousine</td>
      <td>1997</td>
      <td>automatik</td>
      <td>286</td>
      <td>7er</td>
      <td>150,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>bmw</td>
      <td>nein</td>
      <td>2016-04-04 00:00:00</td>
      <td>0</td>
      <td>71034</td>
      <td>2016-04-06 14:45:08</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016-03-26 18:57:24</td>
      <td>Volkswagen_Golf_1.6_United</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$8,990</td>
      <td>test</td>
      <td>limousine</td>
      <td>2009</td>
      <td>manuell</td>
      <td>102</td>
      <td>golf</td>
      <td>70,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>35394</td>
      <td>2016-04-06 20:15:37</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016-03-12 16:58:10</td>
      <td>Smart_smart_fortwo_coupe_softouch/F1/Klima/Pan...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$4,350</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2007</td>
      <td>automatik</td>
      <td>71</td>
      <td>fortwo</td>
      <td>70,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>smart</td>
      <td>nein</td>
      <td>2016-03-12 00:00:00</td>
      <td>0</td>
      <td>33729</td>
      <td>2016-03-15 03:16:28</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016-04-01 14:38:50</td>
      <td>Ford_Focus_1_6_Benzin_TÜV_neu_ist_sehr_gepfleg...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,350</td>
      <td>test</td>
      <td>kombi</td>
      <td>2003</td>
      <td>manuell</td>
      <td>0</td>
      <td>focus</td>
      <td>150,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>ford</td>
      <td>nein</td>
      <td>2016-04-01 00:00:00</td>
      <td>0</td>
      <td>39218</td>
      <td>2016-04-01 14:38:50</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2016-03-21 13:47:45</td>
      <td>Chrysler_Grand_Voyager_2.8_CRD_Aut.Limited_Sto...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$7,900</td>
      <td>test</td>
      <td>bus</td>
      <td>2006</td>
      <td>automatik</td>
      <td>150</td>
      <td>voyager</td>
      <td>150,000km</td>
      <td>4</td>
      <td>diesel</td>
      <td>chrysler</td>
      <td>NaN</td>
      <td>2016-03-21 00:00:00</td>
      <td>0</td>
      <td>22962</td>
      <td>2016-04-06 09:45:21</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2016-03-20 17:55:21</td>
      <td>VW_Golf_III_GT_Special_Electronic_Green_Metall...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$300</td>
      <td>test</td>
      <td>limousine</td>
      <td>1995</td>
      <td>manuell</td>
      <td>90</td>
      <td>golf</td>
      <td>150,000km</td>
      <td>8</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>NaN</td>
      <td>2016-03-20 00:00:00</td>
      <td>0</td>
      <td>31535</td>
      <td>2016-03-23 02:48:59</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2016-03-16 18:55:19</td>
      <td>Golf_IV_1.9_TDI_90PS</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,990</td>
      <td>control</td>
      <td>limousine</td>
      <td>1998</td>
      <td>manuell</td>
      <td>90</td>
      <td>golf</td>
      <td>150,000km</td>
      <td>12</td>
      <td>diesel</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-16 00:00:00</td>
      <td>0</td>
      <td>53474</td>
      <td>2016-04-07 03:17:32</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2016-03-22 16:51:34</td>
      <td>Seat_Arosa</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$250</td>
      <td>test</td>
      <td>NaN</td>
      <td>2000</td>
      <td>manuell</td>
      <td>0</td>
      <td>arosa</td>
      <td>150,000km</td>
      <td>10</td>
      <td>NaN</td>
      <td>seat</td>
      <td>nein</td>
      <td>2016-03-22 00:00:00</td>
      <td>0</td>
      <td>7426</td>
      <td>2016-03-26 18:18:10</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2016-03-16 13:47:02</td>
      <td>Renault_Megane_Scenic_1.6e_RT_Klimaanlage</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$590</td>
      <td>control</td>
      <td>bus</td>
      <td>1997</td>
      <td>manuell</td>
      <td>90</td>
      <td>megane</td>
      <td>150,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>renault</td>
      <td>nein</td>
      <td>2016-03-16 00:00:00</td>
      <td>0</td>
      <td>15749</td>
      <td>2016-04-06 10:46:35</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2016-03-15 01:41:36</td>
      <td>VW_Golf_Tuning_in_siber/grau</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$999</td>
      <td>test</td>
      <td>NaN</td>
      <td>2017</td>
      <td>manuell</td>
      <td>90</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>4</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-14 00:00:00</td>
      <td>0</td>
      <td>86157</td>
      <td>2016-04-07 03:16:21</td>
    </tr>
    <tr>
      <th>11</th>
      <td>2016-03-16 18:45:34</td>
      <td>Mercedes_A140_Motorschaden</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$350</td>
      <td>control</td>
      <td>NaN</td>
      <td>2000</td>
      <td>NaN</td>
      <td>0</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>0</td>
      <td>benzin</td>
      <td>mercedes_benz</td>
      <td>NaN</td>
      <td>2016-03-16 00:00:00</td>
      <td>0</td>
      <td>17498</td>
      <td>2016-03-16 18:45:34</td>
    </tr>
    <tr>
      <th>12</th>
      <td>2016-03-31 19:48:22</td>
      <td>Smart_smart_fortwo_coupe_softouch_pure_MHD_Pan...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,299</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2010</td>
      <td>automatik</td>
      <td>71</td>
      <td>fortwo</td>
      <td>50,000km</td>
      <td>9</td>
      <td>benzin</td>
      <td>smart</td>
      <td>nein</td>
      <td>2016-03-31 00:00:00</td>
      <td>0</td>
      <td>34590</td>
      <td>2016-04-06 14:17:52</td>
    </tr>
    <tr>
      <th>13</th>
      <td>2016-03-23 10:48:32</td>
      <td>Audi_A3_1.6_tuning</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,350</td>
      <td>control</td>
      <td>limousine</td>
      <td>1999</td>
      <td>manuell</td>
      <td>101</td>
      <td>a3</td>
      <td>150,000km</td>
      <td>11</td>
      <td>benzin</td>
      <td>audi</td>
      <td>nein</td>
      <td>2016-03-23 00:00:00</td>
      <td>0</td>
      <td>12043</td>
      <td>2016-04-01 14:17:13</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2016-03-23 11:50:46</td>
      <td>Renault_Clio_3__Dynamique_1.2__16_V;_viele_Ver...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$3,999</td>
      <td>test</td>
      <td>kleinwagen</td>
      <td>2007</td>
      <td>manuell</td>
      <td>75</td>
      <td>clio</td>
      <td>150,000km</td>
      <td>9</td>
      <td>benzin</td>
      <td>renault</td>
      <td>NaN</td>
      <td>2016-03-23 00:00:00</td>
      <td>0</td>
      <td>81737</td>
      <td>2016-04-01 15:46:47</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2016-04-01 12:06:20</td>
      <td>Corvette_C3_Coupe_T_Top_Crossfire_Injection</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$18,900</td>
      <td>test</td>
      <td>coupe</td>
      <td>1982</td>
      <td>automatik</td>
      <td>203</td>
      <td>NaN</td>
      <td>80,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>sonstige_autos</td>
      <td>nein</td>
      <td>2016-04-01 00:00:00</td>
      <td>0</td>
      <td>61276</td>
      <td>2016-04-02 21:10:48</td>
    </tr>
    <tr>
      <th>16</th>
      <td>2016-03-16 14:59:02</td>
      <td>Opel_Vectra_B_Kombi</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$350</td>
      <td>test</td>
      <td>kombi</td>
      <td>1999</td>
      <td>manuell</td>
      <td>101</td>
      <td>vectra</td>
      <td>150,000km</td>
      <td>5</td>
      <td>benzin</td>
      <td>opel</td>
      <td>nein</td>
      <td>2016-03-16 00:00:00</td>
      <td>0</td>
      <td>57299</td>
      <td>2016-03-18 05:29:37</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2016-03-29 11:46:22</td>
      <td>Volkswagen_Scirocco_2_G60</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,500</td>
      <td>test</td>
      <td>coupe</td>
      <td>1990</td>
      <td>manuell</td>
      <td>205</td>
      <td>scirocco</td>
      <td>150,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-29 00:00:00</td>
      <td>0</td>
      <td>74821</td>
      <td>2016-04-05 20:46:26</td>
    </tr>
    <tr>
      <th>18</th>
      <td>2016-03-26 19:57:44</td>
      <td>Verkaufen_mein_bmw_e36_320_i_touring</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$300</td>
      <td>control</td>
      <td>bus</td>
      <td>1995</td>
      <td>manuell</td>
      <td>150</td>
      <td>3er</td>
      <td>150,000km</td>
      <td>0</td>
      <td>benzin</td>
      <td>bmw</td>
      <td>NaN</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>54329</td>
      <td>2016-04-02 12:16:41</td>
    </tr>
    <tr>
      <th>19</th>
      <td>2016-03-17 13:36:21</td>
      <td>mazda_tribute_2.0_mit_gas_und_tuev_neu_2018</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$4,150</td>
      <td>control</td>
      <td>suv</td>
      <td>2004</td>
      <td>manuell</td>
      <td>124</td>
      <td>andere</td>
      <td>150,000km</td>
      <td>2</td>
      <td>lpg</td>
      <td>mazda</td>
      <td>nein</td>
      <td>2016-03-17 00:00:00</td>
      <td>0</td>
      <td>40878</td>
      <td>2016-03-17 14:45:58</td>
    </tr>
    <tr>
      <th>20</th>
      <td>2016-03-05 19:57:31</td>
      <td>Audi_A4_Avant_1.9_TDI_*6_Gang*AHK*Klimatronik*...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$3,500</td>
      <td>test</td>
      <td>kombi</td>
      <td>2003</td>
      <td>manuell</td>
      <td>131</td>
      <td>a4</td>
      <td>150,000km</td>
      <td>5</td>
      <td>diesel</td>
      <td>audi</td>
      <td>NaN</td>
      <td>2016-03-05 00:00:00</td>
      <td>0</td>
      <td>53913</td>
      <td>2016-03-07 05:46:46</td>
    </tr>
    <tr>
      <th>21</th>
      <td>2016-03-06 19:07:10</td>
      <td>Porsche_911_Carrera_4S_Cabrio</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$41,500</td>
      <td>test</td>
      <td>cabrio</td>
      <td>2004</td>
      <td>manuell</td>
      <td>320</td>
      <td>911</td>
      <td>150,000km</td>
      <td>4</td>
      <td>benzin</td>
      <td>porsche</td>
      <td>nein</td>
      <td>2016-03-06 00:00:00</td>
      <td>0</td>
      <td>65428</td>
      <td>2016-04-05 23:46:19</td>
    </tr>
    <tr>
      <th>22</th>
      <td>2016-03-28 20:50:54</td>
      <td>MINI_Cooper_S_Cabrio</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$25,450</td>
      <td>control</td>
      <td>cabrio</td>
      <td>2015</td>
      <td>manuell</td>
      <td>184</td>
      <td>cooper</td>
      <td>10,000km</td>
      <td>1</td>
      <td>benzin</td>
      <td>mini</td>
      <td>nein</td>
      <td>2016-03-28 00:00:00</td>
      <td>0</td>
      <td>44789</td>
      <td>2016-04-01 06:45:30</td>
    </tr>
    <tr>
      <th>23</th>
      <td>2016-03-10 19:55:34</td>
      <td>Peugeot_Boxer_2_2_HDi_120_Ps_9_Sitzer_inkl_Klima</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$7,999</td>
      <td>control</td>
      <td>bus</td>
      <td>2010</td>
      <td>manuell</td>
      <td>120</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>2</td>
      <td>diesel</td>
      <td>peugeot</td>
      <td>nein</td>
      <td>2016-03-10 00:00:00</td>
      <td>0</td>
      <td>30900</td>
      <td>2016-03-17 08:45:17</td>
    </tr>
    <tr>
      <th>24</th>
      <td>2016-04-03 11:57:02</td>
      <td>BMW_535i_xDrive_Sport_Aut.</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$48,500</td>
      <td>control</td>
      <td>limousine</td>
      <td>2014</td>
      <td>automatik</td>
      <td>306</td>
      <td>5er</td>
      <td>30,000km</td>
      <td>12</td>
      <td>benzin</td>
      <td>bmw</td>
      <td>nein</td>
      <td>2016-04-03 00:00:00</td>
      <td>0</td>
      <td>22547</td>
      <td>2016-04-07 13:16:50</td>
    </tr>
    <tr>
      <th>25</th>
      <td>2016-03-21 21:56:18</td>
      <td>Ford_escort_kombi_an_bastler_mit_ghia_ausstattung</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$90</td>
      <td>control</td>
      <td>kombi</td>
      <td>1996</td>
      <td>manuell</td>
      <td>116</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>4</td>
      <td>benzin</td>
      <td>ford</td>
      <td>ja</td>
      <td>2016-03-21 00:00:00</td>
      <td>0</td>
      <td>27574</td>
      <td>2016-04-01 05:16:49</td>
    </tr>
    <tr>
      <th>26</th>
      <td>2016-04-03 22:46:28</td>
      <td>Volkswagen_Polo_Fox</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$777</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>1992</td>
      <td>manuell</td>
      <td>54</td>
      <td>polo</td>
      <td>125,000km</td>
      <td>2</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-04-03 00:00:00</td>
      <td>0</td>
      <td>38110</td>
      <td>2016-04-05 23:46:48</td>
    </tr>
    <tr>
      <th>27</th>
      <td>2016-03-27 18:45:01</td>
      <td>Hat_einer_Ahnung_mit_Ford_Galaxy_HILFE</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$0</td>
      <td>control</td>
      <td>NaN</td>
      <td>2005</td>
      <td>NaN</td>
      <td>0</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>0</td>
      <td>NaN</td>
      <td>ford</td>
      <td>NaN</td>
      <td>2016-03-27 00:00:00</td>
      <td>0</td>
      <td>66701</td>
      <td>2016-03-27 18:45:01</td>
    </tr>
    <tr>
      <th>28</th>
      <td>2016-03-19 21:56:19</td>
      <td>MINI_Cooper_D</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,250</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2007</td>
      <td>manuell</td>
      <td>110</td>
      <td>cooper</td>
      <td>150,000km</td>
      <td>7</td>
      <td>diesel</td>
      <td>mini</td>
      <td>ja</td>
      <td>2016-03-19 00:00:00</td>
      <td>0</td>
      <td>15745</td>
      <td>2016-04-07 14:58:48</td>
    </tr>
    <tr>
      <th>29</th>
      <td>2016-04-02 12:45:44</td>
      <td>Mercedes_Benz_E_320_T_CDI_Avantgarde_DPF7_Sitz...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$4,999</td>
      <td>test</td>
      <td>kombi</td>
      <td>2004</td>
      <td>automatik</td>
      <td>204</td>
      <td>e_klasse</td>
      <td>150,000km</td>
      <td>10</td>
      <td>diesel</td>
      <td>mercedes_benz</td>
      <td>nein</td>
      <td>2016-04-02 00:00:00</td>
      <td>0</td>
      <td>47638</td>
      <td>2016-04-02 12:45:44</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>49970</th>
      <td>2016-03-21 22:47:37</td>
      <td>c4_Grand_Picasso_mit_Automatik_Leder_Navi_Temp...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$15,800</td>
      <td>control</td>
      <td>bus</td>
      <td>2010</td>
      <td>automatik</td>
      <td>136</td>
      <td>c4</td>
      <td>60,000km</td>
      <td>4</td>
      <td>diesel</td>
      <td>citroen</td>
      <td>nein</td>
      <td>2016-03-21 00:00:00</td>
      <td>0</td>
      <td>14947</td>
      <td>2016-04-07 04:17:34</td>
    </tr>
    <tr>
      <th>49971</th>
      <td>2016-03-29 14:54:12</td>
      <td>W.Lupo_1.0</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$950</td>
      <td>test</td>
      <td>kleinwagen</td>
      <td>2001</td>
      <td>manuell</td>
      <td>50</td>
      <td>lupo</td>
      <td>150,000km</td>
      <td>4</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-29 00:00:00</td>
      <td>0</td>
      <td>65197</td>
      <td>2016-03-29 20:41:51</td>
    </tr>
    <tr>
      <th>49972</th>
      <td>2016-03-26 22:25:23</td>
      <td>Mercedes_Benz_Vito_115_CDI_Extralang_Aut.</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$3,300</td>
      <td>control</td>
      <td>bus</td>
      <td>2004</td>
      <td>automatik</td>
      <td>150</td>
      <td>vito</td>
      <td>150,000km</td>
      <td>10</td>
      <td>diesel</td>
      <td>mercedes_benz</td>
      <td>ja</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>65326</td>
      <td>2016-03-28 11:28:18</td>
    </tr>
    <tr>
      <th>49973</th>
      <td>2016-03-27 05:32:39</td>
      <td>Mercedes_Benz_SLK_200_Kompressor</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$6,000</td>
      <td>control</td>
      <td>cabrio</td>
      <td>2004</td>
      <td>manuell</td>
      <td>163</td>
      <td>slk</td>
      <td>150,000km</td>
      <td>11</td>
      <td>benzin</td>
      <td>mercedes_benz</td>
      <td>nein</td>
      <td>2016-03-27 00:00:00</td>
      <td>0</td>
      <td>53567</td>
      <td>2016-03-27 08:25:24</td>
    </tr>
    <tr>
      <th>49974</th>
      <td>2016-03-20 10:52:31</td>
      <td>Golf_1_Cabrio_Tuev_Neu_viele_Extras_alles_eing...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$0</td>
      <td>control</td>
      <td>cabrio</td>
      <td>1983</td>
      <td>manuell</td>
      <td>70</td>
      <td>golf</td>
      <td>150,000km</td>
      <td>2</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-20 00:00:00</td>
      <td>0</td>
      <td>8209</td>
      <td>2016-03-27 19:48:16</td>
    </tr>
    <tr>
      <th>49975</th>
      <td>2016-03-27 20:51:39</td>
      <td>Honda_Jazz_1.3_DSi_i_VTEC_IMA_CVT_Comfort</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$9,700</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2012</td>
      <td>automatik</td>
      <td>88</td>
      <td>jazz</td>
      <td>100,000km</td>
      <td>11</td>
      <td>hybrid</td>
      <td>honda</td>
      <td>nein</td>
      <td>2016-03-27 00:00:00</td>
      <td>0</td>
      <td>84385</td>
      <td>2016-04-05 19:45:34</td>
    </tr>
    <tr>
      <th>49976</th>
      <td>2016-03-19 18:56:05</td>
      <td>Audi_80_Avant_2.6_E__Vollausstattung!!_Einziga...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,900</td>
      <td>test</td>
      <td>kombi</td>
      <td>1992</td>
      <td>automatik</td>
      <td>150</td>
      <td>80</td>
      <td>150,000km</td>
      <td>12</td>
      <td>benzin</td>
      <td>audi</td>
      <td>nein</td>
      <td>2016-03-19 00:00:00</td>
      <td>0</td>
      <td>36100</td>
      <td>2016-04-07 06:16:44</td>
    </tr>
    <tr>
      <th>49977</th>
      <td>2016-03-31 18:37:18</td>
      <td>Mercedes_Benz_C200_Cdi_W203</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,500</td>
      <td>control</td>
      <td>limousine</td>
      <td>2003</td>
      <td>manuell</td>
      <td>116</td>
      <td>c_klasse</td>
      <td>150,000km</td>
      <td>2</td>
      <td>diesel</td>
      <td>mercedes_benz</td>
      <td>nein</td>
      <td>2016-03-31 00:00:00</td>
      <td>0</td>
      <td>33739</td>
      <td>2016-04-06 12:16:11</td>
    </tr>
    <tr>
      <th>49978</th>
      <td>2016-04-04 10:37:14</td>
      <td>Mercedes_Benz_E_200_Classic</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$900</td>
      <td>control</td>
      <td>limousine</td>
      <td>1996</td>
      <td>automatik</td>
      <td>136</td>
      <td>e_klasse</td>
      <td>150,000km</td>
      <td>9</td>
      <td>benzin</td>
      <td>mercedes_benz</td>
      <td>ja</td>
      <td>2016-04-04 00:00:00</td>
      <td>0</td>
      <td>24405</td>
      <td>2016-04-06 12:44:20</td>
    </tr>
    <tr>
      <th>49979</th>
      <td>2016-03-20 18:38:40</td>
      <td>Volkswagen_Polo_1.6_TDI_Style</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$11,000</td>
      <td>test</td>
      <td>kleinwagen</td>
      <td>2011</td>
      <td>manuell</td>
      <td>90</td>
      <td>polo</td>
      <td>70,000km</td>
      <td>11</td>
      <td>diesel</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-20 00:00:00</td>
      <td>0</td>
      <td>48455</td>
      <td>2016-04-07 01:45:12</td>
    </tr>
    <tr>
      <th>49980</th>
      <td>2016-03-12 10:55:54</td>
      <td>Ford_Escort_Turnier_16V</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$400</td>
      <td>control</td>
      <td>kombi</td>
      <td>1995</td>
      <td>manuell</td>
      <td>105</td>
      <td>escort</td>
      <td>125,000km</td>
      <td>3</td>
      <td>benzin</td>
      <td>ford</td>
      <td>NaN</td>
      <td>2016-03-12 00:00:00</td>
      <td>0</td>
      <td>56218</td>
      <td>2016-04-06 17:16:49</td>
    </tr>
    <tr>
      <th>49981</th>
      <td>2016-03-15 09:38:21</td>
      <td>Opel_Astra_Kombi_mit_Anhaengerkupplung</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$2,000</td>
      <td>control</td>
      <td>kombi</td>
      <td>1998</td>
      <td>manuell</td>
      <td>115</td>
      <td>astra</td>
      <td>150,000km</td>
      <td>12</td>
      <td>benzin</td>
      <td>opel</td>
      <td>nein</td>
      <td>2016-03-15 00:00:00</td>
      <td>0</td>
      <td>86859</td>
      <td>2016-04-05 17:21:46</td>
    </tr>
    <tr>
      <th>49982</th>
      <td>2016-03-29 18:51:08</td>
      <td>Skoda_Fabia_4_Tuerer_Bj:2004__85.000Tkm</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,950</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2004</td>
      <td>manuell</td>
      <td>0</td>
      <td>fabia</td>
      <td>90,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>skoda</td>
      <td>NaN</td>
      <td>2016-03-29 00:00:00</td>
      <td>0</td>
      <td>45884</td>
      <td>2016-03-29 18:51:08</td>
    </tr>
    <tr>
      <th>49983</th>
      <td>2016-03-06 12:43:04</td>
      <td>Ford_focus_99</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$600</td>
      <td>test</td>
      <td>kleinwagen</td>
      <td>1999</td>
      <td>manuell</td>
      <td>101</td>
      <td>focus</td>
      <td>150,000km</td>
      <td>4</td>
      <td>benzin</td>
      <td>ford</td>
      <td>NaN</td>
      <td>2016-03-06 00:00:00</td>
      <td>0</td>
      <td>52477</td>
      <td>2016-03-09 06:16:08</td>
    </tr>
    <tr>
      <th>49984</th>
      <td>2016-03-31 22:48:48</td>
      <td>Student_sucht_ein__Anfaengerauto___ab_2000_BJ_...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$0</td>
      <td>test</td>
      <td>NaN</td>
      <td>2000</td>
      <td>NaN</td>
      <td>0</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>0</td>
      <td>NaN</td>
      <td>sonstige_autos</td>
      <td>NaN</td>
      <td>2016-03-31 00:00:00</td>
      <td>0</td>
      <td>12103</td>
      <td>2016-04-02 19:44:53</td>
    </tr>
    <tr>
      <th>49985</th>
      <td>2016-04-02 16:38:23</td>
      <td>Verkaufe_meinen_vw_vento!</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,000</td>
      <td>control</td>
      <td>NaN</td>
      <td>1995</td>
      <td>automatik</td>
      <td>0</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>0</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>NaN</td>
      <td>2016-04-02 00:00:00</td>
      <td>0</td>
      <td>30900</td>
      <td>2016-04-06 15:17:52</td>
    </tr>
    <tr>
      <th>49986</th>
      <td>2016-04-04 20:46:02</td>
      <td>Chrysler_300C_3.0_CRD_DPF_Automatik_Voll_Ausst...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$15,900</td>
      <td>control</td>
      <td>limousine</td>
      <td>2010</td>
      <td>automatik</td>
      <td>218</td>
      <td>300c</td>
      <td>125,000km</td>
      <td>11</td>
      <td>diesel</td>
      <td>chrysler</td>
      <td>nein</td>
      <td>2016-04-04 00:00:00</td>
      <td>0</td>
      <td>73527</td>
      <td>2016-04-06 23:16:00</td>
    </tr>
    <tr>
      <th>49987</th>
      <td>2016-03-22 20:47:27</td>
      <td>Audi_A3_Limousine_2.0_TDI_DPF_Ambition__NAVI__...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$21,990</td>
      <td>control</td>
      <td>limousine</td>
      <td>2013</td>
      <td>manuell</td>
      <td>150</td>
      <td>a3</td>
      <td>50,000km</td>
      <td>11</td>
      <td>diesel</td>
      <td>audi</td>
      <td>nein</td>
      <td>2016-03-22 00:00:00</td>
      <td>0</td>
      <td>94362</td>
      <td>2016-03-26 22:46:06</td>
    </tr>
    <tr>
      <th>49988</th>
      <td>2016-03-28 19:49:51</td>
      <td>BMW_330_Ci</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$9,550</td>
      <td>control</td>
      <td>coupe</td>
      <td>2001</td>
      <td>manuell</td>
      <td>231</td>
      <td>3er</td>
      <td>150,000km</td>
      <td>10</td>
      <td>benzin</td>
      <td>bmw</td>
      <td>nein</td>
      <td>2016-03-28 00:00:00</td>
      <td>0</td>
      <td>83646</td>
      <td>2016-04-07 02:17:40</td>
    </tr>
    <tr>
      <th>49989</th>
      <td>2016-03-11 19:50:37</td>
      <td>VW_Polo_zum_Ausschlachten_oder_Wiederaufbau</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$150</td>
      <td>test</td>
      <td>kleinwagen</td>
      <td>1997</td>
      <td>manuell</td>
      <td>0</td>
      <td>polo</td>
      <td>150,000km</td>
      <td>5</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>ja</td>
      <td>2016-03-11 00:00:00</td>
      <td>0</td>
      <td>21244</td>
      <td>2016-03-12 10:17:55</td>
    </tr>
    <tr>
      <th>49990</th>
      <td>2016-03-21 19:54:19</td>
      <td>Mercedes_Benz_A_200__BlueEFFICIENCY__Urban</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$17,500</td>
      <td>test</td>
      <td>limousine</td>
      <td>2012</td>
      <td>manuell</td>
      <td>156</td>
      <td>a_klasse</td>
      <td>30,000km</td>
      <td>12</td>
      <td>benzin</td>
      <td>mercedes_benz</td>
      <td>nein</td>
      <td>2016-03-21 00:00:00</td>
      <td>0</td>
      <td>58239</td>
      <td>2016-04-06 22:46:57</td>
    </tr>
    <tr>
      <th>49991</th>
      <td>2016-03-06 15:25:19</td>
      <td>Kleinwagen</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$500</td>
      <td>control</td>
      <td>NaN</td>
      <td>2016</td>
      <td>manuell</td>
      <td>0</td>
      <td>twingo</td>
      <td>150,000km</td>
      <td>0</td>
      <td>benzin</td>
      <td>renault</td>
      <td>NaN</td>
      <td>2016-03-06 00:00:00</td>
      <td>0</td>
      <td>61350</td>
      <td>2016-03-06 18:24:19</td>
    </tr>
    <tr>
      <th>49992</th>
      <td>2016-03-10 19:37:38</td>
      <td>Fiat_Grande_Punto_1.4_T_Jet_16V_Sport</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$4,800</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2009</td>
      <td>manuell</td>
      <td>120</td>
      <td>andere</td>
      <td>125,000km</td>
      <td>9</td>
      <td>lpg</td>
      <td>fiat</td>
      <td>nein</td>
      <td>2016-03-10 00:00:00</td>
      <td>0</td>
      <td>68642</td>
      <td>2016-03-13 01:44:51</td>
    </tr>
    <tr>
      <th>49993</th>
      <td>2016-03-15 18:47:35</td>
      <td>Audi_A3__1_8l__Silber;_schoenes_Fahrzeug</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,650</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>1997</td>
      <td>manuell</td>
      <td>0</td>
      <td>NaN</td>
      <td>150,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>audi</td>
      <td>NaN</td>
      <td>2016-03-15 00:00:00</td>
      <td>0</td>
      <td>65203</td>
      <td>2016-04-06 19:46:53</td>
    </tr>
    <tr>
      <th>49994</th>
      <td>2016-03-22 17:36:42</td>
      <td>Audi_A6__S6__Avant_4.2_quattro_eventuell_Tausc...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,000</td>
      <td>control</td>
      <td>kombi</td>
      <td>2001</td>
      <td>automatik</td>
      <td>299</td>
      <td>a6</td>
      <td>150,000km</td>
      <td>1</td>
      <td>benzin</td>
      <td>audi</td>
      <td>nein</td>
      <td>2016-03-22 00:00:00</td>
      <td>0</td>
      <td>46537</td>
      <td>2016-04-06 08:16:39</td>
    </tr>
    <tr>
      <th>49995</th>
      <td>2016-03-27 14:38:19</td>
      <td>Audi_Q5_3.0_TDI_qu._S_tr.__Navi__Panorama__Xenon</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$24,900</td>
      <td>control</td>
      <td>limousine</td>
      <td>2011</td>
      <td>automatik</td>
      <td>239</td>
      <td>q5</td>
      <td>100,000km</td>
      <td>1</td>
      <td>diesel</td>
      <td>audi</td>
      <td>nein</td>
      <td>2016-03-27 00:00:00</td>
      <td>0</td>
      <td>82131</td>
      <td>2016-04-01 13:47:40</td>
    </tr>
    <tr>
      <th>49996</th>
      <td>2016-03-28 10:50:25</td>
      <td>Opel_Astra_F_Cabrio_Bertone_Edition___TÜV_neu+...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,980</td>
      <td>control</td>
      <td>cabrio</td>
      <td>1996</td>
      <td>manuell</td>
      <td>75</td>
      <td>astra</td>
      <td>150,000km</td>
      <td>5</td>
      <td>benzin</td>
      <td>opel</td>
      <td>nein</td>
      <td>2016-03-28 00:00:00</td>
      <td>0</td>
      <td>44807</td>
      <td>2016-04-02 14:18:02</td>
    </tr>
    <tr>
      <th>49997</th>
      <td>2016-04-02 14:44:48</td>
      <td>Fiat_500_C_1.2_Dualogic_Lounge</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$13,200</td>
      <td>test</td>
      <td>cabrio</td>
      <td>2014</td>
      <td>automatik</td>
      <td>69</td>
      <td>500</td>
      <td>5,000km</td>
      <td>11</td>
      <td>benzin</td>
      <td>fiat</td>
      <td>nein</td>
      <td>2016-04-02 00:00:00</td>
      <td>0</td>
      <td>73430</td>
      <td>2016-04-04 11:47:27</td>
    </tr>
    <tr>
      <th>49998</th>
      <td>2016-03-08 19:25:42</td>
      <td>Audi_A3_2.0_TDI_Sportback_Ambition</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$22,900</td>
      <td>control</td>
      <td>kombi</td>
      <td>2013</td>
      <td>manuell</td>
      <td>150</td>
      <td>a3</td>
      <td>40,000km</td>
      <td>11</td>
      <td>diesel</td>
      <td>audi</td>
      <td>nein</td>
      <td>2016-03-08 00:00:00</td>
      <td>0</td>
      <td>35683</td>
      <td>2016-04-05 16:45:07</td>
    </tr>
    <tr>
      <th>49999</th>
      <td>2016-03-14 00:42:12</td>
      <td>Opel_Vectra_1.6_16V</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,250</td>
      <td>control</td>
      <td>limousine</td>
      <td>1996</td>
      <td>manuell</td>
      <td>101</td>
      <td>vectra</td>
      <td>150,000km</td>
      <td>1</td>
      <td>benzin</td>
      <td>opel</td>
      <td>nein</td>
      <td>2016-03-13 00:00:00</td>
      <td>0</td>
      <td>45897</td>
      <td>2016-04-06 21:18:48</td>
    </tr>
  </tbody>
</table>
<p>50000 rows × 20 columns</p>
</div>




```python
autos.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 50000 entries, 0 to 49999
    Data columns (total 20 columns):
    dateCrawled            50000 non-null object
    name                   50000 non-null object
    seller                 50000 non-null object
    offerType              50000 non-null object
    price                  50000 non-null object
    abtest                 50000 non-null object
    vehicleType            44905 non-null object
    yearOfRegistration     50000 non-null int64
    gearbox                47320 non-null object
    powerPS                50000 non-null int64
    model                  47242 non-null object
    odometer               50000 non-null object
    monthOfRegistration    50000 non-null int64
    fuelType               45518 non-null object
    brand                  50000 non-null object
    notRepairedDamage      40171 non-null object
    dateCreated            50000 non-null object
    nrOfPictures           50000 non-null int64
    postalCode             50000 non-null int64
    lastSeen               50000 non-null object
    dtypes: int64(5), object(15)
    memory usage: 7.6+ MB



```python
autos.head()
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
      <th>dateCrawled</th>
      <th>name</th>
      <th>seller</th>
      <th>offerType</th>
      <th>price</th>
      <th>abtest</th>
      <th>vehicleType</th>
      <th>yearOfRegistration</th>
      <th>gearbox</th>
      <th>powerPS</th>
      <th>model</th>
      <th>odometer</th>
      <th>monthOfRegistration</th>
      <th>fuelType</th>
      <th>brand</th>
      <th>notRepairedDamage</th>
      <th>dateCreated</th>
      <th>nrOfPictures</th>
      <th>postalCode</th>
      <th>lastSeen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016-03-26 17:47:46</td>
      <td>Peugeot_807_160_NAVTECH_ON_BOARD</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,000</td>
      <td>control</td>
      <td>bus</td>
      <td>2004</td>
      <td>manuell</td>
      <td>158</td>
      <td>andere</td>
      <td>150,000km</td>
      <td>3</td>
      <td>lpg</td>
      <td>peugeot</td>
      <td>nein</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>79588</td>
      <td>2016-04-06 06:45:54</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016-04-04 13:38:56</td>
      <td>BMW_740i_4_4_Liter_HAMANN_UMBAU_Mega_Optik</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$8,500</td>
      <td>control</td>
      <td>limousine</td>
      <td>1997</td>
      <td>automatik</td>
      <td>286</td>
      <td>7er</td>
      <td>150,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>bmw</td>
      <td>nein</td>
      <td>2016-04-04 00:00:00</td>
      <td>0</td>
      <td>71034</td>
      <td>2016-04-06 14:45:08</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016-03-26 18:57:24</td>
      <td>Volkswagen_Golf_1.6_United</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$8,990</td>
      <td>test</td>
      <td>limousine</td>
      <td>2009</td>
      <td>manuell</td>
      <td>102</td>
      <td>golf</td>
      <td>70,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>35394</td>
      <td>2016-04-06 20:15:37</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016-03-12 16:58:10</td>
      <td>Smart_smart_fortwo_coupe_softouch/F1/Klima/Pan...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$4,350</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2007</td>
      <td>automatik</td>
      <td>71</td>
      <td>fortwo</td>
      <td>70,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>smart</td>
      <td>nein</td>
      <td>2016-03-12 00:00:00</td>
      <td>0</td>
      <td>33729</td>
      <td>2016-03-15 03:16:28</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016-04-01 14:38:50</td>
      <td>Ford_Focus_1_6_Benzin_TÜV_neu_ist_sehr_gepfleg...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,350</td>
      <td>test</td>
      <td>kombi</td>
      <td>2003</td>
      <td>manuell</td>
      <td>0</td>
      <td>focus</td>
      <td>150,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>ford</td>
      <td>nein</td>
      <td>2016-04-01 00:00:00</td>
      <td>0</td>
      <td>39218</td>
      <td>2016-04-01 14:38:50</td>
    </tr>
  </tbody>
</table>
</div>



## First Observations

Columns with empty values:
- vehicleType
- gearbox
- model
- fuelType
- notRepairedDamage

Columns with date/time in string format:
- dateCrawled
- dateCreated
- lastSeen

Columns with integer/float in string format:
- price
- odometer

## Change column names from camelCase to snake_case


```python
column_names = [
    'date_crawled',
    'name',
    'seller',
    'offer_type',
    'price',
    'abtest',
    'vehicle_type',
    'registration_year',
    'gearbox',
    'power_ps',
    'model',
    'odometer',
    'registration_month',
    'fuel_type',
    'brand',
    'unrepaired_damage',
    'ad_created',
    'nr_of_pictures',
    'postal_code',
    'last_seen'
]

autos.columns = column_names
autos.head()
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
      <th>date_crawled</th>
      <th>name</th>
      <th>seller</th>
      <th>offer_type</th>
      <th>price</th>
      <th>abtest</th>
      <th>vehicle_type</th>
      <th>registration_year</th>
      <th>gearbox</th>
      <th>power_ps</th>
      <th>model</th>
      <th>odometer</th>
      <th>registration_month</th>
      <th>fuel_type</th>
      <th>brand</th>
      <th>unrepaired_damage</th>
      <th>ad_created</th>
      <th>nr_of_pictures</th>
      <th>postal_code</th>
      <th>last_seen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2016-03-26 17:47:46</td>
      <td>Peugeot_807_160_NAVTECH_ON_BOARD</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$5,000</td>
      <td>control</td>
      <td>bus</td>
      <td>2004</td>
      <td>manuell</td>
      <td>158</td>
      <td>andere</td>
      <td>150,000km</td>
      <td>3</td>
      <td>lpg</td>
      <td>peugeot</td>
      <td>nein</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>79588</td>
      <td>2016-04-06 06:45:54</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2016-04-04 13:38:56</td>
      <td>BMW_740i_4_4_Liter_HAMANN_UMBAU_Mega_Optik</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$8,500</td>
      <td>control</td>
      <td>limousine</td>
      <td>1997</td>
      <td>automatik</td>
      <td>286</td>
      <td>7er</td>
      <td>150,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>bmw</td>
      <td>nein</td>
      <td>2016-04-04 00:00:00</td>
      <td>0</td>
      <td>71034</td>
      <td>2016-04-06 14:45:08</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2016-03-26 18:57:24</td>
      <td>Volkswagen_Golf_1.6_United</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$8,990</td>
      <td>test</td>
      <td>limousine</td>
      <td>2009</td>
      <td>manuell</td>
      <td>102</td>
      <td>golf</td>
      <td>70,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-03-26 00:00:00</td>
      <td>0</td>
      <td>35394</td>
      <td>2016-04-06 20:15:37</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2016-03-12 16:58:10</td>
      <td>Smart_smart_fortwo_coupe_softouch/F1/Klima/Pan...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$4,350</td>
      <td>control</td>
      <td>kleinwagen</td>
      <td>2007</td>
      <td>automatik</td>
      <td>71</td>
      <td>fortwo</td>
      <td>70,000km</td>
      <td>6</td>
      <td>benzin</td>
      <td>smart</td>
      <td>nein</td>
      <td>2016-03-12 00:00:00</td>
      <td>0</td>
      <td>33729</td>
      <td>2016-03-15 03:16:28</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2016-04-01 14:38:50</td>
      <td>Ford_Focus_1_6_Benzin_TÜV_neu_ist_sehr_gepfleg...</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$1,350</td>
      <td>test</td>
      <td>kombi</td>
      <td>2003</td>
      <td>manuell</td>
      <td>0</td>
      <td>focus</td>
      <td>150,000km</td>
      <td>7</td>
      <td>benzin</td>
      <td>ford</td>
      <td>nein</td>
      <td>2016-04-01 00:00:00</td>
      <td>0</td>
      <td>39218</td>
      <td>2016-04-01 14:38:50</td>
    </tr>
  </tbody>
</table>
</div>



# Data Cleaning|


```python
autos.describe(include='all')
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
      <th>date_crawled</th>
      <th>name</th>
      <th>seller</th>
      <th>offer_type</th>
      <th>price</th>
      <th>abtest</th>
      <th>vehicle_type</th>
      <th>registration_year</th>
      <th>gearbox</th>
      <th>power_ps</th>
      <th>model</th>
      <th>odometer</th>
      <th>registration_month</th>
      <th>fuel_type</th>
      <th>brand</th>
      <th>unrepaired_damage</th>
      <th>ad_created</th>
      <th>nr_of_pictures</th>
      <th>postal_code</th>
      <th>last_seen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>50000</td>
      <td>50000</td>
      <td>50000</td>
      <td>50000</td>
      <td>50000</td>
      <td>50000</td>
      <td>44905</td>
      <td>50000.000000</td>
      <td>47320</td>
      <td>50000.000000</td>
      <td>47242</td>
      <td>50000</td>
      <td>50000.000000</td>
      <td>45518</td>
      <td>50000</td>
      <td>40171</td>
      <td>50000</td>
      <td>50000.0</td>
      <td>50000.000000</td>
      <td>50000</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>48213</td>
      <td>38754</td>
      <td>2</td>
      <td>2</td>
      <td>2357</td>
      <td>2</td>
      <td>8</td>
      <td>NaN</td>
      <td>2</td>
      <td>NaN</td>
      <td>245</td>
      <td>13</td>
      <td>NaN</td>
      <td>7</td>
      <td>40</td>
      <td>2</td>
      <td>76</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>39481</td>
    </tr>
    <tr>
      <th>top</th>
      <td>2016-03-30 19:48:02</td>
      <td>Ford_Fiesta</td>
      <td>privat</td>
      <td>Angebot</td>
      <td>$0</td>
      <td>test</td>
      <td>limousine</td>
      <td>NaN</td>
      <td>manuell</td>
      <td>NaN</td>
      <td>golf</td>
      <td>150,000km</td>
      <td>NaN</td>
      <td>benzin</td>
      <td>volkswagen</td>
      <td>nein</td>
      <td>2016-04-03 00:00:00</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2016-04-07 06:17:27</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>3</td>
      <td>78</td>
      <td>49999</td>
      <td>49999</td>
      <td>1421</td>
      <td>25756</td>
      <td>12859</td>
      <td>NaN</td>
      <td>36993</td>
      <td>NaN</td>
      <td>4024</td>
      <td>32424</td>
      <td>NaN</td>
      <td>30107</td>
      <td>10687</td>
      <td>35232</td>
      <td>1946</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2005.073280</td>
      <td>NaN</td>
      <td>116.355920</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5.723360</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>50813.627300</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>105.712813</td>
      <td>NaN</td>
      <td>209.216627</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.711984</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>25779.747957</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>min</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1000.000000</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>1067.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1999.000000</td>
      <td>NaN</td>
      <td>70.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>30451.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2003.000000</td>
      <td>NaN</td>
      <td>105.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>49577.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2008.000000</td>
      <td>NaN</td>
      <td>150.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>71540.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>max</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9999.000000</td>
      <td>NaN</td>
      <td>17700.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>99998.000000</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
autos['seller'].value_counts()
```




    privat        49999
    gewerblich        1
    Name: seller, dtype: int64



Column **seller** can be dropped because almost all values are the same


```python
autos.drop(columns='seller', inplace=True)
```


```python
autos['offer_type'].value_counts()
```




    Angebot    49999
    Gesuch         1
    Name: offer_type, dtype: int64



Column **offer_type** can be dropped because almost all values are the same


```python
autos.drop(columns='offer_type', inplace=True)
```

Transform column **price** from string to integer


```python
autos['price'] = autos['price'].str.replace('$','')
autos['price'] = autos['price'].str.replace(',','')
autos['price'] = autos['price'].astype(int)
```


```python
autos['price'].head()
```




    0    5000
    1    8500
    2    8990
    3    4350
    4    1350
    Name: price, dtype: int64



Transform **odometer** from string to integer


```python
autos['odometer'] = autos['odometer'].str.replace('km','')
autos['odometer'] = autos['odometer'].str.replace(',','')
autos['odometer'] = autos['odometer'].astype(int)
autos.rename(columns={'odometer': 'odometer_km'}, inplace=True)
```


```python
autos['odometer_km'].head()
```




    0    150000
    1    150000
    2     70000
    3     70000
    4    150000
    Name: odometer_km, dtype: int64



Transform columns **date_crawled, ad_created, last_seen** from string to datetime


```python
autos['date_crawled'] = pd.to_datetime(autos['date_crawled']) 
autos['ad_created'] = pd.to_datetime(autos['ad_created'])
autos['last_seen'] = pd.to_datetime(autos['last_seen'])
```


```python
autos.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 50000 entries, 0 to 49999
    Data columns (total 18 columns):
    date_crawled          50000 non-null datetime64[ns]
    name                  50000 non-null object
    price                 50000 non-null int64
    abtest                50000 non-null object
    vehicle_type          44905 non-null object
    registration_year     50000 non-null int64
    gearbox               47320 non-null object
    power_ps              50000 non-null int64
    model                 47242 non-null object
    odometer_km           50000 non-null int64
    registration_month    50000 non-null int64
    fuel_type             45518 non-null object
    brand                 50000 non-null object
    unrepaired_damage     40171 non-null object
    ad_created            50000 non-null datetime64[ns]
    nr_of_pictures        50000 non-null int64
    postal_code           50000 non-null int64
    last_seen             50000 non-null datetime64[ns]
    dtypes: datetime64[ns](3), int64(7), object(8)
    memory usage: 6.9+ MB


Explore column **price**


```python
autos['price'].unique().shape
```




    (2357,)




```python
autos['price'].describe()
```




    count    5.000000e+04
    mean     9.840044e+03
    std      4.811044e+05
    min      0.000000e+00
    25%      1.100000e+03
    50%      2.950000e+03
    75%      7.200000e+03
    max      1.000000e+08
    Name: price, dtype: float64




```python
autos['price'].value_counts().sort_index().head(10)
```




    0     1421
    1      156
    2        3
    3        1
    5        2
    8        1
    9        1
    10       7
    11       2
    12       3
    Name: price, dtype: int64




```python
autos['price'].value_counts().sort_index(ascending=False).head(10)
```




    99999999    1
    27322222    1
    12345678    3
    11111111    2
    10000000    1
    3890000     1
    1300000     1
    1234566     1
    999999      2
    999990      1
    Name: price, dtype: int64



Remove outliers in column **price**
<p>Remove cars with price < 250</p>
<p>Remove cars with price > 350000</p>


```python
autos = autos[(autos['price'] > 200) & (autos['price'] < 350000)]
autos['price'].describe()
```




    count     47378.000000
    mean       6026.014142
    std        8988.151540
    min         205.000000
    25%        1300.000000
    50%        3200.000000
    75%        7500.000000
    max      345000.000000
    Name: price, dtype: float64



Explore column **odometer_km**


```python
autos['odometer_km'].unique()
```




    array([150000,  70000,  50000,  80000,  10000,  30000, 125000,  90000,
            20000,  60000,   5000, 100000,  40000])




```python
autos['odometer_km'].describe()
```




    count     47378.000000
    mean     125844.695850
    std       39478.320612
    min        5000.000000
    25%      125000.000000
    50%      150000.000000
    75%      150000.000000
    max      150000.000000
    Name: odometer_km, dtype: float64




```python
autos['odometer_km'].value_counts().sort_index()
```




    5000        704
    10000       242
    20000       744
    30000       772
    40000       812
    50000      1007
    60000      1144
    70000      1208
    80000      1405
    90000      1714
    100000     2074
    125000     4984
    150000    30568
    Name: odometer_km, dtype: int64



**Observations** column **odometer_km**:<br/>
80% of the cars have more then 100.000 km<br/>
65% of the cars have more then 150.000 km

**Exploration** of column **date_crawled**


```python
autos['date_crawled'].dt.strftime('%Y-%m-%d').value_counts().sort_index()
```




    2016-03-05    1199
    2016-03-06     666
    2016-03-07    1712
    2016-03-08    1568
    2016-03-09    1561
    2016-03-10    1536
    2016-03-11    1554
    2016-03-12    1751
    2016-03-13     741
    2016-03-14    1732
    2016-03-15    1619
    2016-03-16    1394
    2016-03-17    1492
    2016-03-18     608
    2016-03-19    1643
    2016-03-20    1796
    2016-03-21    1772
    2016-03-22    1551
    2016-03-23    1531
    2016-03-24    1388
    2016-03-25    1480
    2016-03-26    1528
    2016-03-27    1475
    2016-03-28    1663
    2016-03-29    1604
    2016-03-30    1605
    2016-03-31    1510
    2016-04-01    1604
    2016-04-02    1691
    2016-04-03    1836
    2016-04-04    1733
    2016-04-05     621
    2016-04-06     150
    2016-04-07      64
    Name: date_crawled, dtype: int64



**Observation** of column **date_crawled**:<br/>
Data is crawled from 5th of March 2016 up to 7th of April 2016<br/>
Each day roughly the same number of data is crawled (even distribution)

Exploration of column **ad_created**:


```python
autos['ad_created'].dt.strftime('%Y-%m').value_counts().sort_index()
```




    2015-06        1
    2015-08        1
    2015-09        1
    2015-11        1
    2015-12        2
    2016-01       12
    2016-02       61
    2016-03    39650
    2016-04     7649
    Name: ad_created, dtype: int64



**Observations** of column **ad_created**:<br/>
Nearly all car advertisements has been created in March and April 2016

**Exploration** of column **last_seen**<br/>


```python
autos['last_seen'].dt.strftime('%Y-%m-%d').value_counts().sort_index()
```




    2016-03-05       50
    2016-03-06      205
    2016-03-07      254
    2016-03-08      339
    2016-03-09      455
    2016-03-10      497
    2016-03-11      584
    2016-03-12     1133
    2016-03-13      422
    2016-03-14      593
    2016-03-15      746
    2016-03-16      774
    2016-03-17     1329
    2016-03-18      343
    2016-03-19      739
    2016-03-20      978
    2016-03-21      971
    2016-03-22     1014
    2016-03-23      874
    2016-03-24      930
    2016-03-25      900
    2016-03-26      789
    2016-03-27      735
    2016-03-28      985
    2016-03-29     1044
    2016-03-30     1165
    2016-03-31     1130
    2016-04-01     1085
    2016-04-02     1175
    2016-04-03     1190
    2016-04-04     1163
    2016-04-05     5953
    2016-04-06    10547
    2016-04-07     6287
    Name: last_seen, dtype: int64



**Observations** of column **last_seen**:<br/>
All car advertisements are last seen from 5th of March 2016 up to 7th of April 2016

**Exploration** of column **registration_year**:


```python
autos['registration_year'].describe()
```




    count    47378.000000
    mean      2004.836126
    std         88.669801
    min       1000.000000
    25%       1999.000000
    50%       2004.000000
    75%       2008.000000
    max       9999.000000
    Name: registration_year, dtype: float64




```python
low_registration_year = autos[autos['registration_year'] < 1900]
```


```python
low_registration_year.shape
```




    (5, 18)




```python
high_registration_year = autos[autos['registration_year'] > 2016]
```


```python
high_registration_year.shape
```




    (1848, 18)




```python
high_registration_year['registration_year'].value_counts().sort_index()
```




    2017    1367
    2018     466
    2019       1
    2800       1
    4100       1
    4500       1
    4800       1
    5000       3
    5911       1
    6200       1
    8888       1
    9000       1
    9999       3
    Name: registration_year, dtype: int64



**Observations** of column **registration_year**
There are some cars with registration year when cars did not exist. Therefore remove all cars with registration year before 1900.<br/>
There are also cars with registration cars far in the future. Because quite a lot of cars are registered between 2017 and 2020, only cars with registration year after 2020 will be removed


```python
autos = autos[(autos['registration_year'] >= 1900) & 
              (autos['registration_year'] <= 2020)]
autos.shape
```




    (47359, 18)




```python
autos['registration_year'].value_counts(normalize=True).sort_index()
```




    1910    0.000042
    1927    0.000021
    1929    0.000021
    1931    0.000021
    1934    0.000042
    1937    0.000084
    1938    0.000021
    1939    0.000021
    1941    0.000042
    1943    0.000021
    1948    0.000021
    1950    0.000021
    1951    0.000042
    1952    0.000021
    1953    0.000021
    1954    0.000042
    1955    0.000042
    1956    0.000084
    1957    0.000042
    1958    0.000084
    1959    0.000127
    1960    0.000422
    1961    0.000127
    1962    0.000084
    1963    0.000169
    1964    0.000253
    1965    0.000359
    1966    0.000465
    1967    0.000549
    1968    0.000549
              ...   
    1990    0.006651
    1991    0.006884
    1992    0.007285
    1993    0.008341
    1994    0.012331
    1995    0.023016
    1996    0.027049
    1997    0.038324
    1998    0.047594
    1999    0.059545
    2000    0.063029
    2001    0.055005
    2002    0.052049
    2003    0.056821
    2004    0.056885
    2005    0.061213
    2006    0.056315
    2007    0.047974
    2008    0.046580
    2009    0.043899
    2010    0.033510
    2011    0.034143
    2012    0.027598
    2013    0.016829
    2014    0.013852
    2015    0.007918
    2016    0.024156
    2017    0.028865
    2018    0.009840
    2019    0.000021
    Name: registration_year, Length: 81, dtype: float64



## Aggregate mean price and mean mileage per brand

Aggregate mean price per brand


```python
brands = autos['brand'].unique()
brand_prices = {}
brand_mileages = {}
price_per_mileage = {}
for brand in brands:
    brand_autos = autos[autos['brand'] == brand]
    brand_prices[brand] = round(brand_autos['price'].mean(), 2)
    brand_mileages[brand] = round(brand_auto['odometer_km'].mean(), 2)
    price_per_mileage[brand] = round(brand_prices[brand] / brand_mileages[brand], 4)
brand_prices = pd.Series(brand_prices) 
brand_mileages = pd.Series(brand_mileages)
price_per_mileage = pd.Series(price_per_mileage)
autos_by_brand = pd.DataFrame(brand_prices, columns=['mean_price'])
autos_by_brand['mean_mileage'] = brand_mileages
autos_by_brand['price/mileage'] = price_per_mileage
```


```python
autos_by_brand['price/mileage'].sort_values()
```




    daewoo            0.0096
    rover             0.0131
    daihatsu          0.0141
    trabant           0.0161
    renault           0.0206
    lada              0.0215
    fiat              0.0239
    opel              0.0250
    peugeot           0.0255
    saab              0.0265
    lancia            0.0268
    mitsubishi        0.0284
    smart             0.0288
    chrysler          0.0289
    citroen           0.0311
    ford              0.0318
    honda             0.0331
    alfa_romeo        0.0335
    mazda             0.0339
    subaru            0.0340
    suzuki            0.0351
    seat              0.0361
    nissan            0.0389
    volvo             0.0401
    toyota            0.0419
    hyundai           0.0444
    volkswagen        0.0444
    dacia             0.0479
    kia               0.0483
    skoda             0.0523
    chevrolet         0.0546
    bmw               0.0678
    mercedes_benz     0.0698
    audi              0.0756
    mini              0.0861
    jeep              0.0942
    jaguar            0.0976
    sonstige_autos    0.1043
    land_rover        0.1539
    porsche           0.3713
    Name: price/mileage, dtype: float64




```python

```
