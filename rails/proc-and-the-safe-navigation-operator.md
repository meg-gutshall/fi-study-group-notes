# Proc and The Safe Navigation Operator

> `&object` is evaluated in the following way:
>
> If object is a block, it converts into a simple proc.  
> If object is a `Proc`, it converts the object into a block while preserving the `lamba?` status of the object.  
> If object is not a `Proc`, it first calls `#to_proc` on the object, then converts it into a block.

That is taken from a pretty comprehensive yet friendly-written blog post:

{% embed url="https://ablogaboutcode.com/2012/01/04/the-ampersand-operator-in-ruby" %}

So the issue here is that perhaps one or more of `Proc`, `lambda`, `#to_proc` and full understanding of block in this context might trip us up and make it still tricky to understand.

Let’s start with probably the most ‘obvious’ one: `#to_proc` is a method that converts something into a `Proc`. What a `Proc` is might still be a mystery at this point but we now know that we have a method that can turn something into one!

The next nugget we want to take in is that a `lambda` is a type of `Proc` \(but not the other way around\).

So we still are not sure what a `Proc` is but we know a `lambda` is a type of one \(it has some adjusted features but it is a type of `Proc`\).

So the million dollar question: What the hell is a `Proc`?

A `Proc` object is a block of code that has been bound to a set of local variables.

Once a `Proc` object has been bound it can be called in different contexts and still be able to access those variables.

Here is the Ruby Docs for `Proc`: [https://ruby-doc.org/core-2.2.0/Proc.html](https://ruby-doc.org/core-2.2.0/Proc.html)

\(If you have come across closures in JavaScript you may be starting to see some correlating concepts here but don’t worry if you’ve not heard of closures before!\)

We can get pretty deep into `Proc` and things but let’s look at some real examples.

One important feature of a standard `Proc` is that it will not error out if it receives the wrong set of arguments. It will just return `nil` with no additional fuss. With that in mind, we can be thinking about the use of this `&xxxx` syntax being referred to as the safe navigation operator in Ruby.

{% embed url="http://mitrev.net/ruby/2015/11/13/the-operator-in-ruby/" %}

So let’s say we have a collection of `Users` signing up for our app. They have the option of providing us a phone number and we want to display their phone number. One way we might think to do it in pseudo code might be:

```ruby
@user = User.first
if @user.phone_number
  puts @user.phone_number
else
  puts nil
end
```

Kinda lengthy. We could get it down to a one-liner perhaps using ternary conditional syntax but it’s still a fair amount of code.

So what if I told you we could replace that with:

```ruby
puts @user&.phone_number
```

That’d be kinda nice, no?

If you’ve got some time and like space, puppies, and learning more about this stuff, check this out:

{% embed url="https://medium.com/series/c1605e2cfe28" %}

