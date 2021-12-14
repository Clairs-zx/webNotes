# New Features of ES6

- ### Iterator

```javascript
function nameIterator(names) {
  let nextIndex = 0;
  return {
    next: function() {
      return nextIndex < names.length ?
      { value: names[nextIndex++], done: false } :
      { done: true }
    }
  }
}

// Create an array of names
const namesArr = ['Jack', 'Jill', 'John'];
// Init iterator and pass in the names array
const names = nameIterator(namesArr);

console.log(names.next().value);   //'Jack'
console.log(names.next().value);   //'Jill'
console.log(names.next().value);   //'John'
console.log(names.next().value);   //undefinde
```

- ### Generator

```javascript
function* sayName(nameArray){
    for(let i = 0; i < nameArray.length; i++){
        yield nameArray[i];
    }
}
const array = ['Jack','Jill','John'];
const names = sayName(array);
console.log(names.next().value);   //'Jack'
console.log(names.next().value);   //'Jill'
console.log(names.next().value);   //'John'
console.log(names.next().value);   //undefinde
```

- ### Maps

  - ##### Set maps  - Set/Get

  ```javascript
  const map = nes Map();
  
  // Set Keys
  const key1 = 'some string',
        key2 = {},
        key3 = function() {};
  
  // Set map values by key
  map.set(key1, 'Value of key1');
  map.set(key2, 'Value of key2');
  map.set(key3, 'Value of key3');
  
  //Set map values 
  map.set(key1:'Value of key1').set(key2:'Value of key2');
  
  // Get values by key
  console.log(map.get(key1)); //Value of key1 
  
  //count values
  console.log(map.size);  //3
  ```

  - ##### Iterating maps

  ```javascript
  //Loop using [for...of] to get keys and values
  for(let[key,value] of map){
      console.log(`${key}:${value}`);   //key1:Value of key1   key2:Value of key2    key3:Value of key3
  }
  
  //Iterate kyes only
  for(let key of map.keys()){
      console.log(key);
  }
  
  //Iterate values only
  for(let value of map.value()){
      console.log(value);
  }
  
  //Loop with [forEach]
  map.forEach((value,key)=>{
      console.log(`${key}:${value}`);
  });
  
  ```

  - ##### Convert to array

  ```javascript
  console.log(Array.from(map));
  console.log(Array.from(map.values()));
  console.log(Array.from(map.keys()));
  ```

- ### Sets

  - ##### Add sets

  ```javascript
  const set = new Set();
  set.add(100);
  set.add('A string');
  set.add({name：‘John'});
  set.add(true);
  
  const set = new Set(100,'string',{name:'John'});
  console.log(set.size);
  ```

  - ##### check for value

  ```javascript
  console.log(set.has(100));  //true
  console.log(set.has(50+50));  //true
  ```

  - ##### delete from set

  ```javascript
  set.delete(100);
  console.log(set);
  ```

  - ##### Iterating Sets

  ```javascript
  // [For..of]
  for(let item of set){
      console.log(item);
  }
  
  //forEach
  set.forEach((item)=>{
      console.log(item);
  })
  ```

  - ##### Convert set to array

  ```javascript
  console.log(Array.from(set));
  ```

  





