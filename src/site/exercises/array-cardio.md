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
    console.log(buns.join(" or "));
    
    // We have a string "hot dogs,hamburgers,sausages,corn" - use split() to turn it into a string
    str = "hot dogs,hamburgers,sausages,corn"
    console.log( str.split(","));
    
    // take the last item off toppings with pop() - mutable
    const lastItem = toppings.pop();
    console.log('pop', toppings);
    
    // add it back with push()
    toppings.push(lastItem);
    console.log('push', toppings);
    
    // take the first item off toppings with shift() - mutable
    const firstItem = toppings.shift();
    console.log('shift', toppings);
    
    // add it back in with unshift() - mutable
    toppings.unshift(firstItem);
    console.log('unshift()', toppings);

    // Do the last four,but immutable (with spreads and new variables)
    const newToppings =  [...toppings];
    newToppings.pop();

    console.log('new array from spread', newToppings);
    console.log('original array unchanged', toppings);
    
    // Make a copy of the toppings array with slice()
    toppings.slice(0);
    console.log('new array from slice()', toppings)

    // Make a copy of the toppings array with a spread
    const newToppings2 =  [...toppings];

    // take out items 3 to 5 of your new toppings array with splice() - mutable
    newToppings2.splice(3,5);
    console.log('splice1', newToppings2);

    // find the index of Avocado with indexOf() / lastIndexOf()
    console.log('indexOf("avocado")', toppings.indexOf('Avocado'));
    
    // Check if hot sauce is in the toppings with includes()
    const hasHotSauce = toppings.includes('hot sauce');
    console.log('has hot sauce?', hasHotSauce);
    
    // add it if it's not
    if (!hasHotSauce) {
        toppings.push('Hot Sauce');
        console.log('added hot sauce', toppings);
    }

    // flip those toppings around with reverse() - mutable
    console.log('reverse', toppings.reverse());

    /*
    Callback Methods
    */

    // find the first rating that talks about a burger with find() - immutable
    function findBurger(singleFeedback) {
        return singleFeedback.comment.toLowerCase().includes('burg');
    }
    console.log('structured find', feedback.find(findBurger));
    
    // destructured version
    const findResult = feedback.find( ({comment}) => comment.toLowerCase().includes('burg'));

    console.log('destructured find()', findResult);

    // find all ratings that are above 2 with filter() - immutable
    function ratingsAbove2(feedback) {
        return feedback.rating > 2;
    }
    console.log('filter() ratings less than 2', feedback.filter(ratingsAbove2));

    // destructured version
    const ratingResult = feedback.filter( ({rating}) => rating > 2 );
    console.table('destructured filter()', ratingResult);
    

    // find all ratings that talk about a burger with filter() - immutable
    function burgerFeedback(feedback) {
        return feedback.comment.toLowerCase().includes('burg');
    }
    console.table('filter() burger feedback', feedback.filter(burgerFeedback));

    // destructured version
    const filterResult = feedback.filter( ({comment}) => comment.toLowerCase().includes('burg'));
    console.table('destructured filter() burger feedback', filterResult);
    
    // Remove the one star rating however you like!
    // change original array
    const badRating = feedback.find( ({rating}) => rating < 2 );
    const index = feedback.indexOf(badRating);
    feedback.splice(index);
    console.log('splice() indexOf badRating', feedback);

    // create new array
    const legitRatings = feedback.filter( ({rating}) => rating !== 1 );
    console.table('filter ratings less than 1', legitRatings);


    // check if there is at least 5 of one type of meat with some()
    const isAtLeastFiveOfOneMeat = Object.values(meats).some(meatValue => meatValue >= 5);
    console.log('some() min meat', isAtLeastFiveOfOneMeat); // return true
 
    // make sure we have at least 3 of every meat with every()
    const isAtLeastThreeOfEveryMeat = Object.values(meats).every(meatValue => meatValue >= 3);
    console.log('every() min meat', isAtLeastThreeOfEveryMeat); // return true

    // sort the toppings alphabetically with sort() - mutable
    console.log('sort() strings defaults alphabetically - mutable',toppings.sort());
    
    // sort the order totals from most expensive to least with .sort()
    console.log('sort() numbers - mutable', orderTotals.sort((a, b) => a - b));


    // Sort the prices with sort() and turn back into object 
    const pricesArray = Object.entries(prices).sort(function(a,b) {
        const aPrice = a[1];
        const bPrice = b[1];
        return aPrice - bPrice;
    });
    const sortedPrices = Object.fromEntries(pricesArray);
    console.table('sort() object values by number', sortedPrices );
    


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
