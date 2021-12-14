# Regular Expressions

- #### Evaluation Function

  ```javascript
  let re;
  re = /hello/; 
  re = new RegExp('hello','i');
  re2 = /hello/i;  //case insensitive
  re3 = /hello/g;  // Global search
  
  console.log(re);  // /hello/
  console.log(re.source)  // hello
  ```

  1. exec( )   -   Return result in an array or null

     ```javascript
     const result = re.exec("qianzhui hello world");
     console.log(result); // ['hello',index:10,input:"hello world"]
     console.log(result[0]); // hello
     ```

  2. test( )  -  Returns true or false

     ```javascript
     const result = re.test("hello");
     console.log(result); //true
     
     console.log(re.test("Hello")), // false
     console.log(re2.test("Hello")); //true
     ```

  3. match ( )   -   Return result array or null

     ```javascript
     const str = 'hello There';
     console.log(str.match(re)); // ['hello',index:10,input:"hello world"]
     ```

  4. search( )   -   Returns index of the first match if not found returns -1

     ```javascript
     const str = 'Brad hello There';
     const str2 = 'Brad Hello There'
     console.log(str.search(re));  // 5
     console.log(str2.search(re));  //-1
     console.log(str2.search(re2)); // 5
     ```

  5. replace( )   -   Return new string with some or all matches of a pattern

     ```javascript
     const str = 'Hello There';
     const newStr = str.replace(re,'Hi');
     console.log(newStr);  // 'Hi There'
     ```

- #### Metacharacter Symbols

  ```javascript
  let re;
  re = /^h/i;   //Must start with h
  console.log(re.exec('hello'));  // ['h',index:0,input:'hello']
  
  re = /world$/i;  // Must end with 'world'
  console.log(re.exec('hello world'));  //{'world',index:7,input:'hello world'}
  
  re = /^hello$/i;  // Must begin and end with 'hello'
  console.log(re.exec('hello'));  //['hello',index:0, input:'hello']
  console.log(re.exec('hello world'));  //null
  
  re = /h.llo/i;    // . Matches any ONE character only one time
  console.log(re.exec('hello'));  //['hello',index:0, input:'hello']
  console.log(re.exec('heelo'));  //null
  
  re = /h*llo/i;    // * Match 'h' 0 or more times
  console.log(re.exec(llo));  //['llo',index:0, input:'llo']
  console.log(re.exec(hhllo));  //['hhllo',index:0, input:'hhllo']
  console.log(re.exec(hello));  //['llo',index:2, input:'hello']
  
  re = /h+llo/i;    // + Match 'h' 1 or more times
  console.log(re.exec(hello));  //null
  console.log(re.exec(hllo));  //['hllo',index:0, input:'hllo']
  
  re = /gre?a?y/i;    // Optional character
  console.log(re.exec('Gray')); // ['Gray',index:0,input:'Gray']
  console.log(re.exec('Grey'));// ['Grey',index:0,input:'Grey']
  console.log(re.exec('Gry'));// ['Gry',index:0,input:'Gry']
  console.log(re.exec('Griy'));// null
  
  re = /gre?a?y\?/i;   //Escape character
  console.log(re.exec('Gray?'))  // ['Gray?',index:0,input:'Gray?']
  ```

- #### Character Sets & Quantifiers

  - character Set

    ```javascript
    re = /gr[ae]y/i;   // Must be an a or e 
    console.log(re.exec('Gray')); // ['Gray',index:0,input:'Gray']
    console.log(re.exec('Grey'));// ['Grey',index:0,input:'Grey']
    console.log(re.exec('Gry'));// null
    console.log(re.exec('Griy'));// null
    
    re = /gr[ae]*y/i;   // Must be a or e 0 or any times 
    console.log(re.exec('Gry'));// ['Gry',index:0,input:'Gry']
    
    re = /[^GF]ray/i;      // Match anything except a G or F
    console.log(re.exec('Hray'));  // ['Hray',index:0,input:'Hray']
    
    re = /[a-z]/;  //Match any lowercase letter
    re = /[A-Z]ray/;      // Match any uppercase letter
    re = /[A-Za-z]ray/;   // Match any  letter
    re = /[0-9]ray/;      // Match any digit
    ```

  - Quantifiers

    ```javascript
    re = /hel{2}o/i;  //Must occur exactly {m} amount of times
    re = /Hel{2,4}o/i;      // Must occur exactly {m} amount of times
    re = /Hel{2,}o/i;      // Must occur at least {m} times
    ```

  - Grouping

    ```javascript
    re = /^([0-9]x){3}$/;   
    console.log(re.exec('3x3x3x'));  // ['3x3x3x',index:0,input:'3x3x3x']
    ```

- #### Shorthard Character Classes

  - shorthand character class

    ```javascript
    re = /\w/;  //Word character - alphanumeric or _
    console.log(re.exec('3x3x3x'));  // ['3',index:0,input:'3x3x3x']
    console.log(re.exec('_w'));  // ['_',index:0,input:'_w']
    
    re = /\w+/;    // + = one or more
    console.log(re.exec('!'));  //null
    console.log(re.exec(' '));  //null
    console.log(re.exec('w_w'));  // ['w_w',index:0,input:'w_w']
    
    re = /\W/;    // Non-Word character no [number letter underline]
    console.log(re.exec('!'));  // ['!',index:0,input:!']
    console.log(re.exec(' '));  // [' ',index:0,input:' ']
    console.log(re.exec('w_w'));  // null
    
    re = /\d/;    // Match any digit
    re = /\d+/;    // Match any digit 0 or more times
    re = /\D/;      // Match any Non-digit
    
    re = /\s/;      // Match whitespace char
    re = /\S/;      // Match non-whitespace char
    
    re = /Hell\b/i;  //Word boundary
    console.log(re.exec('Hell! where'))  //['Hell'，index：0，input：'Hell! where']
    console.log(re.exec('Hell '))  //['Hell'，index：0，input：‘Hell ']
    console.log(re.exec('Hello'))  //null
    ```

  - Assertions

    ```javascript
    re1 = /x(?=y)/;  // Match x only if followed by y
    re2 = /x(?!y)/;  // Match x only if NOT followed by y
    
    console.log(re1.exec('xy'));  //['xy',index:0,input:'xy']
    console.log(re1.exec('x'));  //null
    console.log(re2.exec('xy'));  //null
    console.log(re2.exec('x'));  //['x',index:0,input:'x']
    ```

  