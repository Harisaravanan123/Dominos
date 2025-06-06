# Dominos - Predictive purchase order system
# Problem Statement:
* Dominos wants to optimize the process of ordering ingredients by predicting future sales and creating a purchase order. By accurately forecasting sales, Dominos can ensure that it has the right amount of ingredients in stock, minimizing waste and preventing stockouts. This project aims to leverage historical sales data and ingredient information to develop a predictive model and generate an efficient purchase order system.

# Preprocessing:
* I impute the null values in the column by using the groupby function with the highly influenced column to the null value column.
* I changed the datatype from object to datetime in my order date column.
* I convert the dataframe into 91 different dataframe, which represents the pizza name and store it in the dictionary to predict the weekly sales by the pizza name.

# Feature Engineering:
* I changed the datetime format in the order date columns.   
* I extracted the day name, week of the year, month from the order date column.
* I took the holiday of the United states by using the holidays library to see the influence of the holidays in the sales.

# Stationarity:
* I used ADFULLER test and KPSS test to check the data is stationary or not.
* In ADFULLER test, the p-value is less than 0.05 and in KPSS test the p-value is greater than 0.05, By that we assumed that the data is stationary.

# Model Training and Evaluation:
* I used ARIMA[AUTO REGRESSIVE INTEGRATED MOVING AVERAGE] Model to fit and predict the sales quantity of a week and store in the dictionary for future creation of purchase order.
* I used MAPE[MEAN ABSOLUTE PERCENTAGE ERROR] to evaluate my model.

# purchase order creation:
* After fitting the model, I predict the future sales for the next week and save it in the form  of dictionary for future use.
* After that I create a column called future sales quantity by using the predicted sales and the ingredient quantity. 
* Then I create the purchase order for next week for  all the total ingredients .
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
      <th>pizza_ingredients</th>
      <th>future_quantity(kg)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>?duja Salami</td>
      <td>0.79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alfredo Sauce</td>
      <td>0.30</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Anchovies</td>
      <td>0.80</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Artichokes</td>
      <td>2.40</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Arugula</td>
      <td>0.28</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Asiago Cheese</td>
      <td>1.36</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Bacon</td>
      <td>9.47</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Barbecue Sauce</td>
      <td>0.51</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Barbecued Chicken</td>
      <td>1.47</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Beef Chuck Roast</td>
      <td>3.06</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Blue Cheese</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Brie Carre Cheese</td>
      <td>0.28</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Calabrese Salami</td>
      <td>3.78</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Capocollo</td>
      <td>14.73</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Caramelized Onions</td>
      <td>0.18</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Chicken</td>
      <td>18.38</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Chipotle Sauce</td>
      <td>1.51</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Chorizo Sausage</td>
      <td>1.81</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Cilantro</td>
      <td>0.76</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Coarse Sicilian Salami</td>
      <td>2.83</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Corn</td>
      <td>5.06</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Eggplant</td>
      <td>0.70</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Feta Cheese</td>
      <td>2.57</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Fontina Cheese</td>
      <td>1.36</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Friggitello Peppers</td>
      <td>0.20</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Garlic</td>
      <td>5.83</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Genoa Salami</td>
      <td>1.85</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Goat Cheese</td>
      <td>3.15</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Gorgonzola Piccante Cheese</td>
      <td>1.32</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Gouda Cheese</td>
      <td>0.98</td>
    </tr>
    <tr>
      <th>30</th>
      <td>Green Olives</td>
      <td>1.16</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Green Peppers</td>
      <td>1.79</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Italian Sausage</td>
      <td>0.36</td>
    </tr>
    <tr>
      <th>33</th>
      <td>Jalapeno Peppers</td>
      <td>1.24</td>
    </tr>
    <tr>
      <th>34</th>
      <td>Kalamata Olives</td>
      <td>0.80</td>
    </tr>
    <tr>
      <th>35</th>
      <td>Luganega Sausage</td>
      <td>1.41</td>
    </tr>
    <tr>
      <th>36</th>
      <td>Mozzarella Cheese</td>
      <td>4.10</td>
    </tr>
    <tr>
      <th>37</th>
      <td>Mushrooms</td>
      <td>6.94</td>
    </tr>
    <tr>
      <th>38</th>
      <td>Onions</td>
      <td>0.71</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Oregano</td>
      <td>0.36</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Pancetta</td>
      <td>1.18</td>
    </tr>
    <tr>
      <th>41</th>
      <td>Parmigiano Reggiano Cheese</td>
      <td>3.12</td>
    </tr>
    <tr>
      <th>42</th>
      <td>Pears</td>
      <td>0.09</td>
    </tr>
    <tr>
      <th>43</th>
      <td>Peperoncini verdi</td>
      <td>0.43</td>
    </tr>
    <tr>
      <th>44</th>
      <td>Pepperoni</td>
      <td>8.23</td>
    </tr>
    <tr>
      <th>45</th>
      <td>Pesto Sauce</td>
      <td>1.03</td>
    </tr>
    <tr>
      <th>46</th>
      <td>Pineapple</td>
      <td>3.05</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Plum Tomatoes</td>
      <td>0.87</td>
    </tr>
    <tr>
      <th>48</th>
      <td>Prosciutto</td>
      <td>0.28</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Prosciutto di San Daniele</td>
      <td>0.64</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Provolone Cheese</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Red Onions</td>
      <td>16.32</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Red Peppers</td>
      <td>3.42</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Ricotta Cheese</td>
      <td>1.64</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Romano Cheese</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Sliced Ham</td>
      <td>1.40</td>
    </tr>
    <tr>
      <th>56</th>
      <td>Smoked Gouda Cheese</td>
      <td>0.63</td>
    </tr>
    <tr>
      <th>57</th>
      <td>Soppressata Salami</td>
      <td>1.93</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Spinach</td>
      <td>5.67</td>
    </tr>
    <tr>
      <th>59</th>
      <td>Sun-dried Tomatoes</td>
      <td>0.36</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Thai Sweet Chilli Sauce</td>
      <td>1.07</td>
    </tr>
    <tr>
      <th>61</th>
      <td>Thyme</td>
      <td>0.05</td>
    </tr>
    <tr>
      <th>62</th>
      <td>Tomatoes</td>
      <td>11.23</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Zucchini</td>
      <td>0.88</td>
    </tr>
  </tbody>
</table>
</div>







