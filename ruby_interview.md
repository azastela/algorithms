## The Questions

### General
  * Why did you switch from another language(php) to ruby. What advantages of ruby language comparing with your old language.
  * Describe your experience in ruby

### Ruby
* module vs class. differences.
* 3 types of access modifiers what the difference.
* does multiple inheritance exists in ruby. how to simulate multiple inheritance
* what the difference between map and each
* how can you have abstract class in Ruby. method that definitely needs to be defined in child class.
* class B inherits from class A and inludes module C, class A and module C have method f. what method will be called

```ruby
class A
  def f
    p 'in A'
  end
end
module C
  def f
    p 'in C'
  end
end
class B < A
  include C
end
p B.new.f
```
* implement custom inject method. [0, 1, 2, 3, 3, 4].my_inject(0) { |acc, el| acc += el }

```ruby
module MyInject
  def my_inject(acc = nil)
    each do |element|
      acc = yield(acc, element)
    end
    acc
  end
end
Enumerable.send(:include, MyInject)
[0, 1, 2, 3, 3, 4].my_inject(0) { |acc, el| acc += el }
```
* (optional) make this line work: [1, 2, 3, 4].map(&'to_s')
```ruby
class String
  def to_proc
    Proc.new { |el| el.send(self.to_sym) }
  end
end
```

### Ruby on Rails
* describe HTTP request phase Rails parts/libraries calling. Rails process -> Rack -> ActionDispatch -> Controller
* what is rack and when it is applicable? Filtering request, security, authorization
* describe N+1 problem, how to avoid associations or queries that return list of objects that are iterated User -> has 10 Books user.books.each {|b| puts b } will execute 10 queries for books and 1 for user. Use User.includes(:books).each will execute 2 queries
* what is difference between has_and_belongs_to_many and has_many through? Both contains joint table, but in has many througn role of joint table plays real entity table
* polymorphic association. could you describe what is it. and when to use.
* refactor this examples
<br>
https://github.com/ar-shestopal/tets_assignment/blob/master/app/models/user.rb
<br>
http://dmcca.be/2014/02/02/the-value-of-rails-worst-practices.html
<br>
https://bitbucket.org/spicyoranges/instaprinter
