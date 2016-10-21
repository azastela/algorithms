## The Questions

### General
  * describe your experience in ruby
  * describe REST

### Ruby
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
* describe assets pipeline. Cleaning, minifying JS CSS, can compile coffescript scss, hashes compiled version.
* describe N+1 problem, how to avoid associations or queries that return list of objects that are iterated User -> has 10 Books user.books.each {|b| puts b } will execute 10 queries for books and 1 for user. Use User.includes(:books).each will execute 2 queries
* what is difference between has_and_belongs_to_many and has_many through? Both contains joint table, but in has many througn role of joint table plays real entity table
* refactor this method in model

```ruby
def result_message
  m = ResultCodes[result_code]
  if m != nil then
    return m
  else
    return "Unknown"
  end
end
```

### CSS and HTML
* experience with bootstrap. Bootstrap grid. Why should we use it
* how to align span in dev vertically center

```css
<style>
  div {
    height: 50px;
    //line-height: 50px;
  }
</style>
<div>
  <span>Текст</span>
</div>
```

* we have 3 divs. content, sidebar and footer. all float: left. content - height: 100px, sidebar and footer - height: 50px; footer will be right under sidebar to the right and content will be to the left. How can we make footer be under content and sidebar.

### JavaScript
* what frameworks did you work with
* what is clojure. what the purpose of using it. Context refference to outside function inside of another
* what is hoisting. what will be the output of the following example:

```javascript
var n = 1;
function printSomething() {
     console.log(n);
     var n = 2;
     console.log(n);
}  
printSomething();
```

* why wrapping file context into self invoking function function (function() {  })(). To avoid variable names conflicts among different files
* what is the difference between jQuery click() and on('click'). Click is attaching event to existing element live to not existing, live is listening body.
* what is difference between stopPropagation, preventDefault, return false when we use it in event handler
