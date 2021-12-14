# Javascript Patterns

- ### Module Pattern   

  ###### It allows us to break our code up into modules and have private functions and variables

  ```javascript
  const UICtrl = (function(){
      let text = 'hello';           //private vars and functions
      const changeText = function(){
          const element = document.querySelector('h1');
          element.textContent = text;
      }
      
      return {      //public var and functions
          callChangeText:function(){
              changeText();
          },
          log:function(){
              console.log(text);
          }
      }
  })();
  
  console.log(UICtrl);     //{callChangeText:f,log:f}
  UICtrl.callChangeText(); // 调用changeText函数
  UICtrl.log();            // hello
  console.log(UICtrl.text);  // undefined
  ```

  

- ### Revealing Module Pattern

  ```javascript
  const ItemCtrl = (function(){
      let data = [];
      function add(item){
          data.push(item);
      }
      function get(id){
          return data.find(item=>{
              return item.id === id;
          })
      }
      return{
          add: add,
          get: get
      }
  })();
  ItemCtrl.add({id: 1, name: 'John'});
  ItemCtrl.add({id: 2, name: 'Make'});
  console.log(ItemCtrl.get(2));   //{id: 2, name: 'Make'}
  ```

  

- ### singleton Pattern

  ###### It is a kind of a module pattern where we can only create one instance of an object

  ```javascript
  const Singlenton = (function(){
      let instance;
      function createInstance(){
          const object = new Object({name: 'John'});
          return object;
      }
      
      return{
          getInstance: function(){
              if(!instance){
                  intance = createInstance();
              }
              return instance;
          }
      }
  })();
  
  const instanceA = Singleton.getInstance();
  const instanceB = Singleton.getInstance();
  console.log(instanceA)  //{name: 'John'}
  console.log(instanceA === instanceB);  //true
  ```

  

- ### Factory pattern

  ###### It is used to create many many objects 

  ```javascript
  function MemberFactory(){
      this.createMember: function(name, type){
          let member;
          if(type === 'simple'){
              member = new SimpleMembership(name);  //object
          }else if(type === 'standard'){
              member = new StandardMembership(name);
          }else if(type === 'super'){
              member = new SuperMembership(name);
          }
          
          member.type = type;
          member.define = function(){
              console.log(`${this.name} (${this.type}): ${this.cost}`);
          }
      }
  }
      
  const SimpleMembership = function(name){
      this.name = name;
      this.cost = '$5';
  } 
  const StandardMembership = function(name){
      this.name = name;
      this.cost = '$10';
  } 
  const SuperMembership = function(name){
      this.name = name;
      this.cost = '$15';
  } 
  
  const members = [];
  const factory = new MemberFactory();
  members.push(factory.createMember('John Doe','simple'));
  members.push(factory.createMember('Chris Jackson','super'));
  members.push(factory.createMember('Tom Smith','standard'));
  
  members.forEach((member) => {
      member.define();
  })
  //John Doe (simple): $5
  //Chris Jackson (super): $15
  //Tom Smith (standard): $10
  
  console.log(members);  // (3)[SimpleMembership,SuperMembership, StandardMembership] 
  					   //    0:SimpleMembership{name: 'John Doe', cost: '$5', type: 'simple', define: f}
  
  
  
  ```

  

- ### Observer Pattern

###### 		It allows us to basically  subscribe and unsubscribe to events or functionality

- ### Mediator Pattern

- ### State Pattern