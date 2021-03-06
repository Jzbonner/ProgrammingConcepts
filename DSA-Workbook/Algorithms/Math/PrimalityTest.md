## Primality Test
A *prime number* is a positive integer `p > 1`, that has no positive integer divisors other than 1 and *p* itself. For example, the only divisors of 13 are 1 and 13, making 13 a prime number. Positive integers other than 1 which are not prime are known as *composite numbers*. 

A **primality test** is a test to determine whether or not a given number is prime, as opposed to actually decomposing the number into its constituent prime factors (which is known as **prime factorization**). Primality test come in two varieties: *deterministic and probabilistic*. Deterministic test determine with absolute certainty whether a number is prime or not. Probabilistic test can potentially falsely identify a composite number as prime, however they are much faster than deterministic test. Numbers that pass a probabilistic test are referred to as *probable primes* until their primality can be demonstrated deterministically.   

### Implementation 
You can implement a Primality Test in JavaScript in a number of ways. A simple solution would invoke the use of an arrow function to check whether the input parameter is divisible by all the natural numbers less than the value of the `num` variable, and if so return false. Otherwise return the value of the `num` variable, an eloquent solution to the primality test would go as follows: 

```javascript 
const isPrime = num => {
  for(let i = 2; i < num; i++)
    if(num % i === 0) return false;
  return num > 1;
}
```

You can decrease the complexity of the algorithm from `O(n)` to `O(sqrt(n))` by iterating the loop until the square root of the input parameter: 

```javascript 
const isPrime = num => {
    for(let i = 2, s = Math.sqrt(num); i <= s; i++)
        if(num % i === 0) return false; 
    return num > 1;
}
```

![Diagram1](https://github.com/Jzbonner/ProgrammingConcepts/blob/master/img-media/primality.jpeg?raw=true)

#### Implentation from [PolyGot Developer](https://www.thepolyglotdeveloper.com/2015/04/determine-if-a-number-is-prime-using-javascript/) 
The logic behind constructing a primality test is as follows: 
1. Create an array from two until the value and assign a value of true since we are going to assume everything is prime to start.
2. Take the square root of our desired value which will represent a limit to our looping.
3. Loop from two until our new square rooted limit.
4. Check to see if our current index is prime, otherwise ignore it.
5. Loop through (i * i) + ix until our initial value where x is incremental starting from value one.
6. Set every index hit to false because it is no longer a prime number.

```javascript 
function printPrime(value) {
    var primes = [];
    for(var i = 2; i < value; i++) {
        primes[i] = true;
    }
    var limit = Math.sqrt(value);
    for(var i = 2; i < limit; i++) {
        if(primes[i] === true) {
            for(var j = i * i; j < value; j += i) {
                primes[j] = false;
            }
        }
    }
    for(var i = 2; i < value; i++) {
        if(primes[i] === true) {
            console.log(i + " " + primes[i]);
        }
    }
}
```