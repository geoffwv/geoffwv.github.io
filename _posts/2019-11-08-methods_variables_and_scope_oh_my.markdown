---
layout: post
title:      "Methods, variables, and scope oh my!"
date:       2019-11-08 12:57:56 -0500
permalink:  methods_variables_and_scope_oh_my
---


Methods, variables and the scope of each are some of the key concepts of the Ruby programming language. Let’s take a look at them and dig into the way they function.

Variables are a means of storing information. They are a container that we can use to hold any type of data. Hashes, strings, arrays, and numbers can all be stored in variables for later use. They’re similar to nouns in that they can define and name things in Ruby.

Variables have several different types that all have their uses:

- Local variable – this is a variable that exists within method or class they’re defined in. Local variables begin with a lowercase letter or underscore. An example of a local variable is, river1 = “Gauley”, which sets the value of river1 to the string “Gauley”

- Instance variable - these can be distinguished from other types of variables by the at symbol, @, that begins their name. They belong to the instance of a class. They are the containers for information specific to that particular instance. @river1 = “Gauley” is an example of the syntax for an instance variable and sets the value of @river1 to the string “Gauley” inside the instance.

- Class variable – this type of variable is available to the entire class on which it’s called. The information stored pertains to the class in its entirety so it can be accessed by both class and instance methods. They easy to spot since they begin with a double at symbol, @@. An example of a class variable is, @@river1= “Gauley”, which sets the value of @@river1 to the string “Gauley” with a class.

- Constants – this variable can’t be defined in a method and their value should remain...well, constant. They’re distinguished by beginning with a capital letter or having the entire name capitalized. A class is a type of constant.

- Global – This is a constant defined outside of classes or methods that can be accessed anywhere in your program. They’re distinguished by beginning with a dollar sign, $. They can make your program difficult to debug since they can be accessed and redefined from anywhere in a program.

Methods are ways to provide functionality to our Ruby objects. Methods allow us as Rubyists to give our program behaviors. They are considered the verbs of the programming language since they allow us to provide action or behavior to our programs.

The two types of methods we will deal with the most frequently are the instance method and the class method. The short definition for the two is that class methods called on a class and instance methods are called on an instance of the class. Class methods use the syntax of the keyword self in the method def line.

Let’s look at some code to see to clear up this explanation:

class River

  def self.location
    puts “Location is a class method.”
  end 

  def rapids
    puts “Rapids is an instance method.”
  end

end

When we call River.location on the River class it works perfectly. The return is #=> Location is a class method.

Calling River.rapids on the other hand, which is an instance method, on the class River produces, #=> undefined method ‘rapids” for River:Class (NoMethodError).

If we create a new instance of the class River with River.new.rapids the return is #=> Rapids is an instance method.

The key here is that instance methods only work with an instance so you need to create a new instance to use them, hence River.new.rapids. 

Finally, let's talk about scope. The scope is where a variable is accessible within a program. There are four types of scope so let’s go back to the code to see how this all works. 

First, there’s local scope. Consider this code:

river = “New”

 def rivers
    river = “Gauley”
 end

puts rivers 

The return here will be #=> “Gauley”. The method rivers doesn’t care what the previous value of river was. It’s outside of the method rivers so it’s outside its scope. A variable defined in a method lives in that method and can’t leave that method. A variable created outside a method can only be used inside the method if it’s passed in as an argument.

Instance scope allows each instance to have its own version of a variable. It’s easy to pick out in your code since it has an “at” symbol, @, to begin its name. Let’s look at an example:

 class River
   def harder_rapids
     @rapids = “Meat Cleaver”
   end 
 
   def easier_rapids
     @rapids = “Dudley’s Dip”
   end
 end
 
Let’s create two new instances of the class River, we’ll call them:
 
 upper_yough = River.new
 new_river = River.new 

Then we give each of them one of the methods:
 
 upper_yough.harder_rapids
 new_river.easier_rapids

The value of rapids is different for both. upper_yough gets Meat Cleaver and new_river gets Dudley’s Dip. Both are values for @rapids but they’re defined in different methods and so have different scope.

Class scope is a variable shared by all instances of the class. It also easy to identify in your code from the “double at”, @@, symbol that begins its name. It’s the same for all instances of the class but isn’t accessible outside of the class.

Finally, there’s global scope. That’s accessible from anywhere in the program no matter where they’re declared

Hopefully, this has helped to explain these concepts in Ruby. Happy coding!

This blog wouldn’t have been possible without the following resources:
    • Flatiron course material
    • https://www.techotopia.com/index.php/Ruby_Variable_Scope
    • https://www.sitepoint.com/understanding-scope-in-ruby 
    • http://www.railstips.org/blog/archives/2009/05/11/class-and-instance-methods-in-ruby
