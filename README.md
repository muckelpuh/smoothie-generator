<!-- This is the markdown template for the final project of the Building AI course, 
created by Reaktor Innovations and University of Helsinki. 
Copy the template, paste it to your GitHub README and edit! -->

# The Smoothie Generator

My final project for the Building AI course: The Smoothie Generator

## Summary

Each of us knows the problem. The fridge is full of fruits and vegetables, but you don't know what to do with them. The Smoothie Generator can help here. After entering the available fruits and vegetables, the Smoothie Generator generates a list of possible smoothies with the aim of throwing away as little as possible.


## Background

Food wastage is a big problem in the world. While many people do not have enough food, people in the large industrialized nations throw away a lot of food (e.g. 75kg in Germany). At the same time, we all live unhealthily today, move too little and don't eat healthily.

The Smoothie Generator aims to solve two of the three problems:
* Less food should be thrown away with the aim of making smoothies from leftover food.
* The smoothies also contribute to a healthier diet.

However, the user has to work on the lack of movement himself.


## How is it used?

The Smoothie Generator is based on the "Django" web framework on the server side. All ingredients available in the household can be entered into a dynamic list. The entered data is sent via AJAX to an interface programmed in Python, which carries out the necessary operations and returns the corresponding recipes.

There are two user roles:
* Viewer: Viewers can enter ingredients and get recipes based on that.
* Editor: Editors can also set their own recipes and make ratings (from 1 to 5 stars).

## Data sources and AI methods

Users with the "Editor" role serve as the data source. These enter the required recipes. Note that, by definition, a recipe can contain n ingredients. The entered recipes and ingredients are sanitized and stored in a database (either SQL or NoSQL database).

The Manhattan metric is used to determine the best fitting recipe. When the user enters a set of ingredients and sends an AJAX request to the server, the Python-written interface checks for the discrepancies.

Here's an example:

* User input: apple, banana, carrot, orange, pear, strawberry

| Typ         | Ingredient 1 | Ingredient 2 | Ingredient 3 | Ingredient 4 |
| ----------- | ------------ | ------------ |------------ |------------ |
| Recipe 1    | apple        | banana | carrot | orange
| Recipe 2    | pear        | Brokolli | carrot | lemon
| Recipe 3    | raspberry     | strawberry | blueberry | 

Using the Manhattan metric, we see that all the ingredients for Recipe 1 are present.


## Challenges

One challenge is that no units are taken into account in the first step. If there is only one apple in the fridge, but two apples are needed, the algorithm does not yet work. The metric would have to be expanded here.

## What next?

The Smoothie Generator can be expanded and also offer sports programs at the same time. The user can enter which muscles he wants to train with which goal. Based on the Manhattan metric, the most suitable programs could then also be suggested for the user. Of course, the title Smoothie Generator would then no longer be correct :-)

