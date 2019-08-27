```javascript
function fixCurry(fn, totalArgs){
  totalArgs = totalArgs || fn.length
    return function recursor(){
      return arguments.length < totalArgs
        ? recursor.bind2(this, ...arguments)
        : fn.call(this, ...arguments);
    }
}

const add6 = fixCurry((a, b, c) => a + b + c);
add1(2)(3)(4) //output: 9
add(2, 3, 4) //output: 9
add(2)(3, 4) //output: 9
add(2, 3)(4) //output: 9
```

```javascript
  Function.prototype.bind2 = function(context) {
    const self = context;
    const fn = this;
    const args = Array.prototype.slice.call(arguments, 1)
    return function() {
      const newArgs = args.concat(Array.prototype.slice.call(arguments))
      return fn.apply(self, newArgs);
    }
  }
```

```javascript
function add(x) {
  let sum  = x;

  return function variableSum(y) {
    if (arguments.length) {
      sum += y;
      return variableSum;
    } else {
      return sum;
    }
  }
}


add(2)(3)() //output: 5
const t = add(3)(4)(5)
t() //output: 12
```

```javascript
/**
 * You pass a function and a delay to be be debouced to the debounce function. You get
 * back debounced function, that  gets called and if it receives a call before the delay again
 * that call is ignored and the next call is accepeted after the delay and so on.
 *
 * Execute this function only if 100 milliseconds have passed without it being called.”
 * */
const debounce = function(fn, delay) {
  let timer;
  return function(...args) {
  const self = this;
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(self, ...args), delay);
  }
}

```

```javascript
  /**
   * We pass a function to e throttled and an interval at which
   * frequency the throttled function should be invoked. So if there is trigger
   * happening multiple times within the interval invoke it only once once.
   * ex: clicking of button to join a competetion(Restrict the user to limit the clicks
   * on the button for a minute i.e dont make api call within a minute.
   *
   * “Execute this function at most once every 100 milliseconds.”
   * */

const throttle = (fn, interval) {
  let timer = true;

  return function() {
    const self = this;
    if (timer) {
      fn.apply(self, Array.prototype.slice.call(arguments));
      timer = false;
      setTimeout(() => timer = true, interval);
    }
  }
}

```

```javascript
/**
 * Flattent a deep nested array: recursively and iteratively
 * */

const flatten = (array) => {
  if (!Array.isArray(array)) {
    return array;
  }

  let flattenedArray = [];
  for (let i = 0; i < array.length; i ++ ) {
    flattenedArray = flattenedArray.concat(flatten(array[i]));
  }

  return flattenedArray;
}

const flatten = arr => {
  var flattenedArray = [];
  while(arr.length) {
    var value = arr.shift();
    if(Array.isArray(value)) {
      arr = value.concat(arr);
    } else {
      array.push(value);
    }
  }
  return flattenedArray;
}

flatten([1,[2,[3]],[4]]); // => [1,2,3,4]

```

