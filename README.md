# data-structures
Common data stuctures implementations in JS

## Linked Lists
```JavaScript
// Linked list has 2 advantages
// 1. Efficency in resizing
// 2. Efficency when adding an element in the start/end of the list.

class LinkedList {
  constructor () {
    this.head = null
    this.tail = null
  }
  prepend (value) {
  	const newNode = { value, next: this.head}
    
    if (!this.head) {
      this.tail = newNode
    }
    
    this.head = newNode
    
  }
  append (value) {
  	const newNode = {
      value,
      next: null
    }
    if (this.tail) {
      this.tail.next = newNode
    }
    this.tail = newNode
    
    if (!this.head) this.head = newNode
  }
  
  delete (value) {
  	if (!this.head) return null
    
    while (this.head && this.head.value === value) {
   	  this.head= this.head.next
    }
    
    let curNode = this.head
    
    while (curNode.next) {
      if (curNode.next.value === value) {
      	curNode.next = curNode.next.next
      } else {
      	curNode = curNode.next
      }
    }
    
    if (this.tail.value === value) {
      this.tail = curNode
    }
  }
  
  toArray () {
  	const elements = []
    
  	let curNode = this.head;
    
    while (curNode) {
      elements.push(curNode.value)
      curNode = curNode.next
    }
    
    return elements
  }
}


const list = new LinkedList()
list.prepend("Rasul")
list.append("Rasul")
list.append(1)
list.append("Rasul")

console.log(list.toArray(), "initial")

list.delete("Rasul")


console.log(list)
console.log(list.toArray(), "initial")

```
#
