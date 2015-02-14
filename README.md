# Quick and dirty introduction to Ruby

#### Preparation.

To work through these examples, you will need a working ruby environment on your machine. Installation steps differ depending on which version of Windows or OS X or which Linux or Unix distribution you are running, on which package manager you are using (if any), whether you are using a ruby version manager such as rvm or rbenv, and whether you are using an integrated development environment (IDE). All of that is out of scope for this document. We will assume you have a working ruby environment you can play with. 

#### 1. Traditional first program.

Open a terminal window or command-line window and enter:

```ruby
irb
```

That will start the interactive ruby processor. Irb is a read-evaluate-print-loop (repl) program. You can type ruby statements into irb and it will display the output from those statements on the console. Try typing the following and see what happens:

```ruby
'Hello, world'
```

There, you've just written your first program. Congratulations, you're a ruby expert! 

By the way, when you want to stop irb, enter 'quit'.

#### 2. Standard I/O streams.

All operating systems support three basic I/O streams: standard input, standard output, and standard error. They are often named stdin, stdout, and stderr, although the names may vary from one operating system to another or from one programming language to another. When you type input into irb, the tool reads your input from standard input and it writes to standard output. 

When you write ruby code outside of a repl, you have to write ruby statements to write output. You can do that inside irb, as well. Here is how to write to the standard output stream. (People usually pronounce 'puts' "put ess"). Try this:

```ruby
STDOUT.puts 'Hello, world'
```

Notice the return value is nil, meaning 'no value'. This means the 'puts' command does not return a value to the caller. The output itself is a 'side effect'.

#### 3. STDOUT is assumed by default.

```ruby
puts 'Hello, world'
```

##4. Write to the standard error stream.

```ruby
STDERR.puts 'Hello, world'
```

#### 5. Say hello to yourself or someone else. 

You can substitute your name or any other name for 'John' if you wish.

```ruby
puts 'Hello, John'
```

#### 6. String concatenation.

```ruby
puts 'Hello, ' + 'John'
```

#### 7. Declare a variable and assign a value to it.

```ruby
my_name = 'John'
```

#### 8. Display the contents of a variable.

```ruby
puts my_name
```

#### 9. Concatenate a literal string with the value of a variable.

```ruby
puts 'Hello, ' + my_name
```

#### 10. String interpolation

Insert string values into another string. Useful for formatting messages.

```ruby
puts "Hello, #{my_name}"
```

#### 11. Expressions.

Ruby evaluates expressions and returns their value. You have been doing this all along.

In step 1, you wrote 'Hello, world' and ruby returned 'Hello, world'. That is a simple expression - its value is just 'Hello, world'

In step 6, you wrote 

puts 'Hello, ' + 'John'

Here's what happened:

a. Ruby evaluated the expression Hello, ' + 'John and returned the result 'Hello, John'. 
b. Ruby passed the result 'Hello, John' to puts.
c. puts displayed the value on stdout. 

Here are some more expressions you can try. (Now that you understand what's going on, you don't have to keep typing 'puts' while you're in irb unless you want to.)

```ruby
5 + 6
2 * (3 + 5)
```

Notice the expressions 'Hello, ' + 'John' and 5 + 6 both use the '+' operator, but it has a different effect in each case. Ruby knows that adding two string means sticking the values together, and adding two numbers means to perform arithmetic addition on the numbers. 

#### 12. Operator precedence.

Ruby applies operators in a certain order when it evaluates expressions. The order is called 'operator precedence'.  

```ruby
2 * 3 + 5
2 * (3 + 5)
```

Ruby reads left to right and applies arithmetic operators * and / first, and then operators + and -. That is the default operator precedence. To override this, use parentheses to group the operations you want to occur first. 

```ruby
2 * (3 + 5)
2 * 30 / 6 + 4
2 * (30 / (6 + 4))
```

Notice the results of evaluating the three expressions above. Ruby evaluates expressions in the innermost parentheses first and works its way outward until the whole expression has been evaluated.

#### 13. Everything is an object. 

Objects are instances of classes. Each object has a method named 'class' that reports the name of its class.

```ruby
puts 'Hello'.class
```

#### 14. A class is like the script for a play. An object is like a performance of the play. 

All performances of Hamlet are based on the script of Hamlet, but each performance is unique.

```ruby
string1 = 'one'
string2 = 'two'

puts string1.class
puts string1

puts string2.class
puts string2
```

From the output you can surmise that every string object is a member of the String class, and every instance of the String class is a separate object. 

#### 15. An object has 'identity'. 

This is how ruby can tell different instances of a class apart. These objects are of the same class, but have different identities.

```ruby
puts string1.object_id
puts string2.object_id
```

Every ruby object has a method named 'object_id' that returns its object_id. (Other languages might identify objects in other ways.)

#### 16. An object has 'members'. 

Members include fields that contain values and methods that perform operations on the object.

```ruby
puts string1.methods
puts string1.methods.sort
puts string1.size
```

#### 17. Numbers are objects, too. 

```ruby
puts 5.class
puts 5.methods.sort
puts 5.size

my_num = 5
puts my_num.class
puts my_num.methods.sort
puts my_num.size
```

From the output you can see that a literal number is an object, and a variable that contains a numerical value is also an object. In ruby, everything is an object.

Now you know:

a. Ruby is an object-oriented language.
b. Everything in ruby is an object.
c. The characteristics of an object are defined by its class. (An object's class is sometimes called its 'type'.)
d. Every object has three key properties: identity, state, and operations.
e. An object's identity distinguishes it from all other objects in memory.
f. An object's state comprises the current values of all its data members (fields).
g. An object's operations are blocks of code that modify or report the object's state.

#### 18. Why does 5.size return 8 and not 5?  

Ruby creates an object of the appropriate class depending on the value of the number.

```ruby
puts 5.class
puts 5.size
puts 1234567890123456.class
puts 1234567890123456.size
puts 123456789012345678901234.class
puts 123456789012345678901234.size
```

A floating-point number doesn't have a 'size' method

```ruby
puts 12.55.class
puts 12.55.size
```

Ruby dynamically changes the type of object so the value will fit into the variable.

```ruby
my_num = 1234567890123456
puts my_num.class
my_num = 123456789012345678901234
puts my_num.class
```

#### 19. Converting between integer and string types.

```ruby
puts 'Hello ' + 4
puts 'Hello ' + 4.to_s

puts 5 + '4'
puts 5 + '4'.to_i
```

In this context, ruby automatically converts the value of my_num into a string:

```ruby
my_num = 5
puts "I have #{my_num} kittens."
```

Now you know:

a. Ruby is a dynamically-typed language.
b. A dynamically-typed language determines the appropriate class for each object by examining its contents.
c. You don't have to declare the type or class of variables in a dynamically-typed language.
d. Within certain limits, a dynamically-typed language can convert the type of a variable from one class to another depending on how the variable is used.
e. When ruby can't guess how to convert the type of a variable, you can call a method on the variable to convert it explicitly to another type, provided the particular conversion makes sense. 


#### 20. You can define your own methods.

```ruby
def add (number1, number2)
  result = number1 + number2  
  return result
end

add(2, 3)
```

#### 21. Simplification: Parentheses are optional... 

...except in cases when their absence would confuse the compiler.

```ruby
def add number1, number2
  result = number1 + number2  
  return result
end

add 2, 3
```

When we append another method call to the result of the first method call, we have to enclose the arguments in parentheses so ruby will know where the first expression ends:

```ruby
add(2, 3).class
```

#### 22. Simplification: You don't need a separate variable for the result of a method.

```ruby
def add number1, number2  
  return number1 + number2
end

add 2, 3
```

#### 23. Simplification: You don't always need a 'return' statement.

A ruby method returns the last value it evaluated, whatever that may be. So, you can omit the 'return' statement in most cases.

```ruby
def add number1, number2  
  number1 + number2
end

add 2, 3
```

In the example above, the last expression evaluated in method 'add' is 'number1 + number2', so that is the value returned from the method.

#### 24. If you need to return from the middle of a method, you need a 'return' statement.

```ruby
def add_positive number1, number2
  if number1 < 0
    return "First number can't be negative"
  elsif number2 < 0
    return "Second number can't be negative"  
  else
    number1 + number2
  end
end

add_positive -4, 5
add_positive 4, -5
add_positive 4, 5
```

Now you know:

1. You can define a method in ruby with the 'def' statement.
1. All the statements between the 'def' and the matching 'end' statements are part of the method.
1. A method is part of a class.
1. A method has a name.
1. A method accepts zero or more arguments.
1. A method returns zero or 1 results.
1. When a method doesn't return a value, ruby treats the result as 'nil' (no value).

#### 25. You can process a list of values (array).

```ruby
arr1 = [ 3, 5, 2, 14, 6, -9 ]
puts arr1.class
puts arr1.methods.sort
puts arr1
puts arr1.sort
puts arr1.shuffle
puts arr1.shuffle
```

Arrays can contain other types besides numbers:

```ruby
arr2 = [ 'Rajesh', 'Ping', 'Susan', 'Martina' ]
```

Array elements can be of different types:

```ruby
arr3 = [ 5.25, 'Steven', true, -75 ]
```

#### 26. Access a specific element in an array.

```ruby
puts arr1[2]
```

#### 27. Convert an array into a string.

```ruby
str1 = arr1.to_s

puts arr1[2]
puts str1[2]
```

#### 28. Create an empty array and add elements to it.

```ruby
arr1 = []
puts arr1.length
puts arr1

arr1[0] = 1
puts arr1.length
puts arr1
puts arr1[0]

arr1[2] = 3
puts arr1.length
puts arr1
puts arr1[0]
puts arr1[1]
puts arr1[2]
```

#### 29. Another way to add elements to an array.

```ruby
arr1 = []
arr1 << 1
arr1 << 2
arr1 << 3
puts arr1.length
puts arr1
```

#### 30. Iterating over an array. 

```ruby
arr1 = [1, 2, 3, 4, 5]
arr1.each { |x| puts x }
arr1.each { |x| puts x * 2 }

arr1.each do |x|
  puts x * 2
end
```

#### 31. Arrays within arrays (multidimensional arrays).

```ruby
arr1 = [1, 2, 3]
arr2 = ['foo', 'bar', arr1]

puts arr2[2][1]
```

Now you know:

1. To process a list of values, you can use an array.
1. You can refer to any element in the array by using its index.
1. Array elements can be of any type - include other arrays.
1. Arrays have a method named 'each' that functions as an iterator. You can pass a block of code into 'each', and it will execute that block once for each element in the array.

#### 32. You can store a list of values with keys.

In Ruby this is called a hash. Other languages call the same kind of structure a dictionary, a map, or a list of key-value pairs.

```ruby
hash1 = { 'key1' => 'value1', 'key2' => 'value2' }
```

The keys and values may be any type of object:

```ruby
hash1 = { 'key1' => 'value1', 'key2' => 2, 'key3' => [5, 4, 3] }
```

#### 33. Retrieve an element from a hash by its key.

```ruby
value1 = hash1['key2']
```

This works because ruby stores the hash keys in an array:

```ruby
hash1.keys
hash1.keys[1]
```

Ruby also stores the hash values in an array:

```ruby
hash1.values
hash1.values[1]
```

But it's more convenient to use the keys to retrieve the values.

```ruby
hash1['key2']
```

#### 34. Add elements to a hash.

```ruby
hash1 = {}
hash1['one'] = 1
hash1['two'] = 2
```

#### 35. Merge the contents of two hashes.

```ruby
hash1 = {}
hash1['one'] = 1
hash1['two'] = 2

hash1.merge 'three' => 3, 'four' => 4
hash1
```

#### 36. Process the elements in a hash.

```ruby
hash1.keys.each { |key| puts hash1[key] }
```

```ruby
hash1.keys.each do |key| 
  puts hash1[key]
end  
```

#### 37. Symbols.

When you need to use a string value as some sort of label or key that never changes, you can gain a little efficiency by using a symbol rather than a string object. A symbol comprises a colon followe by its string value, without quotes.

```ruby
String looks like this: 'key1'
Symbol looks like this: :key1
```

A symbol is immutable - you can't change its value. So, you can't do this:

```ruby
:key1 = 'something'
```

You can use symbols as the keys in a hash:

```ruby
hash1['one'] = 1

hash1[:one] = 1
```

You can convert between string and symbol types:

```ruby
:hey.class
value1 = :key.to_s
value1.class
value1.to_sym.class
```

#### 38. Iterators, loops.

```ruby
5.times do |i|
  i * 2
end

[1, 2, 3, 4, 5].each do |i|
  i * 2
end
```

#### 39. Boolean values.

Ruby represents boolean values with 'true' and 'false' objects.

```ruby
true.class
true.methods
false.class
false.methods
```

#### 40. Conditional expressions.

Conditional expressions return true or false values.

```ruby
5 > 4
5 < 4

val1 = 18
val2 = 7 * 3
puts 'val1 is larger' if val1 > val2
puts 'val2 is larger' if val2 > val2

if val1 > val2
  puts 'val1 is larger'
elsif val2 > val1
  puts 'val2 is larger'  
else
  puts 'val1 and val2 are equal'
end
```

#### 41. You can create your own classes.

```ruby
class Dog
  def bark
    puts 'Woof!'
  end
  def beg
    puts 'Feed me!'
  end
end

fido = Dog.new
fido.bark
fido.beg
```

From this point forward, it will be inconvenient to work in irb. The time has come to save your ruby code in files.

#### 42. Create a ruby project.

If you are using an integrated development environment (IDE), use its project set-up features to create a ruby project. The details are out of scope for this document.

If you are working with a text editor and command line, create a project directory with a couple of subdirectories, like this:

```
ruby_sandbox/
  |
  +-- app/
  |
  +-- spec/
```

#### 43. Creating a ruby class.

Create a file in your application directory named 'dog.rb'. For example, you might create the file in this location:

```
/ruby_sandbox/app/dog.rb
```

Enter the following code in the dog.rb file:

```ruby
class Dog
end

fido = Dog.new
```

It's important to note that the filename is all lowercase, while the class name starts with an uppercase letter.

On a command line or in your IDE, execute that file:

```ruby
cd your-project
ruby app/dog.rb
```

If no output appears on the console, then everything is OK. The program doesn't write any output, so this is expected. If there are error messages, then see if you can diagnose the problem based on the messages.

#### 44. Teach your dog to bark.

```ruby
class Dog
  def bark
    puts 'Woof!'
  end
end

my_dog = Dog.new
my_dog.bark
```

#### 45. Give your dog a name.

```ruby
class Dog
  def initialize name
    @name = name
  end  
  def say_name
    "My name is #{@name}."
  end  
  def bark
    'Woof!'
  end
end

my_dog = Dog.new 'Rover'
puts "My dog says: #{my_dog.say_name} #{my_dog.bark}"
```

#### 46. Teach your dog to come when called.

```ruby
class Dog
  def initialize name
    @name = name
  end  
  def say_name
    "My name is #{@name}."
  end  
  def bark
    'Woof!'
  end
  def come name
    if name == @name
      "My name is #{name}, so I'm coming!"
    else
      "(My name is not #{name}, so I'm ignoring you.)"
    end    
  end
end

my_dog = Dog.new 'Rover'
puts my_dog.come 'Rover'
puts my_dog.come 'Fido'
```

Every ruby class has an 'initialize' method. When you call 'new', the 'initialize' method is called. When you need to initialize objects, you can override the 'initialize' method and place any necessary initialization code there.

47. Your dog is a mammal.

Many kinds of objects belong to some sort of taxonomy of things that have a hierarchical relationship. For example, a dog is a canine; a canine is a mammal; a mammal is an animal; an animal is a living organism. In that example, 'living organism' is the top of a hierarchy of things. 'Animal' and 'plant' inherit many characteristics from 'living organism', and they add unique characteristics as well. 'Mammal', 'lizard', and 'arachnid' are types of 'animal'. They all have common characteristics that they inherit from 'animal' and from 'living organism', and each adds unique characteristics different from the others, as well. You could take it a step further and define each species of dog. A Chihuahua inherits most of its characteristics from Dog, and yet is distinct from a Rottweiler.

In object-oriented programming languages, we represent this kind of hierarchy using a mechanism called 'inheritance'. A class can inherit members from classes above it in a class hierarchy. We say an object 'is-a' Thing when that object's class is Thing or when the Thing class exists anywhere in the class hierarchy above the object. So we would say Dog 'is-a' Canine. We would also say Dog 'is-a' Mammal, and Dog 'is-a' Animal, and so forth. 

Let's start to separate the unique characteristics of Dog from the common characteristics of Mammal. A Dog can do the following things (we'll go ahead and add a few to illustrate the point):

* belongs to a species
* bark
* come when called
* ('say name' is actually a little bit optimistic)
* eat
* sleep
* defecate
* urinate
* mate
* live birth
* run
* jump

To determine which characteristics are unique to Dog and which are common to all Mammals, we can ask ourselves whether all mammals can do each thing.

All Mammals

* belong to a species
* eat
* sleep
* defecate
* urinate
* mate
* vocalize
* give live birth

Dogs

* bark
* come when called
* run
* jump

Create another file for the Mammal class. Call it mammal.rb. Code some of the behaviors of Mammal in the class. There's no need to be comprehensive, as this is only a learning exercise

```ruby
# mammal.rb
class Mammal
  def initialize species
    @species = species
  end
  def say_species
    @species
  end    
  def vocalize
    'Mammal is making a sound'
  end
  def eat
    'Mammal is eating' 
  end
  def sleep
    'Mammal is sleeping'
  end    
end

# dog.rb
require_relative 'mammal'

class Dog < Mammal
  def initialize species, name
    @name = name
  end
  def say_name
    "My name is #{@name}."
  end  
  def bark
    'Woof!'
  end
  def come name
    if name == @name
      "My name is #{name}, so I'm coming!"
    else
      "(My name is not #{name}, so I'm ignoring you.)"
    end    
  end
end

puts 'Dog...'
my_dog = Dog.new 'German Shepherd', 'Rover'
puts my_dog.come 'Rover'
puts my_dog.come 'Fido'
puts my_dog.say_species
puts my_dog.say_name
puts "If I call bark, I get #{my_dog.bark}"
puts "If I call vocalize, I get #{my_dog.vocalize}"

puts 'Species...'
mammal = Mammal.new 'Some sort of mammal'
puts mammal.say_species
puts mammal.vocalize
```

The 'require_relative' declaration at the top of dog.rb tells ruby where to find the mammal.rb file at run time. Whenever your code refers to another source file, you have to tell ruby where to find it.

48. Refer to general definitions rather than specific ones when possible.

The example above calls 'bark' when the dog vocalizes, but a more general method is available in the Mammal class - 'vocalize'. If we change the name of 'bark' to 'vocalize', then ruby will use the dog's version of 'vocalize' when our program refers to a Dog object, and the mammal's version of 'vocalize' when our program refers to a Mammal object.

```ruby
# dog.rb
require_relative 'mammal'

class Dog < Mammal
  def initialize species, name
    @name = name
  end
  def say_name
    "My name is #{@name}."
  end  
  def vocalize
    'Woof!'
  end
  def come name
    if name == @name
      "My name is #{name}, so I'm coming!"
    else
      "(My name is not #{name}, so I'm ignoring you.)"
    end    
  end
end

my_dog = Dog.new
mammal = Mammal.new

puts "If I call my_dog.vocalize, I get #{my_dog.vocalize}"
puts "If I call mammal.vocalize, I get #{mammal.vocalize}"
```

49. A little housekeeping.

We've been calling our application in the same file as our Dog class definition. We really would prefer to separate the definition of the application from the use of the application. Let's create another file, run.rb, to execute our application. That way, the dog.rb file contains the definition of Dog, and nothing else.

```ruby
# dog.rb file
require_relative 'mammal'

class Dog < Mammal
  def initialize species, name
    @name = name
  end
  def say_name
    "My name is #{@name}."
  end  
  def vocalize
    'Woof!'
  end
  def come name
    if name == @name
      "My name is #{name}, so I'm coming!"
    else
      "(My name is not #{name}, so I'm ignoring you.)"
    end    
  end
end

# run.rb file
require_relative 'dog'

my_dog = Dog.new 'Dachshund', 'Godzilla'
mammal = Mammal.new 'Undetermined species'

puts "If I call my_dog.vocalize, I get #{my_dog.vocalize}"
puts "If I call mammal.vocalize, I get #{mammal.vocalize}"
```

Notice the 'require_relative' declaration that tells ruby where to find the file, 'dog.rb'. Why do we not need to tell ruby where to find 'mammal.rb'? Because that declaration is already present in the 'dog.rb' file.

50. Mixing common code into a class.

A module is a collection of methods that can be included with any class. Functionality that is common to many classes can be defined in a module. This allows the common functionality to be re-used in many classes. In ruby terminology, a module that is included in a class is called a 'mixin' because it 'mixes' the code in the module with the code in the class. Client code can treat the methods defined in the module as if they were part of the class.

What if we make Mammal a module and mix it into the Dog class, instead of having Dog inherit from Mammal?

```ruby
# mammal.rb
class Mammal
  def initialize species
    @species = species
  end
  def say_species
    @species
  end    
  def vocalize
    'Mammal is making a sound'
  end
  def eat
    'Mammal is eating' 
  end
  def sleep
    'Mammal is sleeping'
  end    
end

# dog.rb
require_relative 'mammal'

class Dog
  include Mammal

  def initialize species, name
    @name = name
    super species
  end
  def say_name
    "My name is #{@name}."
  end  
  def vocalize
    'Woof!'
  end
  def come name
    if name == @name
      "My name is #{name}, so I'm coming!"
    else
      "(My name is not #{name}, so I'm ignoring you.)"
    end    
  end
end

# run.rb file
require_relative 'dog'
my_dog = Dog.new 'Dachshund', 'Godzilla'
puts "#{my_dog.say_name} I am a #{my_dog.say_species}. #{my_dog.vocalize}"

```

Now you know enough about ruby to get started with real work. In other words, you know enough to be a little bit dangerous. Here are some additional resources to help you become less dangerous:

* [Ruby documentation](http://ruby-doc.org/)
* [Google search for ruby tutorials](https://www.google.com/search?client=ubuntu&channel=fs&q=ruby+tutorial&ie=utf-8&oe=utf-8)
* ['The' ruby gems repository](https://rubygems.org/) 
