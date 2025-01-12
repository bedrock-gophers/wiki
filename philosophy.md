# Philosophy

While this section may seem extremely redundant and not needed, it's important to understand that most Dragonfly users come from other popular softwares - such as Pocketmine-MP and Nukkit.

Although Dragonfly aims to serve the same purpose as these other softwares, they couldn't be more different in how we have to create software using them.

It's important that at the end of this section, main group of users of Dragonfly, takeaway this important lessons:

> For those who have used other softwares and are proficient in its respective language but are new to both Go and Dragonfly:
>> Drop all the good practices you assumed were 'good', most will not apply in the context of Go.

*If you do not fall in this group, you can feel free to skip this section, but it's still a good read nonetheless*

## Language

If you are a developer from softwares like Pocketmine-MP and Nukkit, you are primarily used to programming in an Object-Oriented Programming (OOP) Language (e.g PHP, Java, Kotlin).

One of the biggest problems that you must overcome is to drop the concept of OOP in exchange for Go's more functional style.

Although you are probably akinned to the extremely organized and strict nature of OOP organization, these concepts simply do not work with the good practices of Go and will often backfire at you. This in turn makes your once elegant Go code, into something not so much.

Below, we will give a few examples of examples of paradigms you are used to in Java/PHP, make their bad equivalents in Go, explain why they are bad, and then show the best way to actually implement them in Go!

## Encapsulation

Encapsulation is simply the idea of bundling your data into a class. Consider the following example:

Java:
```java
public class User {
    private String name;

    public User(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```
PHP:
```php
class User {
    private String $name;

    public function __construct(string $name) {
        $this->name = $name;
    }

    public function getName(): string {
        return $this->name;
    }

    public function setName(string $name) {
        $this->name = $name;
    }
}
```

Above are examples of encapsulating a name (with respect to a User class) in both Java/PHP. Below is the **INCORRECT** implementation of this concept in Go.

```go
type User struct {
    name string
}

func (u *User) GetName() string {
    return u.name
}

func (u *User) SetName(name string) {
    u.name = name
}
```

## TODO

### Language
- explain pointer receivers
- explain proper inheritance
- explain bad use cases of interfaces (e.g `IGame`, `IUser`, `IRole`)
- explain polymorphism (similar to inheritance)
- explain not using `Get` paradigm and only making setter functions when necessary
- Coupling arguments into their own class/JSON

### Software
- multi-handler systems
- overengineering a session system
- recreating utility classes from PM/Nukkit into DF (when they already exist)
- overengineering worlds and world handlers
- overengineering