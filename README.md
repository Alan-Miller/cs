# cs
Computer science notes

# Recursion

### Alternatives to recursion

<details>
<summary>Alternatives</summary>

  #### hard coded
  - for small, known number of times 

  #### for loops
  - good for set number of times
  - great for arrays and objects

  #### while loops
  - good for unknown number of times


  #### variable depth
  ```js
    let animals = {
      dog: {
        labrador: {
          american: '',
          english: ''
        }, 
        akita: {
          japanese: '',
          american: ''
        }
      },
      cat: ''
    }
  ```
</details>


### Example: addAllThings

```js
  function addAllThings(n) {
    if (n === 1) {
      console.log('done');
      return ;
    }
    else {
      console.log('n', n);
      return n + addAllThings(n - 1);
    }
  }
  addAllThings(4
```

Each iteration of the recursion function runs and remains on the pending call stack because it cannot yet complete until the last time, when it finally gets a value.