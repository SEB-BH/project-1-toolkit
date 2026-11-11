<h1>
  <span class="headline">Project Toolkit</span>
  <span class="subhead">Objects from Classes</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to create separate objects from a class and call a method that changes one object’s data.

## Start with familiar objects

Imagine our delivery game has several robots. Each robot needs a name, a battery level, and a delivery count.

We already know how to store that information:

```js
const robotOne = {
  name: 'Pearl',
  battery: 100,
  deliveries: 0
};

const robotTwo = {
  name: 'Falcon',
  battery: 100,
  deliveries: 0
};
```

Both objects have the same structure.

If we need many robots with the same starting properties and actions, a **class** gives us a reusable way to create them.

> 💡 A JavaScript class creates objects. It has a different purpose from an HTML `class` attribute used for CSS.

## Describe how to create one robot

Add this class above any code that creates robots:

```js
class DeliveryRobot {
  constructor(name) {
    this.name = name;
    this.battery = 100;
    this.deliveries = 0;
  }
}
```

We use **PascalCase** for a class name: each word starts with a capital letter.

The **constructor** sets up a new object. JavaScript runs it when we create an instance using `new`. [MDN](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Advanced_JavaScript_objects/Classes_in_JavaScript?utm_source=chatgpt.com)

Inside this constructor:

- `name` is the value we receive.
- `this` refers to the new object being created.
- `this.name = name` stores the received name on that object.
- Each object starts with its own battery level and delivery count.

## Create two objects

Replace the earlier object declarations with:

```js
const robotOne = new DeliveryRobot('Pearl');
const robotTwo = new DeliveryRobot('Falcon');
```

`new` asks JavaScript to create an object using the class.

An object created from a class is called an **instance**.

Inspect the results:

```js
console.log(robotOne);
console.log(robotTwo);
```

We still have two separate objects. We have changed how we create them.

## Give each robot an action

A robot should be able to complete a delivery.

A **method** is a function associated with an object. Inside the class, add this method **after the constructor’s closing brace and before the class’s closing brace**:

```js
deliver() {
  this.battery = this.battery - 20;
  this.deliveries = this.deliveries + 1;
}
```

Class methods use this shorter syntax: no `const`, no arrow, and no comma between methods.

Call the method on one robot:

```js
robotOne.deliver();
```

Then inspect individual values:

```js
console.log(robotOne.battery);    // 80
console.log(robotOne.deliveries); // 1

console.log(robotTwo.battery);    // 100
console.log(robotTwo.deliveries); // 0
```

When we call `robotOne.deliver()`, `this` inside that method refers to `robotOne`.

The same method can work with another robot:

```js
robotTwo.deliver();
```

Each robot keeps its own data.

## Protect the rule

Our current method would eventually allow a negative battery level.

A delivery should only happen when the robot has at least `20` battery remaining.

Replace the method with:

```js
deliver() {
  if (this.battery >= 20) {
    this.battery = this.battery - 20;
    this.deliveries = this.deliveries + 1;
  }
}
```

The complete class is now:

```js
class DeliveryRobot {
  constructor(name) {
    this.name = name;
    this.battery = 100;
    this.deliveries = 0;
  }

  deliver() {
    if (this.battery >= 20) {
      this.battery = this.battery - 20;
      this.deliveries = this.deliveries + 1;
    }
  }
}
```

We have grouped related **data** and **actions**.

The same pattern can represent customers, vehicles, animals, items, or characters in a game.

> 💡 Changing an object does not automatically change the page. In a DOM game, an event listener can call the method and then call your rendering function to display the updated data.

## 🎓 You Do

Add a `recharge()` method that restores a robot’s battery to `100`. Call it on one robot and log both robots’ battery levels to confirm that their data remains separate.
