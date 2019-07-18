# Structs and Classes lab

Fork and clone this repo. On your fork, answer and commit the follow questions. When you are finished, submit the link to your repo on Canvas.


## Question 1√

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

let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")
```

Will these three lines of code run? If not, why not?

```swift
fred.name = "Brick"  // WILL RNN
fred.weight = 999.2 // WILL RUN
fred.homePlanet = "Mars" WILL NOT RUN. Because it is a constant and cant be modified.
```

Fix the class definition for `Giant` in the space below so that it **does** work:

```swift
class Giant {
var name: String
var weight: Double
var homePlanet: String

init(name: String, weight: Double, homePlanet: String) {
self.name = name
self.weight = weight
self.homePlanet = homePlanet
}
}

let fred = Giant(name: "Fred", weight: 340.0, homePlanet: "Earth")
```
## Question 2√

Take a look at this struct that represents an alien:

```swift
struct Alien {
 var name: String
 var height: Double
 var homePlanet: String
}
let bilbo = Alien(name: "Bilbo", height: 1.67, homePlanet: "Venus")
```

Will these three lines of code run? If so, why not?

```swift
bilbo.name = "Jake"
bilbo.height = 1.42
bilbo.homePlanet = "Saturn"
```

they will not run because the bilbo is a constant and the arguements cant be changed.

Change the declaration of `bilbo` so that the above three lines of code **do** work:
```swift
struct Alien {
var name: String
var height: Double
var homePlanet: String
}
var bilbo = Alien(name: "Bilbo", height: 1.67, homePlanet: "Venus")


bilbo.name = "Jake"
bilbo.height = 1.42
bilbo.homePlanet = "Saturn"
```

## Question 3√

Consider this bit of code that uses the `Giant` class:

```swift
let edgar = Giant(name: "Edgar", weight: 520.0, homePlanet: "Earth")
let jason = edgar
jason.name = "Jason"
```

What will the value of `edgar.name` be after those three lines of code are run? What will the value of `jason.name` be? Why?

Since jason is referencing  edgar, any chanes made to its property will affect any instance of its creation. So since jason.name was changed to "Jason", edgar.name will be will also be "Jason"
jason.name will be "Jason " because it was changed.

## Question 4√

Given this bit of code that uses the `Alien` struct:

```swift
var charles = Alien(name: "Charles", height: 2.25, homePlanet: "Pluto")
var charlesFromJupiter = charles
charlesFromJupiter.homePlanet = "Jupiter"
```

What will the value of `charles.homePlanet` be after the above code run? What about the value of `charlesFromJupiter.homePlanet`? Why?

charles.homePlanet will be "Pluto" after the code has been ran. 
charlesFromJupiter.homePlanet will be "Jupiter" because it is a value type


## Question 5√

Here's a struct that represents a bank account: √

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

Does this code work? Why or why not? √

The code would not work because balance isnt mutable. (self is immitable)

Fix the `BankAccount` struct so it does work.

```swift
struct BankAccount {
var owner: String
var balance: Double

mutating func deposit(_ amount: Double) {
balance += amount
}

mutating func withdraw(_ amount: Double) {
balance -= amount
}
}
```

Given the code below (which should incorporate any fixes you made):      X

```swift
var joeAccount = BankAccount(owner: "Joe", balance: 100.0)
var joeOtherAccount = joeAccount
joeAccount.withdraw(50.0)
```

What will the value of `joeAccount.balance` be after the above code runs? What about the value of √ `joeOtherAccount.balance`? Why?

joeAccount.balance = Will be 50
joeOtherAccount.balance = Will still be 100 because  joeOtherAccount made a copy of the value and was unchanged with  joeAccount.balance having a withdraw


## Question 6

a. Write a struct called `Person` that has 3 properties of type `String`: a first name, a last name and a middle name. Have the middle name be optional. Create 2 instances of a `Person`, one with a middle name and one without. Print one of their first names.

```swift
struct Person {
var firsName:String
var lastName:String
var middleName:String?
}

var person1 = Person(firsName: "Adam", lastName: "Jackson", middleName: "Henry")

var person2 = Person(firsName: "Ayoola", lastName: "Abudu", middleName: nil)
```

b. Write a method in `Person` called `fullName` that will return a formatted string of an instance's full name. Call this method on both the instances you created in part a.

```swift
struct Person {
var firsName:String
var lastName:String
var middleName:String?

func fullname() -> String {
if let middle = middleName{
return   "my full name is \(firsName) \(middle) \(lastName)"
}else {
return   "my full name is \(firsName) \(lastName)"
}
}
}

var person1 = Person(firsName: "Adam", lastName: "Jackson", middleName: "Henry")

var person2 = Person(firsName: "Ayoola", lastName: "Abudu", middleName: nil)

print(person1.fullname())
print(person2.fullname())
```

## Question 7

a. Create a class called `Book` that has properties `title`, `author` and `rating`, of type `String`, `String`, and `Double` respectively. Don't forget the initializer. Create some instances of `Book`.

```swift
class Book {
var title:String
var author:String
var rating:Double

init (title:String, author:String, rating:Double) {
self .title = title
self .author = author
self .rating = rating
}

}

var favoriteBook = Book(title: "Harry Potter", author: "J. K. Rowling", rating: 9.2)
```

b. Add a method to `Book` called `isGood` that returns `true` if its rating is greater than or equal to 7
```swift
class Book {
var title:String
var author:String
var rating:Double

init (title:String, author:String, rating:Double) {
self .title = title
self .author = author
self .rating = rating
}

func isGood () -> Bool {
if rating >= 7 {
return true
}else {
return false
}
}
}

var favoriteBook = Book(title: "Harry Potter", author: "J. K. Rowling", rating: 9.2)

favoriteBook.isGood()
```

## Question 8

```swift
class Dog {

}
```

Work through the following tasks one by one, in order. Each time, add to the `Dog` class above. Each task has sample output that you should be able to replicate when you are done.

a. Give `Dog` four properties, all with default values: `name (string), breed (string), mood (string), and hungry (boolean)`.

```swift
var dog1 = Dog()
dog1.name //returns "dog"
dog1.breed //returns "unknown"
dog1.mood //returns "calm"
dog1.hungry //returns false
```
```swift
class Dog {

var name = "dog"
var breed = "unknown"
var mood = "calm"
var hungry = false
}
```

b. Add an `init` method so that you can initialize new dogs with values for name, breed, mood, and hungry. It should still have the same default values for these properties

```swift
var dog2 = Dog(name: "Oreo", breed: "English Setter", mood: "excited", hungry: true)
dog2.name //returns "Oreo"
dog2.breed //returns "English Setter"
dog2.mood //returns 'excited'
dog2.hungry //returns true
```
```swift
class Dog {

var name:String
var breed:String
var mood:String
var hungry:Bool

init (name:String, breed:String, mood:String, hungry:Bool) {
self .name = name
self .breed = breed
self .mood = mood
self .hungry = hungry
}
}
var dog2 = Dog(name: "Oreo", breed: "English Setter", mood: "excited", hungry: true)
dog2.name
dog2.breed
dog2.mood
dog2.hungry
```
c. Add an instance method called `playFetch()`. It should set the dog's `hungry` property to `true`, set its mood property to `playful`, and print "Ruff!"

```swift
var dog3 = Dog(name: "Rhett", breed: "English Setter", mood: "excited", hungry: false)
dog3.hungry //returns false
dog3.mood //returns "excited"
dog3.playFetch() //prints "Ruff!"
dog3.hungry //returns true
dog3.mood //returns "playful"
```

```swift
class Dog {

var name:String
var breed:String
var mood:String
var hungry:Bool

init (name:String, breed:String, mood:String, hungry:Bool) {
self .name = name
self .breed = breed
self .mood = mood
self .hungry = hungry
}
func playFetch() {
self .hungry = true
self .mood = "playful"
print("wolf")
}
}

var dog3 = Dog(name: "Rhett", breed: "English Setter", mood: "excited", hungry: false)
dog3.hungry 
dog3.mood
dog3.playFetch()
dog3.hungry
dog3.mood

```

d. Add an instance method called `feed()`. If the dog is hungry, it should set `hungry` to `false` and print "Woof!" If the dog is not hungry, it should print "The dog doesn't look hungry"

```swift
var dog4 = Dog(name: "Partner", breed: "Golden Retriever", mood: "thoughtful", hungry: true)
dog4.hungry //returns true
dog4.feed() //prints "Woof!"
dog4.hungry //returns false
```

```swift
class Dog {

var name:String
var breed:String
var mood:String
var hungry:Bool

init (name:String, breed:String, mood:String, hungry:Bool) {
self .name = name
self .breed = breed
self .mood = mood
self .hungry = hungry
}
func playFetch() {
self .hungry = true
self .mood = "playful"
print("wolf")
}
func feed () {
if hungry == true {
self .hungry = false
}
print("wolf")
}

}


var dog4 = Dog(name: "Partner", breed: "Golden Retriever", mood: "thoughtful", hungry: true)
dog4.hungry //returns true
dog4.feed() //prints "Woof!"
dog4.hungry //returns false
```

e. Add an instance method called `toString` that returns a `String` type description of the dog:

```swift
var dog5 = Dog(name: "Rascal", breed: "Golden Retriever", mood: "feeling pawesome", hungry: true)
print(dog5.toString())
//prints:
//Name: Rascal
//Breed: Golden Retriever
//Mood: feeling pawesome
```

```swift
class Dog {

var name:String
var breed:String
var mood:String
var hungry:Bool

init (name:String, breed:String, mood:String, hungry:Bool) {
self .name = name
self .breed = breed
self .mood = mood
self .hungry = hungry
}
func playFetch() {
self .hungry = true
self .mood = "playful"
print("wolf")
}
func feed () {
if hungry == true {
self .hungry = false
}
print("wolf")
}
func toString()-> String {
return "This dogs name is \(name), its breed is \(breed) and its \(mood)"

}

}

var dog5 = Dog(name: "Rascal", breed: "Golden Retriever", mood: "feeling pawesome", hungry: true)
print(dog5.toString())
```

f. Add a type property called `count` that keeps track of how many dogs have been created so far.

//Ex: There have been five dogs created so far
`Dog.count //returns 5`

```swift
class Dog {

var name:String
var breed:String
var mood:String
var hungry:Bool
static var count = 0

init (name:String, breed:String, mood:String, hungry:Bool) {
self .name = name
self .breed = breed
self .mood = mood
self .hungry = hungry
Dog.count += 1
}
func playFetch() {
self .hungry = true
self .mood = "playful"
print("wolf")
}
func feed () {
if hungry == true {
self .hungry = false
}
print("wolf")
}
func toString()-> String {
return "This dogs name is \(name), its breed is \(breed) and its \(mood)"

}
}

var dog5 = Dog(name: "Rascal", breed: "Golden Retriever", mood: "feeling pawesome", hungry: true)
var dog2 = Dog(name: "Rascal", breed: "Golden Retriever", mood: "feeling pawesome", hungry: true)
class count:Dog {

}

```

## Question 9

There are three common scales that are used to measure temperature: Celsius, Fahrenheit, and Kelvin:

C = (F - 32) / 1.8
F = 1.8 * C + 32
K = C + 273

a. Make a struct called `FreezingPoint` that has three properties: `celsius`, `fahrenheit`, and `kelvin`. Give them all default values equal to the freezing point of water.

```swift
struct FreezingPoint {
var celsius = 0.0
var fahrenheit = 32.0
var kelvin = 273.2

}
```
b. Make a struct called `Celsius` that has three properties: `celsius`, `fahrenheit`, and `kelvin`. Give `celsius` a default value of `0.0`, and make the values of `fahrenheit` and `kelvin` correct values, converted from the `celsius` property.

```swift
var tenDegreesCelsius = Celsius(celsius: 10.0)
tenDegreesCelsius.celsius //returns 10.0
tenDegreesCelsius.kelvin //returns 283.0
tenDegreesCelsius.fahrenheit //returns 50.0
```

```swift
struct Celsius {
var celsius = 0.0
var fahrenheit = Double()
var kelvin = Double()

init (celsius:Double){
fahrenheit = 1.8 * celsius + 32
kelvin = celsius + 273
}
}

var tenDegreesCelsius = Celsius(celsius: 10.0)
tenDegreesCelsius.celsius //returns 10.0
tenDegreesCelsius.kelvin //returns 283.0
tenDegreesCelsius.fahrenheit //returns 50.0
```
c. Give the `Celsius` struct a method called `isBelowFreezing` that returns a `Bool` (true if the temperature is below freezing).
```swift
struct Celsius {
var celsius = 0.0
var fahrenheit = Double()
var kelvin = Double()

init (celsius:Double){
fahrenheit = 1.8 * celsius + 32
kelvin = celsius + 273
}
func isBelowFreezing () -> Bool{
if celsius <= 0.0 {
return true
}else{
return false
}

}
}

let temp = Celsius.init(celsius: 10.0).isBelowFreezing()
```

## Question 10

Create a struct called `RGBColor` that has 3 properties, `red`, `green`, `blue` that are all of type `Double`.

Given the below array of color dictionaries, create an array of `RGBColor`.

```swift
let colorDictArray: [[String: Double]] = [["red": 1.0, "green": 0.0, "blue": 0.0],
 ["red": 0.0, "green": 1.0, "blue": 0.0],
 ["red": 0.0, "green": 0.0, "blue": 1.0],
 ["red": 0.6, "green": 0.9, "blue": 0.0],
 ["red": 0.2, "green": 0.2, "blue": 0.5],
 ["red": 0.5, "green": 0.1, "blue": 0.9],]
```

```swift
struct RGBColor {
var red:Double
var green:Double
var blue: Double
}
var colorRGBArray = [RGBColor]()
for dict in colorDictArray {
colorRGBArray += [RGBColor(red: dict["red"]!, green: dict["green"]!, blue: dict["blue"]!)]
}
```

## Question 11

a. Create a class called `Movie` that has properties for `name` (`String`), `year` (`Int`), `genre` (`String`), `cast` (`[String]`), and `description` (`String`). Create an instance of your `Movie` class

```swift
class Movies {
var name:String
var year:Int
var genre:String
var cast:[String]
var discription:String

init (name:String, year:Int, genre:String, cast:[String], discription:String){
self .name = name
self .year = year
self .genre = genre
self .cast = cast
self .discription = discription
}
}

var bestMovieEver = Movies(name: "Avengers EndGame", year: 2019, genre: "Action", cast: ["mike, fredlyne"], discription: "best movie ever")
```

b. Create an instance method inside `Movie` called `blurb` that returns a formatted string describing the movie.

```swift
class Movies {
var name:String
var year:Int
var genre:String
var cast:[String]
var discription:String

init (name:String, year:Int, genre:String, cast:[String], discription:String){
self .name = name
self .year = year
self .genre = genre
self .cast = cast
self .discription = discription
}
func blurb () -> String {

let discriptions =  "\(name) came out in \(year). It was an good film starring \(cast) and it was the \(discription)"
return discriptions
}
}

var bestMovieEver = Movies(name: "Avengers EndGame", year: 2019, genre: "Action", cast: ["mike, fredlyne"], discription: "best movie ever")

```

Ex: "Borat came out in 2006. It was an odd film starring Sacha Baron Cohen as a man named Borat who was visiting America from Kazakhstan."


## Question 12

Create a function outside of your `Movie` class called `makeMovie` that takes in a dictionary of type `[String: Any]`, like `dieHardDict` below, and returns an `optional Movie`. Use `dieHardDict` to create an instance of a `Movie`.

```swift
let dieHardDict: [String: Any] = ["name": "Die Hard",
 "year" : 1987,
 "genre": "action",
 "cast": ["Bruce Willis", "Alan Rickman"],
 "description": "John Mclain saves the day!"]
```

Hint: To use a value type `Any`, you will need to cast it to its expected type.

Below, `nameAsAny` is of type `Any` because thats the type of the value in the dictionary:

```swift
if let nameAsAny = dieHardDict["name"] {
 print(nameAsAny)
}
```

Below, `nameAsString` is of type `String` because the optional binding is attempting to cast it as a `String`.

```swift
if let nameAsString = dieHardDict["name"] as? String {
 print(nameAsString)
}
```

If the binding fails it returns `nil`. `1987` cannot be cast as a `String` because it is a number.

```swift
if let yearAsString = dieHardDict["year"] as? String {
 print(yearAsString)
} else {
 print("this didn't work")
}
```

```swift
let dieHardDict: [String: Any] = ["name": "Die Hard",
"year" : 1987,
"genre": "action",
"cast": ["Bruce Willis", "Alan Rickman"],
"description": "John Mclain saves the day!"]

class Movies {
var name:String
var year:Int
var genre:String
var cast:[String]
var discription:String

init (name:String, year:Int, genre:String, cast:[String], discription:String){
self .name = name
self .year = year
self .genre = genre
self .cast = cast
self .discription = discription
}
func blurb () -> String {

let discriptions =  "\(name) came out in \(year). It was an good film starring \(cast) and it was the \(discription)"
return discriptions
}
}


func makeMovie (movie:[String:Any]) -> Movies? {

return Movies(name: movie["name"] as! String, year: movie["year"] as! Int, genre: movie["genre"] as! String, cast: movie["cast"] as! [String], discription: movie["description"] as! String)
}

var goodMovie = makeMovie(movie: dieHardDict)

```

## Question 13

Given the below array of movie dictionaries, use your function from the last question to create a `Array` of `Movie`.

```swift
// movies is an Array of Dictionaries
// each element of movies is a Dictionary with the keys
// 'name','year', 'genre', 'cast' and 'description'
var movies: [[String:Any]] = [
 [
 "name": "Minions",
 "year": 2015,
 "genre": "animation",
 "cast": ["Sandra Bullock", "Jon Hamm", "Michael Keaton"],
 "description": "Evolving from single-celled yellow organisms at the dawn of time, Minions live to serve, but find themselves working for a continual series of unsuccessful masters, from T. Rex to Napoleon. Without a master to grovel for, the Minions fall into a deep depression. But one minion, Kevin, has a plan."
 ],
 [
 "name": "Shrek",
 "year": 2001,
 "genre": "animation",
 "cast": ["Mike Myers", "Eddie Murphy", "Cameron Diaz"],
 "description": "Once upon a time, in a far away swamp, there lived an ogre named Shrek whose precious solitude is suddenly shattered by an invasion of annoying fairy tale characters. They were all banished from their kingdom by the evil Lord Farquaad. Determined to save their home -- not to mention his -- Shrek cuts a deal with Farquaad and sets out to rescue Princess Fiona to be Farquaad\"s bride. Rescuing the Princess may be small compared to her deep, dark secret."
 ],
 [
 "name": "Zootopia",
 "year": 2016,
 "genre": "animation",
 "cast": ["Ginnifer Goodwin", "Jason Bateman", "Idris Elba"],
 "description": "From the largest elephant to the smallest shrew, the city of Zootopia is a mammal metropolis where various animals live and thrive. When Judy Hopps becomes the first rabbit to join the police force, she quickly learns how tough it is to enforce the law."
 ],
 [
 "name": "Avatar",
 "year": 2009,
 "genre": "action",
 "cast": ["Sam Worthington", "Zoe Saldana", "Sigourney Weaver"],
 "description": "On the lush alien world of Pandora live the Na\"vi, beings who appear primitive but are highly evolved. Because the planet\"s environment is poisonous, human/Na\"vi hybrids, called Avatars, must link to human minds to allow for free movement on Pandora. Jake Sully, a paralyzed former Marine, becomes mobile again through one such Avatar and falls in love with a Na\"vi woman. As a bond with her grows, he is drawn into a battle for the survival of her world."
 ],
 [
 "name": "The Dark Knight",
 "year": 2008,
 "genre": "action",
 "cast": ["Christian Bale", "Heath Ledger", "Aaron Eckhart"],
 "description": "With the help of allies Lt. Jim Gordon and DA Harvey Dent, Batman has been able to keep a tight lid on crime in Gotham City. But when a vile young criminal calling himself the Joker suddenly throws the town into chaos, the caped Crusader begins to tread a fine line between heroism and vigilantism."
 ],
 [
 "name": "Transformers",
 "year": 2007,
 "genre": "action",
 "cast": ["Shia LaBeouf", "Megan Fox", "Josh Duhamel"],
 "description": "The fate of humanity is at stake when two races of robots, the good Autobots and the villainous Decepticons, bring their war to Earth. The robots have the ability to change into different mechanical objects as they seek the key to ultimate power. Only a human youth, Sam Witwicky can save the world from total destruction."
 ],
 [
 "name": "Titanic",
 "year": 1997,
 "genre": "drama",
 "cast": ["Leonardo DiCaprio", "Kate Winslet", "Billy Zane"],
 "description": "The ill-fated maiden voyage of the R.M.S. Titanic; the pride and joy of the White Star Line and, at the time, the largest moving object ever built. She was the most luxurious liner of her era -- the \"ship of dreams\" -- which ultimately carried over 1,500 people to their death in the ice cold waters of the North Atlantic in the early hours of April 15, 1912."
 ],
 [
 "name": "The Hunger Games",
 "year": 2012,
 "genre": "drama",
 "cast": ["Jennifer Lawrence", "Josh Hutcherson", "Liam Hemsworth"],
 "description": "Katniss Everdeen voluntarily takes her younger sister\"s place in the Hunger Games, a televised competition in which two teenagers from each of the twelve Districts of Panem are chosen at random to fight to the death."
 ],
 [
 "name": "American Sniper",
 "year": 2014,
 "genre": "drama",
 "cast": ["Bradley Cooper", "Sienna Miller", "Kyle Gallner"],
 "description": "Navy S.E.A.L. sniper Chris Kyle\"s pinpoint accuracy saves countless lives on the battlefield and turns him into a legend. Back home to his wife and kids after four tours of duty, however, Chris finds that it is the war he can\"t leave behind."
 ]
]
```
```swift

class Movies {
var name:String
var year:Int
var genre:String
var cast:[String]
var discription:String

init (name:String, year:Int, genre:String, cast:[String], discription:String){
self .name = name
self .year = year
self .genre = genre
self .cast = cast
self .discription = discription
}
func blurb () -> String {

let discriptions =  "\(name) came out in \(year). It was an good film starring \(cast) and it was the \(discription)"
return discriptions
}
}


func makeMovie (movie:[String:Any]) -> [Movies]{
var movieArray = [Movies]()
for _ in movie{
movieArray += [Movies(name: movie["name"] as! String, year: movie["year"] as! Int, genre: movie["genre"] as! String, cast: movie["cast"] as! [String], discription: movie["description"] as! String)]
}
return movieArray
}
```
