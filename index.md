---
layout: home
---

<img src="assets/meat_consumer.jpg" style="width:925px;height:373;">

## Introduction

Meat consumption is a highly controversial topic in nowadays society in terms of environment, health, and ethical reasons. This situation introduces different ways of consuming meat and divides people according to their behaviors such as vegan, vegetarian, occasional meat consumer, and people consuming large amounts of meats. In this story, we will be telling you the tale about the consumption behavior of meat and vegetables. If you are intersted in learning what are the factors influencing meat consumption or how does meat consumption influence other aspects of our alimentation this story is for you.

## The Data

To tell our story, we will be using data collected over 2 years from frequent shoppers in the USA. It contains information about grocery shopping of 2500 households and the demographic information of 800 of them. We will be particularly focusing on 51,000 food products and their 2.1 million transactions.


<section id="key_numbers_data" markdown="1">

<div class="card-deck" style="margin-bottom:2em;">
  <div class="card">
    <div class="card-body"  style="text-align: center;">
      <h5 class="card-title">2,1M</h5>
      <p class="card-text" style="text-align: center;">Transactions</p>
    </div>
  </div>
  <div class="card">
    <div class="card-body"  style="text-align: center;">
      <h5 class="card-title">2,5K</h5>
      <p class="card-text" style="text-align: center;">Houselholds</p>
    </div>
  </div>
  <div class="card">
    <div class="card-body"  style="text-align: center;">
      <h5 class="card-title">51K</h5>
      <p class="card-text" style="text-align: center;">Food products</p>
    </div>
  </div>
</div>

</section>


<!-- For our analysis, we use the Dunnhumby dataset. It contains information about grocery shopping of 2500 households with the demographic information of 800 of them. We will be particularly focusing on 51,000 food products and 2.1 million transactions. -->

Among all food-related transactions, 16% of them are products containing meat (seafood products are considered as a type of meat). As a comparison, when looking at vegetables this number drop to 10%.


![](/assets/waffle_food_trans.svg)

Among these meat products transactions, 40% of them are for poducts containing meat (eg. meat sandwiches, bolognes, ...), 36% are transactions related to red meat and 17% to white meat. We observe less seafood consumption which consists of only 7% of the transactions of meat products.

![](/assets/waffle_meat_trans.svg)

## Time Analysis

Does our consumption of meat and vegeatable vary accorss the year?  This is the first question we will try to answer. To do so, let's look  at the number tansactions over the year for different type of food.

{% include monthly_meat.html %}

<section id="legend" markdown="1">
<p style="font-size: 0.8em;"><em>*The graph above normalizes the total number of transactions of each category to 12 so that the expected score per month is 1.</em></p>
</section>

Our monthly consumption of vegetables, red and white meat stays pretty much constant. However, we can observe interesting variations for certain types of foods. 

For example, we have a peak for turkey on Thanksgiving and pumpkin in Halloween. Moreover, people seems to buy more seafood during the winter. 

Thus, preferences of people change seasonally or weekly (due to the special days) for some specific products but time does not seems to affect their meat and vegetable consumption in general.

## Demographic Factors

If time does not influence our consumption of meat and vegeatable, what does? 
Some people might think that men consume more meat than women so let's look at the consumption  of theses 2 groups.

{% include gender.html %}

As we can see from the figure above, women and men tend to spent very similar amount on all type of meat. Women spend slighlty more than men on vegetable.  

Let's now look at 2 others factors: age and income. 

<section id="sliders" markdown="1">
  <div class="container">
    <div class="row">
      <div class="col-sm">
        {% include slider_age_small.html %}
      </div>
      <div class="col-sm">
        {% include slider_income_small.html %}
      </div>
    </div>
  </div>
</section>

The ratio of spending on red meat and vegetables tends to increase with age. In contrast, we observe a decreasing trend when looking at white meat. In terms of income, richer people spend less portion of their money on meat and products containing meat. People in the highest income category spend a higher  portion of their money on seafood products.

<div class="row">
  <div class="col-sm"></div>
  <div class="col-sm">
    <div class="btn-group" role="group" aria-label="Basic example" style="margin-top: 2em;">
      <button type="button" id="redmeat" class="btn btn-outline-dark active" onclick="redMeat()">Red Meat</button>
      <button type="button" id="whitemeat" class="btn btn-outline-dark" onclick="whiteMeat()">White Meat</button>
      <button type="button" id="seafood" class="btn btn-outline-dark" onclick="seafood()">Seafood</button>
      <button type="button" id="vegetables" class="btn btn-outline-dark" onclick="vegetables()">Vegetables</button>
    </div>
  </div>
  <div class="col-sm"></div>
</div>

<div class="row">
  <div class="col-sm"></div>
  <div class="col-sm">
     <img id="heatmap" src="assets/redmeat_HM.svg" style="margin-bottom:2em;">
  </div>
  <div class="col-sm"></div>
</div>

<script>
var selected = "redmeat"

function redMeat(){
document.getElementById(selected).classList.remove("active");
selected = "redmeat"
document.getElementById("heatmap").src="assets/redmeat_HM.svg";
document.getElementById(selected).classList.add("active");

}
function whiteMeat(){
document.getElementById(selected).classList.remove("active");
selected = "whitemeat"
document.getElementById("heatmap").src="assets/whiteMeat_HM.svg";
document.getElementById(selected).classList.add("active");

}
function seafood(){
document.getElementById(selected).classList.remove("active");
selected = "seafood"
document.getElementById("heatmap").src="assets/seafood_HM.svg";
document.getElementById(selected).classList.add("active");

}
function vegetables(){
document.getElementById(selected).classList.remove("active");
selected = "vegetables"
document.getElementById("heatmap").src="assets/vegetables_HM.svg";
document.getElementById(selected).classList.add("active");
}
</script>

## Group Comparison

We are now going to take a closer look at certain extreme groups of people and see which products are popular for them! We are specifically interested in three different comparisons. The first comparison is extreme meat consumers vs extreme vegetable consumers. Then, we compare people aged between 19-35 and above 55. Finally, we look at households with an income under 50K and above 100K. 

<div class="row">
  <div class="col-sm"></div>
  <div class="col-sm">
    <div class="btn-group" role="group" aria-label="Basic example" style="margin: 1em;">
      <button type="button" id="extreme" class="btn btn-outline-dark active" onclick="update('extreme_div')">Extreme Consumers</button>
      <button type="button" id="youngold" class="btn btn-outline-dark" onclick="update('youngold_div')">Young vs Old</button>
      <button type="button" id="poorich" class="btn btn-outline-dark" onclick="update('poorrich_div')">Lowest vs Highest Income</button>
    </div>
  </div>
  <div class="col-sm"></div>
</div>

<div id="extreme_div">

  <h3>Extreme Consumers</h3>

  <p>We select, among all the households, the 5% that spent the biggest part of their food spendings on meat. These people are categorized as "extreme meat consumers". 
  We apply the same selection strategy to obtain the "extreme vegetable consumers".</p>

  <p>We look at the popular words in the description of the products consumed by those groups. Red and green words represent extreme meat and extreme vegetable consumers respectively.</p>


  <img id="wordCloudBMvsBV" src="assets/BM_vs_BV.png" style="width:925px;height:219px; margin-bottom:4em;">

  <p>Extreme meat consumers spend most of their money on meat and meat-related products like beef, wings ribs, primal cuts, etc... They also prefer unhealthy products like chips. Thus, their diet is protein-heavy and lack of other nutrients. In contrast, we observe a much more balanced diet in extreme vegetable consumers. They consume largely fresh products, fruits vegetables and also they consume beef, turkey, milk, and cheese as a protein source.</p>

  {% include meat_extremeMeatVSextremeVeggies.html %}

  <p>Looking specifically at meat spendings, we see that extreme meat consumers spend most of their money on bovine meat (31%) followed by poultry and pork (both 24%).</p>

  <p>On the other hand, extreme vegetable consumers spend most of their money to buy poultry (32%) followed by bovine meat (24%) and pork (19%). They also spend more money on seafood compare to extreme meat consumers (15% vs 10%).</p>

  {% include commodities_extremes.html %}

</div>

<div id="youngold_div">

  <h3>Young vs Old</h3>

  <p>We select, among all the households, the 5% that spent the biggest part of their food spendings on meat. These people are categorized as "extreme meat consumers". We apply the same selection strategy to obtain the "extreme vegetable consumers".</p>

  <p>We look at the popular words in the description of the products consumed by those groups. Blue and brown words represent young and brown consumers respectively.</p>

  <img id="wordCloud" src="assets/O_vs_Y.png" style="width:925px;height:219px; margin-bottom:4em;">

  <p>Although old and young people have similar preferences in general, old people tend to consume have a more balanced diet where they consume more fruit, juice, salad compared to chips and snacks.</p>

  
  {% include meat_youngestVSoldest.html %}
  

  <p>Looking specifically at meat spendings, we see that heavy meat buyers prefer to buy bovine meat (33%) followed by pork (24%) and poultry (21%). On the other hand, heavy vegetable buyers prefer to buy poultry (32%) followed by bovine meat (27%) and pork (19%).</p>

</div>

<div id="poorrich_div">

  <h3>Lowest vs Highest Income</h3>

  <p>We select, among all the households, the 5% that spent the biggest part of their food spendings on meat. These people are categorized as "extreme meat consumers". We apply the same selection strategy to obtain the "extreme vegetable consumers".</p>

  <p>We look at the popular words in the description of the products consumed by those groups. Dark-brwon and yellow words represent lowest and highest income consumers respectively.</p>

  <img id="wordCloud" src="assets/R_vs_P.png" style="width:925px;height:219px; margin-bottom:4em;">

  <p>In terms of income, people with lower income prefer to spend most of their money on meat and meat-related products whereas people with higher income spend their money more luxury products like wines, expensive cereals, and fruits.</p>

  {% include meat_lowestVShighest_income.html %}

  

  <p>Looking specifically at meat spendings, we see that heavy meat buyers prefer to buy bovine meat (33%) followed by pork (24%) and poultry (21%). On the other hand, heavy vegetable buyers prefer to buy poultry (32%) followed by bovine meat (27%) and pork (19%).</p>

</div>


<script>

  document.getElementById("youngold_div").style.display = 'none';
  document.getElementById("poorrich_div").style.display = 'none';





  var active = "extreme"

  function update(arg){

    document.getElementById(active).classList.remove("active");

    if (arg == "extreme_div") {
      document.getElementById("youngold_div").style.display = 'none';
      document.getElementById("poorrich_div").style.display = 'none';
      document.getElementById("extreme_div").style.display = 'block';
      

      document.getElementById("extreme").classList.add("active");
      active = "extreme";

    }
    else if (arg == "youngold_div") {
      document.getElementById("youngold_div").style.display = 'block';
      document.getElementById("poorrich_div").style.display = 'none';
      document.getElementById("extreme_div").style.display = 'none';

      document.getElementById("youngold").classList.add("active");
      active = "youngold";
    }
    else if (arg == "poorrich_div") {
      document.getElementById("youngold_div").style.display = 'none';
      document.getElementById("poorrich_div").style.display = 'block';
      document.getElementById("extreme_div").style.display = 'none';

      document.getElementById("poorich").classList.add("active");
      active = "poorich";
    }

  }

</script>




## Notes
p-values are provided for equality of means via ANOVA test with a 95% confidence interval. 

All the error bars are computed using 95% confidence interval. 

