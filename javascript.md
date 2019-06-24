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
