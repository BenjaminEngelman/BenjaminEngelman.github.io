---
layout: home
---

<img src="assets/meat_consumer.jpg" style="width:925px;height:373;">

## Introduction

Meat consumption is a highly controversial topic in nowadays society in terms of environment, health, and ethical reasons. This situation introduces different ways of consuming meat and divides people according to their behaviors such as vegan, vegetarian, occasional meat consumer, and people consuming large amounts of meats. In this post, we will be telling you the tale about the consumption behavior of meat and vegetables that we learned from the grocery shoppings of households over two years.

## Dataset
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
      <h5 class="card-title">2500</h5>
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

For our analysis, we use the Dunnhumby dataset. It contains information about grocery shopping of 2500 households with the demographic information of 800 of them. We will be particularly focusing on 51,000 food products and 2.1 million transactions.

![](/assets/waffle.svg)

Among all food-related transactions, 10% of them are vegetables and 16% of them are products contain meat. Among those which contain meat, 36% and 17% of them are red and white meat respectively. We observe less seafood consumption which consists of 7% of the products with meat.

## Time Analysis

{% include monthly_meat.html %}

<section id="legend" markdown="1">
<p style="font-size: 0.8em;"><em>*The graph above normalizes the total number of transactions of each category to 12 so that the expected score per month is 1.</em></p>
</section>

Monthly consumption of vegetables and red and white meat does not vary however, we observe interesting variations for certain types of foods. For example, we have a peak for turkey on Thanksgiving and pumpkin in Halloween. Moreover, we observe some seasonal peaks with certain products such as seafood. Thus, preferences of people change seasonally or weekly (due to the special days) however it does not affect their meat and vegetable consumption in general.

## Demographic

{% include gender.html %}

Among individuals, women  and men have very similar meat and vegetable consumptions.

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

The ratio of spending on red meat (p=0.001) and vegetables (p=0.02) tends to increase with age. In contrast, we observe a decreasing trend in white meat (p=0.003). In terms of income, richer people spend less portion of their money on meat (p=0.001) and products contain meat (p=0.001). Although we do not observe any statistical significance in vegetables, red, and white meat, we observe that people in the richest category spend more portion of their money on sea products (p=0.001).

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
     <img id="heatmap" src="assets/redmeat_HM.svg" style="margin-bottom:3em;">
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

Let's take a closer look at certain extreme groups of people and see which products are popular for them! We are specifically interested in three different comparisons. The first comparison is extreme meat consumers vs extreme vegetable consumers. Then, we compare people aged between 19-35 and above 55. Finally, we look at households with an income under 50K and above 100K. 

<div class="row">
  <div class="col-sm"></div>
  <div class="col-sm">
    <div class="btn-group" role="group" aria-label="Basic example" style="margin: 1em;">
      <button type="button" id="extreme" class="btn btn-outline-dark active" onclick="extreme()">Extreme Consumers</button>
      <button type="button" id="youngold" class="btn btn-outline-dark" onclick="youngOld()">Young vs Old</button>
      <button type="button" id="poorich" class="btn btn-outline-dark" onclick="poorRich()">Poor vs Rich</button>
    </div>
  </div>
  <div class="col-sm"></div>
</div>


<img id="wordCloud" src="assets/BM_vs_BV.png" style="width:925px;height:219px; margin-bottom:4em;">

<script>
var selected2 = "extreme"
function extreme(){
document.getElementById(selected2).classList.remove("active");
selected2 = "extreme"
document.getElementById("wordCloud").src="assets/BM_vs_BV.png";
document.getElementById(selected2).classList.add("active");


}
function youngOld(){
document.getElementById(selected2).classList.remove("active");
selected2 = "youngold"
document.getElementById("wordCloud").src="assets/O_vs_Y.png";
document.getElementById(selected2).classList.add("active");
}
function poorRich(){
document.getElementById(selected2).classList.remove("active");
selected2 = "poorich"
document.getElementById("wordCloud").src="assets/R_vs_P.png";
document.getElementById(selected2).classList.add("active");
}
</script>

Extreme meat consumers spend most of their money on meat and meat-related products like beef, wings ribs, primal cuts, etc. and they prefer unhealthy products like chips. Thus, their diet is protein-heavy and lack of other nutrients. In contrast, we observe a much more balanced diet in extreme vegetable consumers. They consume largely fresh products, fruits vegetables and also they consume beef, turkey, milk, and cheese as a protein source.

Although old and young people have similar preferences in general, old people tend to consume have a more balanced diet where they consume more fruit, juice, salad compared to chips and snacks.

In terms of income, people with lower income prefer to spend most of their money on meat and meat-related products whereas people with higher income spend their money more luxury products like wines, expensive cereals, and fruits.


## Conclusion

I love potatoes.

## Notes
p-values are provided for equality of means via ANOVA test with a 95% confidence interval. 

All the error bars are computed using 95% confidence interval. 

