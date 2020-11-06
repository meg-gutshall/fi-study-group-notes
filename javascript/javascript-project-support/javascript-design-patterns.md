# JavaScript Design Patterns

> **Alice Balbuena on 02/24/20**

## Design Patterns

* Optimizable, reusable solutions
* Should be purposefully chosen and implemented per situation
* Two main patterns: the Prototype Pattern and the Factory Method Pattern
  * Creation design patterns
  * Use the smallest amount of memory footprint
* MVC is a structural/architectural design pattern

## Prototype Pattern

* Create our own inheritance chain by using `Object.create()` to create our own "shadow copy"
  * Inherits the properties of the parent object so any clone has access to the parent information 
* Can set default properties in parent and then overwrite them in clone

## Factory Method Pattern

* Add the word "factory" at the end of the variable itself \(i.e. `UserFactory`\)
* Use when you work with small objects that have a lot of shared properties

```javascript
// TODO: Explain this shit!!

let UserFactory = {
  createUser: function(name, role) {
    let user;
    
    if (role === "Admin") {
      user = Object.create(Admin, { name: { value: name }});
    } else {
      user = Object.create(User, { name: { value: name }});
    }
    
    return user;
  }
};
//=> undefined

const User = {
  name: "",
  permissions: ["User"]
};
//=> undefined

const Admin = Object.create(User, {
  permissions: { value: ["User", "Admin"] }
});
//=> undefined

const userFactory = Object.create(UserFactory);
//=> undefined

const alice = userFactory.createUser("Alice", "Admin");
//=> undefined

// RETURN VALUES
UserFactory;
//=> {createUser: f}
User;
//=> {name: "", permissions: Array(1)}
Admin;
//=> {permissions: Array(2)}
userFactory;
//=> {}
alice;
//=> {name: "Alice"}

console.log("name:", alice.name);
// LOG: name Alice
//=> undefined
console.log("permissions:", alice.permissions);
// LOG: permissions (2) ["User", "Admin"]
//=> undefined
```

### Abstracted Factory Method Pattern

* Abstracts away code to make it inaccessible, therefore safeguarding the code

```javascript
let UserFactory = (function() {
  const types = {
    Standard: {
      name: "",
      permissions: ["User"]
    },
    Admin: {
      name: "",
      permissions: ["User", "Admin"],
      isAllowed: function() {
        const allow = this.permissions.includes("Admin");
        return allow ? "You can do that" : "You cannot do that";
      }
    }
  };
  
  return {
    createUser: function(name, role) {
      let User = types[role];
      return User ? Object.create(User, { name: { value: name }}) : null;
    }
  };
})();
//=> undefined

const userFactory = Object.create(UserFactory);
//=> undefined

const alice = userFactory.createUser("Alice", "Admin");
//=> undefined

console.log(alice.isAllowed());
//=> LOG: You can do that
//=> undefined
```

## Anti-Patterns

* Never pollute the global context --&gt; It can be easily overwritten
* `setTimeout(function, time)` --&gt; Never pass in a string for the `function` argument
* `eval(string)` --&gt; Don't do it!
* Never modify `Object.prototype`

## Resources

* [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/) by Addy Osmani

