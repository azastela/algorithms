1 Common Knoledge
  * describe your experience in ruby
  * describe REST

2 Ruby
  * is Ruby single inheritance or multi. how to simulate multiple inheritance
  * what the difference between map and each
  * how can you have abstract class in Ruby
    by throwing exception inside of method notation
  * class B inherits from class A and inludes module C, class A and module C have method f. what method will be called
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
  * what are singleton methods, how they are used
    methods that belong to one object a = A.new; def a.hello; puts 'hello'; end
  * implement custom inject method. [0, 1, 2, 3, 3, 4].my_inject(0) { |acc, el| acc += el }
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
  * (optional) make this line work: [1, 2, 3, 4].map(&'to_s')
    class String
      def to_proc
        Proc.new { |el| el.send(self.to_sym) }
      end
    end

3 Ruby on Rails
  * describe HTTP request phase Rails parts/libraries calling
    Rails process -> Rack -> ActionDispatch -> Controller
  * what is rack and when it is applicable?
    filtering request, security, authorization
  * describe assets pipeline
    cleaning, minifying JS CSS, can compile coffescript scss, hashes compiled version
  * describe N+1 problem, how to avoid
    associations or queries that return list of objects that are iterated
    User -> has 10 Books user.books.each {|b| puts b } will execute 10 queries for books and 1 for user
    use User.includes(:books).each will execute 2 queries
  * what is difference between many to many and has many through?
    both contains joint table, but in has many througn role of joint table plays real entity table
  * refactor this method in model
    def result_message
      m = ResultCodes[result_code]
      if m != nil then
        return m
      else
        return "Unknown"
      end
    end

4 CSS and HTML
  * experience with bootstrap. Bootstrap grid. Why should we use it
  * how to align span in dev vertically center
    <style>
      div {
        height: 50px;
        //line-height: 50px;
      }
    </style>
    <div>
      <span>Текст</span>
    </div>
  * we have 3 divs. content, sidebar and footer. all float: left. content - height: 100px, sidebar and footer - height: 50px; footer will be right under sidebar to the right and content will be to the left. How can we make footer be under content and sidebar.

5 JavaScript
  * what frameworks did you work with
  * what is clojure. what the purpose of using it.
    context refference to outside function inside of another
  * what is hoisting. what will be the output of the following example:
    var n = 1;
    function printSomething() {
         console.log(n);
         var n = 2;
         console.log(n);
    }  
    printSomething();
  * why wrapping file context into self invoking function function (function() {  })()
    to avoid variable names conflicts among different files
  * what is the difference between jQuery bind() and on()
    bind is attaching event to existing element live to not existing, live is listening body
  * what is difference between stopPropagation, preventDefault, return false when we use it in event handler
