
## Classes, Attributes & Constructors

```
class Book {
	author;
	title; 

    constructor(author, title,){
        this.author = author;
        this.title = title;
    }

}
```
or much better directly
```
class Book {
    constructor(author, title, pages) {
        this.author = author;
        this.title = title;
    }
}
```
## Methods

```
class Book {
    constructor(author, title) {
        this.author = author;
        this.title = title;
    }

    //methods to set

    setAuthor(newAuthor) {
        this.author = newAuthor;
    }

    setTitle(newTitle) {
        this.title = newTitle;
    }

    // methods to get

    getAuthor() {
        return this.author;
    }

    getTitle() {
        return this.title;
    }
}

const myBook = new Book("Gege akutangina", "Jujutsu Sukuna vs. All"); //Creating an Instance

console.log(myBook.getAuthor());  //outputs an existing author
console.log(myBook.getTitle());   //outputs an existing title

myBook.setAuthor("Kanehito Yamada");
myBook.setTitle("Frieren: Beyond Journey's End");

console.log(myBook.getAuthor()); //outputs a new author
console.log(myBook.getTitle()); //outputs a new title
```

## Inheritance & Objects
```
class Book {
    constructor(author, title) {
        this.author = author;
        this.title = title;
    }
}

class Manga extends Book {
    constructor(author, title) {
        super(author, title); // Constructor from parent class
    }
}

const myManga = new Manga("Gege Akutangina", "Jujutsu Sukuna vs. All");
console.log("Author:" + " " + myManga.author);
console.log("Title:" + " " + myManga.title);
```

let's make it separated

```
// book.js
class Book {
    constructor(author, title, pages) {
        this.author = author;
        this.title = title;
        this.pages = pages;
    }
}
```
```
// manga.js
class Manga extends Book {
    constructor(author, title, fandom) {
        super(author, title); // Call the constructor of the parent class
        this.fandom = fandom;
    }
}
```
```
//In HTML file
<script>
    const myManga = new Manga("Gege Akutangina", "Jujutsu Sukuna vs. All");
    console.log("Author:" + " " + myManga.author);
    console.log("Title:" + " " + myManga.title);
</script>
```
## Encapsulation
```
class Book {
	author; //public
	_title; //protected
	#pages; //private

    constructor(author, title, pages){
        this.author = author;
        this._title = title;
        this.#pages = pages;
    }

}
```
make it work
```
class Book {
    constructor(author, title, pages) {
        this.author = author; // can access anywhere in the world :D
        this._title = title; //can access within the class and it's subclasses
        // this.#pages = pages; //can't access outside it's class
    }
}

class Manga extends Book {
    constructor(author, title, pages, fandom) {
        super(author, title, pages); // Constructor from parent class
        this.fandom = fandom; //specific values for manga only
    }
}

const myManga = new Manga("Gege Akutangina", "Jujutsu sukuna vs. all", 200, "Mga baliw na");
console.log("Author:" + " " + myManga.author);
console.log("Title:" + " " + myManga._title);
// console.log("Pages:" + " " + myManga.#pages); // Error - private field
console.log("Fandom:" + " " + myManga.fandom);
```

## Abstraction

```
class Book {
    constructor(author, title, pages) {
        this.author = author;
        this._title = title;
        this.pages = pages;
    }

    // Abstract method to display basic information
    displayInfo() {
        console.log(`Title: ${this.getTitle()}`);
        console.log(`Author: ${this.author}`);
        console.log(`Pages: ${this.pages}`);
    }

    // Abstract method to get the title
    getTitle() {
        return this._title;
    }
}

class Manga extends Book {
    constructor(author, title, pages, fandom) {
        super(author, title, pages); // Constructor from parent class
        this.fandom = fandom; // Specific values for manga only
    }

    // Override the displayInfo method to include manga-specific details
    displayInfo() {
        super.displayInfo(); // Call the parent's displayInfo method
        console.log(`Fandom: ${this.fandom}`);
    }
}

const myManga = new Manga("Gege Akutangina", "Jujutsu sukuna vs. all", 200, "Mga baliw na");
myManga.displayInfo(); // Output manga information in a simplified manner
```
## Polymorphism

two types of behaviors

### 1.Method Overriding
```
class Book {
    constructor(author, title) {
        this.author = author;
        this.title = title;
    }

    availability(){
        return console.log('available')
    }
}

class Manga extends Book {
    constructor(author, title) {
        super(author, title); // Constructor from parent class
    }

    availability(){
        return console.log('not available')
    }
}

const myManga = new Manga("Gege Akutangina", "Jujutsu Sukuna vs. All");
console.log("Author:" + " " + myManga.author);
console.log("Title:" + " " + myManga.title);
myManga.availability(); // throws not available
```


### 2.Method Overloading (not applicable to javascript the same way as java or other)

```
class Book {
    constructor(author, title) {
        this.author = author;
        this.title = title;
    }

    availability(x) {
        if (typeof x === 'undefined') {
            console.log('not available');
        } else {
            console.log("the available pieces are: " + x);
        }
    }
}

class Manga extends Book {
    constructor(author, title) {
        super(author, title); // Constructor from parent class
    }
}

const myManga = new Manga("Gege Akutangina", "Jujutsu Sukuna vs. All");
console.log("Author:" + " " + myManga.author);
console.log("Title:" + " " + myManga.title);
myManga.availability();    // Output: not available
myManga.availability(159); // Output: the available pieces are: 159
```

## Summary

in this summary, Object Class, Objects, Attributes, Methods & Constructors are all implemented in one go.
try running the whole code below here: [copy the code below and paste here](https://www.w3schools.com/js/tryit.asp?filename=tryjs_object_constructor1)

```
<!DOCTYPE html>
<html>
	<body>
	
	<h1>OOP</h1>
	<h3>JavaScript Object Class, Objects, Attributes, Methods & Constructors.</h3>
	
	<p id="guard"></p>
	<p id="agility"></p>
	
	<script>
	
	// Class function for Dog
	class Dog {
		// Constructor function for Dog objects
	    constructor(name, kind) {
	        this.name = name;
	        this.kind = kind;
	    }
	    
	    toBark(){
	    	return alert('Bark');
	    }
	}
	
	class GuardDog extends Dog {
	    constructor(name, kind, combatYears) {
	        super(name, kind); // Constructor from parent class
	        this.combatYears = combatYears;
	    }
	    
	    toFight(){
	    	return alert('Fighting')
	    }
	}
	
	class AgilityDog extends Dog {
		constructor(name, kind, speed){
	    	super(name, kind);
	        this.speed = speed;
	    }
	    
	    toRace(){
	    	return alert('Running')
	    }
	}
	
	// Create Dog objects
	const guard = new GuardDog("Bruno", "K9", "3 years");
	const agility = new AgilityDog("Collie", "Border Collies", "25mph");
	
	guard.toBark();
	agility.toBark();
	guard.toFight();
	agility.toRace();
	
	// Display Dog
	document.getElementById("guard").innerHTML =
	"My Dog's name is " + guard.name + ", he is a " + guard.kind + " and in service for for " + guard.combatYears + "."; 
	
	document.getElementById("agility").innerHTML =
	"My Dog's name is " + agility.name + ", he is a " + agility.kind +" and the fastest dog in the contest with a record of " + agility.speed + ".";
	
	</script>
	
	</body>
</html>
``
