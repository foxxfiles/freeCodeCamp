---
id: 594810f028c0303b75339ad3
title: Vector dot product
challengeType: 5
forumTopicId: 302343
---

# --description--

A vector is defined as having three dimensions as being represented by an ordered collection of three numbers: (X, Y, Z).

# --instructions--

Write a function that takes any numbers of vectors (arrays) as input and computes their dot product. Your function should return `null` on invalid inputs such as vectors of different lengths.

# --hints--

dotProduct should be a function.

```js
assert.equal(typeof dotProduct, 'function');
```

dotProduct() should return null.

```js
assert.equal(dotProduct(), null);
```

dotProduct(\[[1], [1]]) should return 1.

```js
assert.equal(dotProduct([1], [1]), 1);
```

dotProduct(\[[1], [1, 2]]) should return null.

```js
assert.equal(dotProduct([1], [1, 2]), null);
```

dotProduct([1, 3, -5], [4, -2, -1]) should return 3.

```js
assert.equal(dotProduct([1, 3, -5], [4, -2, -1]), 3);
```

`dotProduct(...nVectors)` should return 156000.

```js
assert.equal(
  dotProduct(
    [0, 1, 2, 3, 4],
    [0, 2, 4, 6, 8],
    [0, 3, 6, 9, 12],
    [0, 4, 8, 12, 16],
    [0, 5, 10, 15, 20]
  ),
  156000
);
```

# --seed--

## --seed-contents--

```js
function dotProduct(...vectors) {

}
```

# --solutions--

```js
function dotProduct(...vectors) {
  if (!vectors || !vectors.length) {
    return null;
  }
  if (!vectors[0] || !vectors[0].length) {
    return null;
  }
  const vectorLen = vectors[0].length;
  const numVectors = vectors.length;

  // If all vectors not same length, return null
  for (let i = 0; i < numVectors; i++) {
    if (vectors[i].length !== vectorLen) {
      return null;  // return undefined
    }
  }

  let prod = 0;
  let sum = 0;
  let j = vectorLen;
  let i = numVectors;
  // Sum terms
  while (j--) {
    i = numVectors;
    prod = 1;

    while (i--) {
      prod *= vectors[i][j];
    }
    sum += prod;
  }
  return sum;
}
```
