# CS
Computer science notes

## Recursion

#### Alternatives to recursion

<details>
<summary>Alternatives</summary>

  #### hard coded
  - for small, known number of times 

  #### for loops
  - good for set number of times
  - great for arrays and objects

  #### while loops
  - good for unknown number of times

</details>

#### Example: variable depth

<details><summary>print nested objects</summary>

```js
  // showing object depth
  let animals = {
    dog: {
      labrador: {
        american: 'http://dogpics.com/7423.png',
        english: 'http://dogpics.com/5274.png'
      }, 
      akita: {
        japanese: 'http://dogpics.com/3486.png',
        american: 'http://dogpics.com/4843.png'
      },
      poodle: {
        standard: {
          french: 'http://dogpics.com/8484.png',
          barbone: 'http://dogpics.com/1268.png'
        },
        miniature: 'http://dogpics.com/1350.png',
        toy: 'http://dogpics.com/884.png'
      }
    },
    cat: 'http://grumpycat.com/mrGrumpy.png'
  }

  function printObj(obj, count = 0) {
    for (let prop in obj) {
      if (typeof obj[prop] === 'object') {
        console.log('---'.repeat(count), prop + ':');
        printObj(obj[prop], count + 1);
      }
      else console.log('---'.repeat(count), prop + ':', obj[prop]);
    }
  }
  printObj(animals);
```
</details>


#### More examples

<details><summary>addition, factorials</summary>
  
  ```js

    // addition
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
    addAllThings(4);


    // factorials
    function fac(n) {
      if (n === 1) return 1;
      else return n * fac(n - 1);
    }

    fac(4); // 24

  ```

  - Each iteration of the recursion function runs and remains on the pending call stack because it cannot yet complete until the last time, when it finally gets a value.

</details>

