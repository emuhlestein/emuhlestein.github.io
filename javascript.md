---
layout: page
title: Javascript
---
#### Arrow Function
Both of these statements do the same thing.
~~~
square = (x) => { return x * x; };
~~~
or
~~~
square = x => x * x;
~~~
#### Closure

wrapValue creates a local binding (a local variable). It them passes back a function that returns the local binding. This is called closure.  

A function that references a local binding is called a closure.
~~~
function wrapValue(n) {
  let local = n;
  return () => local;
}

let wrap1 = wrapValue(1);
console.log(wrap1());
// -> 1
~~~

#### Arrays

```
var cars1 = [ "Mustang", "Corvette", "Charger" ]; // create an array of strings
var cars2 = new Array( "Mustang", "Corvette", "Charger" ); // create an array of strings
```
Both of the above statements do the same thing. The first one is preffered.

```
var car = cars1[0]; // grab the first element of the array
```

##### Methods
cars1.length;
cars1.sort(); // sorts an array alphabetically
cars1.reverse(); // reverse sort
To sort numbers:
var nums = [1,60,45,70,2,100];
nums.sort(function(a,b) {return a - b});
//This is a compare function
function(a,b) {return a - b}

cars.forEach(<function>);
cars.push("Camry"); // adding a new element to an array
Can also add elements like this:
cars[5] = "Malibu"; // this is not a good way as it could leave holes in the array if the index is too large
  
#### Difference between arrays and objects
Arrays use numbered indexes.
Objects use named indexes.

Creating empty array:
var points = new Array(); // Bad
var points = []; // Good

An arrays is an object.

var fruits = ["Banana", "Orange", "Apple", "Cherry"];
fruits.toString(); // converts array into a string of comma-separated array values.
"Banana,Orange,Apple,Cherry"

fruits.join(" * "); // converts array into a string of all elements separated by ' * '.
fruits.pop(); // removes last item from array
fruits.push("Peach"); // add item onto end of array
fruits.shift(); // removes the first element
fruits.unshift(); // adds item to start of array and shifts other items

delete fruits[0]; // legal but bad; leaves first element undefined

fruits.splice(1,2); // remove one element from position 1-remove items beginning at position 1 and up until, but not including position 2.
fruits.splice(0,1); // remove the first element
fruits.splice(2, 0 , "Lemon", "Strawberry"); // add (splice) in elements at position 2. These are the elements listed. Remove 0 elements.

var boys = ['Ed', 'Jim', 'Fred'];
var girls = ['Bobi', 'Julie'];
var kids = boys.concat(girls); // combine 2 arrays

Can also merge arrays with values:

var kids = boys.concat(['Bobi', 'Julie']);


