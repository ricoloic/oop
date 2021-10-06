# OOP - Object Oriented Programing

the principle is to make a blueprint. You can thing of what you want to represent is as if "what is it to be me", what i mean about this.

```jsx
  INSTANCE car

    DEFINE PROPERTIES WHIT : color / brand :

      SET car.color EQUAL TO color OR :default_value
      SET car.brand EQUAL TO type OR :default_brand

    STOP DEFINE PROPERTIES

  STOP INSTANCE
```

so my object is a car, really simple car but we start with that

my ar is define by tow properties (not including the name of the object)

- a color property
- a brand property

lets create a car

```jsx

  f150 EQUAL TO NEW car WITH : color "RED" / brand "RAM" :

  PRINT TO SCREEN f150

  # RESULT #

  f150 INSTANCE OF car
    PROPERTIES
      - color EQUAL "RED"
      - brand EQUAL "RAM"
```

let say we want a to define a user object on a site
"think about what is it to be a user, mmm, I wonder"

```jsx

  INSTANCE user

    DEFINE PROPERTIES WHIT : name /  age / gSTOPer :

      SET user.name EQUAL TO name
      SET user.age EQUAL TO age
      SET user.gSTOPer EQUAL TO gSTOPer OR :default_gSTOPer

      SET user.points EQUAL TO 0

    STOP DEFINE PROPERTIES

    DEFINE FUNCTION add_points WITH points_to_add

      SET user.points EQUAL TO user.points PLUS points_to_add

    STOP DEFINE FUNCTION

    DEFINE FUNCTION print_properties

      PRINT TO SCREEN user

    STOP DEFINE

  STOP INSTANCE

  # CREATING AN INSTANCE #

  admin EQUAL TO NEW user : name "rico suave" / age 19 / gSTOPer "Alien" :

  USE print_properties FROM admin

  # RESULT #

  admin INSTANCE OF user
    PROPERTIES
      - name EQUAL "rico suave"
      - age EQUAL 19
      - gSTOPer EQUAL "Alien"
      - points EQUAL 0
    FUNCTIONS
      - add_points : points_to_add :
      - print_properties

  # ADDING POINTS TO THE USER #

  USE add_points FROM admin WITH : points_to_add 110 :

  USE print_properties FROM admin

  # RESULT #
  admin INSTANCE OF user
    PROPERTIES
      - name EQUAL "rico suave"
      - age EQUAL 19
      - gSTOPer EQUAL "Alien"
      - points EQUAL 110
    FUNCTIONS
      - add_points : points_to_add :
      - printProperties

```

---

you might go about coding it like this

```js
class User {
  /** the gSTOPer = "Unknown" is the default value when not provided */
  constructor(name, age, gSTOPer = "Unknown") {
    this.name = name;
    this.age = age;
    this.gSTOPer = gSTOPer;

    this.points = 0;
  }

  addPoints(pointsToAdd) {
    this.points = this.points + pointsToAdd;
  }

  printProperties() {
    console.log(this);
  }
}
```

so this would be our representation of the class/object definition for a user

```js

  // CREATING AN INSTANCE //

  const admin = new User("rico suave", 19, "Alien");
  admin.printProperties();

  // RESULT //

  User {
    name: 'rico suave',
    age: 19,
    gSTOPer: 'Alien',
    points: 0,

    Prototype {
      constructor: class User { constructor(name, age, gSTOPer) },
      addPoints: function addPoints(pointsToAdd),
      printProperties: function printProperties()
    }
  }

  // ADDING POINTS TO THE USER //

  admin.addPoints(110);
  admin.printProperties();

  // RESULT //

  User {
    name: "rico suave",
    age: 19,
    gSTOPer: "Alien",
    points: 110,

    Prototype {
      constructor: class User { constructor(name, age, gSTOPer) },
      addPoints: function addPoints(pointsToAdd),
      printProperties: function printProperties()
    }
  }
```

if we go back to the car example we could implement some buttons for the car radio

```jsx
  INSTANCE radio_button

    DEFINE PROPERTIES WITH : name / usage :

      SET radio_button.name EQUAL TO name

      DEFINE FUNCTION use EQUAL TO usage

    STOP DEFINE PROPERTIES

  STOP INSTANCE


  INSTANCE car

    DEFINE PROPERTIES WHIT : color / brand / radio_buttons :

      SET car.color EQUAL TO color OR :default_value
      SET car.brand EQUAL TO type OR :default_brand

      SET car.radio_buttons EQUAL TO EMPTY LIST

      FOR EACH radio_button IN radio_buttons

        ADD radio_button TO car.radio_buttons

      STOP FOR EACH

    STOP DEFINE PROPERTIES

  STOP INSTANCE
```
