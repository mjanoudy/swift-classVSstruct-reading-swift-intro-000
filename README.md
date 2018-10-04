# Classes & Structs Quiz

![](http://i.imgur.com/zWBjkea.jpg)  

> Success is not final, failure is not fatal: it is the courage to continue that counts. -[Winston Churchill](https://en.wikipedia.org/wiki/Winston_Churchill)

## Overview

This quiz will give you practice working with both classes and structs. 

## Quiz Time!

In the last few lessons, you've learned a lot about classes and structs in Swift. Now, challenge yourself with a brief quiz to test everything you've learned.

### Question 1

Given this class that represents a giant:

```swift
class Giant {
    var name: String
    var weight: Double
    let homePlanet: String

    init(name: String, weight: Double, homePlanet: String) {
        self.name = name
        self.weight = weight
        self.homePlanet = homePlanet
    }
}
```

And this code that instantiates an instance of `Giant`:

```swift
let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")
```

Will these three lines of code run? If not, why not?

```swift
fred.name = "Brick"
fred.weight = 999.2
fred.homePlanet = "Mars"
```

ANSWER: The first two lines will run, because the properties were declared as variables, wheres home planet was declared as a constant and cannot be changed.

### Question 2

Can you fix the class definition above so that it _does_ work?

ANSWER: Changed the homePlanet property to a variable instead of constant and it works!

### Question 3

Take a look at this struct that represents an alien:

```swift
struct Alien {
    var name: String
    var height: Double
    var homePlanet: String
}
```

And this line of code that instantiates an `Alien`:

```swift
let bilbo = Alien(name: "Bilbo", height: 1.67, homePlanet: "Venus")
```

Will these three lines of code run? If so, why not?

```swift
bilbo.name = "Jake"
bilbo.height = 1.42
bilbo.homePlanet = "Saturn"
```

ANSWER: These lines will not run because a struct creates a COPY, and so since we declared bilbo as a let constant, we cannot change any of its properties.

### Question 4

Can you change the declaration of `bilbo` so that the above three lines of code _do_ work?

ANSWER: Simply change let bilbo to var bilbo and it will work 

### Question 5

Consider this bit of code that uses the `Giant` class:

```swift
let edgar = Giant(name: "Edgar", weight: 520.0, homePlanet: "Earth")
let jason = edgar
jason.name = "Jason"
```

What will the value of `edgar.name` be after those three lines of code are run? What will the value of `jason.name` be? Why?

ANSWER: the value of edgar.name will be Edgar still, and the value of jason.name will be Jason, as the line jason.name = "Jason" changes the name of the copy, not the original unlike in classes where the instance of jason just refers to the original.

### Question 6

Given this bit of code that uses the `Alien` struct:

```swift
var charles = Alien(name: "Charles", height: 2.25, homePlanet: "Pluto")
var charlesFromJupiter = charles
charlesFromJupiter.homePlanet = "Jupiter"
```

What will the value of `charles.homePlanet` be after the above code run? What about the value of `charlesFromJupiter.homePlanet`? Why?

ANSWER: similar to before, charlesFromJupiter is a COPY of charles, and so changing the value of home planet will only affect charlesFromJupiter and not charles, whose home planet remains pluto.

### Question 7

Here's a struct that represents a bank account:

```swift
struct BankAccount {
    var owner: String
    var balance: Double

    func deposit(_ amount: Double) {
        balance += amount
    }

    func withdraw(_ amount: Double) {
        balance -= amount
    }
}
```

Does this code work? Why or why not?

ANSWER: As these function will be changing something inside the struct's copy, without changing the original struct, swift will not even let us run this code. Since we are changing the properties, we must use mutating functions. 

### Question 8

Can you fix the `BankAccount` struct so it _does_ work?

ANSWER: simply add mutating infront of functions.

### Question 9

Given this bit of code (which incorporates any fixes you made in Question 8):

```swift
var joeAccount = BankAccount(owner: "Joe", balance: 100.0)
var joeOtherAccount = joeAccount
joeAccount.withdraw(50.0)
```

What will the value of `joeAccount.balance` be after the above code runs? What about the value of `joeOtherAccount.balance`? Why?

ANSWER: joeOtherAccount is just a copy of joe, so the instant it is initiated, it had 100 in its balance property. Changing the joe property does not change joeOtherAccount.
joe.balance = 50
joeOtherAccount.balance = 100

### Question 10

Here's a class that can track songs in a music library:

```swift
class MusicLibrary {
    var tracks: [String]

    init() {
        tracks = []
    }

    func add(track: String) {
        tracks.append(track)
    }
}
```

Given this bit of code that uses `MusicLibrary`:

```swift
let library1 = MusicLibrary()
library1.add(track: "Michelle")
library1.add(track: "Voodoo Child")
let library2 = library1
library2.add(track: "Come As You Are")
```

After this code runs, what are the contents of `library1.tracks`? What about the contents of `library2.tracks`? Why?

ANSWER: since a class lets you refer to one instance to another, changing the contents of library 2 by adding a song also adds it to its original reference, library 1.

<a href='https://learn.co/lessons/ClassesVsStructs' data-visibility='hidden'>View this lesson on Learn.co</a>
