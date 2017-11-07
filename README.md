# CS

Computer science notes
<br/>

## Recursion
- Each iteration of the recursion function runs and remains on the pending call stack because it cannot yet complete until the last time, when it finally gets a value.
- Real case scenarios: 
  - Populate a database (doing calculations for many rows).


<details>
<summary>Alternatives to recursion</summary>

  #### hard coded
  - for small, known number of times 

  #### for loops
  - good for set number of times
  - great for arrays and objects

  #### while loops
  - good for unknown number of times

</details>

#### Examples

<details><summary>nested objects, addition, factorials</summary>

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

</details>
<br/>

## Linked Lists
- Each node has data and a pointer property pointing to the next node.
- This allows for insertion at any place in memory without keeping list item together, which creates problems:
  - We might need to add something but the next spot in memory is taken.
  - We might try reserving a large amount of space for potential use when we need to insert things, but we might not know how much space to reserve, and the space goes unused until those insertions are made.
- To insert, change prior nodes pointer to point to new node, and new node's pointer to next.
- Real case scenarios: 
  - Photo site has user side with gallery and admin side and you need to allow user to rearrange images with drag-and-drop capability in the gallery but still keep track of that order.

  <details><summary>Example: Linked list with add and remove methods</summary>
  
  ```js
    class Node {
      constructor(val) {
        this.data = val;
        this.next = null;
      }
    }

    class LinkedList {
      constructor() {
        this.head = null;
      }
      // add to list
      add(val) {
        let node = new Node(val); console.log(`added ${JSON.stringify(node)}`); // make new node
        if (!this.head) this.head = node; // if no head, head = node
        else {
          let current = this.head; // start at head
          while (current.next) current = current.next; // traverse list while .next is true
          current.next = node; // newest node goes on end
        }
      }
      // remove from list
      remove(val) {
        let current = this.head;
        let previous = null;
        while (current.data !== val) {
          previous = current;
          current = current.next;
        }
        previous.next = current.next;
        console.log(`removed node with value ${JSON.stringify(val)}`);
      }
    }

    let list = new LinkedList();
    list.add(11);
    list.add(1);
    list.add(6);
    list.add(8);
    list.remove(6);
  ```
  
  </details>