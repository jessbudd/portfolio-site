---
title: Nothin' to see here folks!
layout: layouts/blank.njk
date: 2020-12-19
meta: practice makes progress
# tags: exercises
# img: https://jessbudd.com/images/featured/quoteGenerator.png
# excerpt:
---

<h1>{{title}}</h1>

<script>
    const toppings = [
        "Mushrooms ",
        "Tomatoes",
        "Eggs",
        "Chili",
        "Lettuce",
        "Avocado",
        "Chiles",
        "Bacon",
        "Pickles",
        "Onions",
        "Cheese",
    ];

    const buns = ["egg", "wonder", "brioche"];

    const meats = {
        beyond: 10,
        beef: 5,
        pork: 7,
    };

    const prices = {
        hotDog: 453,
        burger: 765,
        sausage: 634,
        corn: 234,
    };

    const orderTotals = [342, 1002, 523, 34, 634, 854, 1644, 2222];

    const feedback = [
        { comment: "Love the burgs", rating: 4 },
        { comment: "Horrible Service", rating: 2 },
        { comment: "Smoothies are great, liked the burger too", rating: 5 },
        { comment: "Ambiance needs work", rating: 3 },
        { comment: "I DONT LIKE BURGERS", rating: 1 },
    ];

    /*
    Static Methods
    */

    // Array.of();
    Array.of('Jess'); // returns ['Jess']
    Array.of(...'Jess'); // returns ['J','e','s','s']

    // Make a function that creates a range from x to y with Array.from();
    function createRange(start, end) {
    const range = Array.from(
        { length: end - start + 1 },
        function (_item, index) {
        return index + start;
        }
    );
    return range;
    }
    console.log(createRange(5, 7));

    // Check if the last array you created is really an array with Array.isArray();
    const range = createRange(4,6); // returns [4,5,6]
    console.log(Array.isArray(range)); // returns true

    // Take the meats object and make three arrays with Object.entries(), Object.keys, Object.values()
    console.log(Object.entries(meats)); // returns array of arrays (each object being its own array)
    console.log(Object.keys(meats)); // returns array of all keys in the object
    console.log(Object.values(meats)); // returns array of all values in the object
    console.log('');
    
    
    /*
    Instance Methods
    */
    // Display all bun types with " or " - use join()
    // We have a string "hot dogs,hamburgers,sausages,corn" - use split() to turn it into a string
    // take the last item off toppings with pop()
    // add it back with push()
    // take the first item off toppings with shift()
    // add it back in with unshift()
    // Do the last four,but immutable (with spreads and new variables)
    // Make a copy of the toppings array with slice()
    // Make a copy of the toppings array with a spread
    // take out items 3 to 5 of your new toppings array with splice()
    // find the index of Avocado with indexOf() / lastIndexOf()
    // Check if hot sauce is in the toppings with includes()
    // add it if it's not
    // flip those toppings around with reverse()
    /*
    Callback Methods
    */
    // find the first rating that talks about a burger with find()
    // find all ratings that are above 2 with filter()
    // find all ratings that talk about a burger with filter()
    // Remove the one star rating however you like!
    // check if there is at least 5 of one type of meat with some()
    // make sure we have at least 3 of every meat with every()
    // sort the toppings alphabetically with sort()
    // sort the order totals from most expensive to least with .sort()
    // Sort the prices with sort()  
    /*
    Looping Methods (next)
    */
</script>
<style>
body {
    min-height: 100vh;
    display: grid;
    align-items: center;
    justify-items: center;
}
.container {
  text-align: center;
  margin: 20% auto;
}

</style>
