##Iteration: Each Vs. Collect


###Objectives
1. Identify the return values of the `each` and `collect` methods.
2. Implement the `each` and `collect` methods.

###Overview
This lesson will give a deeper dive on how to use the `each` and `collect` methods.


For our examples we will be building a `hamburger` method that takes an array of `toppings` as an argument.

####What we want our methods to do
- Take in an array of hamburger toppings.
- Iterate through each topping, one at a time.
- Manipulate that data (do something to it).
- Return the manipulated data.

##Each
The most important thing to remember about `each` is that it does not change the return value. It implicitly returns the original array.

```ruby
toppings = ["pickles", "mushrooms", "bacon"]

def hamburger(toppings)
  toppings.each do |topping|
    puts "I love #{topping} on my burgers!"
  end
end
```
####This method will print:

```ruby
I love pickles on my burgers!
I love mushrooms on my burgers!
I love bacon on my burgers!
```

####But the return value is still:

`["pickles", "mushrooms", "bacon"]`

####If we want a different return value, we have to explicitly tell it to do so.

In this version of our burger method we set an empty array called `my_statements`, which we will then explicitly return after we finish our loop.
Inside our `each` statement loop, we manipulate each topping by interpolating it inside a string. We then push that string into our `my_statements` array.
After we iterate over each topping in our array, we return the new `my_statements` array.

You'll notice that since the `each` doesn't return the thing we want, we have to add an extra line at the end that returns the `my_statements` array.

```
def hamburger(toppings)
  my_statements = []
  toppings.each do |topping|
    my_statements << "I love #{topping} on my burgers!"
  end
  my_statements
end
```
###Our new return value:
```
[
  "I love pickles on my burgers!"
  "I love mushrooms on my burgers!"  
  "I love bacon on my burgers!"
]
```
However, if we do want a different return value, there is a handy method called `map`, also known as `collect`. These methods are abstractions of our `each` method. An abstraction is the process of taking away or removing characteristics from something in order to reduce it to a set of essential characteristics. Let's take a look at a few examples.


##Map & Collect

```ruby
toppings = ["pickles", "mushrooms", "bacon"]

def hamburger(toppings)
  toppings.map do |topping|
    puts "I love #{topping} on my burgers!"
  end
end
```
Since `map` and `collect` are the same thing, this can be expressed exactly the same way with `collect`, like the following.

```ruby
def hamburger(toppings)
  toppings.collect do |topping|
    puts "I love #{topping} on my burgers!"
  end
end
```

####This method will print:
```ruby
I love pickles on my burgers!
I love mushrooms on my burgers!
I love bacon on my burgers!
```
####This method will return:

`[nil, nil, nil, nil]`

####Why does it return nil?
If you look inside our `map` loop, you will see that we are using `puts`, which always has a `nil` return value. What this is telling us is that our return value is indeed being changed by `map`. Let's look at another example.

Here we are no longer using `puts`, but instead implicitly returning what is inside our block. Again showing that `map` will give us a new return value based on the logic inside our block.

```
def burger(toppings)
  toppings.collect do |topping|
    "I love #{topping} on my burgers"
  end
end
```
####Our new return value:

```
[
  "I love pickles on my burgers!"
  "I love mushrooms on my burgers!"  
  "I love bacon on my burgers!"
]
```
###Takeaway:
- If you want want the transformations to be reflected in the return value use `map` or `collect`.
- If you want to return the original return value use `each`.

<a href='https://learn.co/lessons/each-vs-collect-readme' data-visibility='hidden'>View this lesson on Learn.co</a>
