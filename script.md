# 1 - Recursion

## introduction:

- recursion is when a function calls itself to execute something repeatedly
- it can be used to replace all the loop operators, like for loops
- it is used mainly when following `functional programming` and, especially in javascript should not be abused
- it is a very useful tool, for some use cases, and it will come up in most job interviews

## examples:

### 1 - factorial

#### Looping:

```javascript
window.factorial = function (val) {
  let result = 1
  for (let i = val; i >= 1; i--) {
    result = result * i
  }
  return result
}
```

#### Recursion:

```javascript
window.factorial = function (val) {
  if (val < 1) {
    return 1
  }
  return val * factorial(val - 1)
}
```

### 02 - Prime Numbers

- this was an interview question
- Primes: [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]

#### looping

```javascript
window.isPrime = function (val) {
  for (let i = 2; i <= Math.sqrt(val); i++) {
    if (val % i === 0) {
      return false
    }
  }
  return val > 1
}

window.primes = function (limit) {
  const primes = []
  for (let i = 2; i <= limit; i++) {
    if (isPrime(i)) {
      primes.push(i)
    }
  }
  return primes
}
```

#### Recursion

```javascript
window.isPrime = function (val, divisor = val) {
  if (divisor === 2) {
    return val > 1
  }
  return val % (divisor - 1) !== 0 && isPrime(val, divisor - 1)
}

window.primes = function (limit, arr = []) {
  if (limit < 2) {
    return arr.reverse()
  }
  if (isPrime(limit)) {
    arr.push(limit)
  }
  return primes(limit - 1, arr)
}
```
