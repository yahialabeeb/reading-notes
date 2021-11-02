# Functions
As duckett said 
> Functions let you group a series of statements together to perform a 
specific task. If different parts of a script repeat the same task, you can 
reuse the function (rather than repeating the same set of statements).

## Important phrases 
### caling 
when you ask function to do its task
### parameters 
the information needed to achieve functions task.
(not all function) the response of function the you look for

## Create Function

### Declaring a function 
A function declaration creates a function that you 
can call later in your code and can be called before it has even been 
declared.
#### sentax 
function sayhello() {
    code stat.
} 
#### calling a function 
you can calling function by write his name with () , if the function need information we have to put it inside ()
##### example 
1. sayHello();
1. getArea(3, 4)

## Get information from function 
* for one value 
let anyvarriable = functionname(p1, p2)
* for multiple values 
let anyvarriable1 = functionname(p1, p2)[0]
let anyvarriable2 = functionname(p1, p2)[1]

## Function expression 
a function expression is a function that treated as an 
expression, and it will not processed d until the interpreter gets to that 
statement. 
#### sentax 
var area = function sayhello(p1,p2) {
    code stat.
}
## named and anonymous function
named functions is the funcyion that you 
must give it a name In order to call the function later in your code.  
* anonymous is A function with no name. 

## IMMEDIATELY INVOKED FUNCTION EXPRESSIONS (IIFES)
hollding the value returned from the function in a variable without named the function is commonly use
### exapmles of IIFES
* As an argument when a function is called 
(to calculate a value for that function). 
* To assign the value of a property to an object. 
* In event handlers and listeners to perform a task when an event occurs. 
* To prevent conflicts between two scripts that might use the same variable names

## variable scope 
#### Local 
* The variable have value inside the function and cannot asccessed outside of the function 
* The variable can have different values for differint function         
#### Globle 
* Global variables are stored in memory for as long 
as the web page is loaded into the web browser.

## Pair Programming
pair programming commonly involves two roles: the Driver and the Navigator. The Driver is the programmer who is typing and the only one whose hands are on the keyboard. Handling the “mechanics” of coding, the Driver manages the text editor, switching files, version control, and—of course writing—code. The Navigator uses their words to guide the Driver but does not provide any direct input to the computer. The Navigator thinks about the big picture, what comes next, how an algorithm might be converted in to code, while scanning for typos or bugs.
### Why pair program
pair program helps devlopers study several programming languages. 
#### Greater efficiency
* Research indicates that pair programing takes slightly longer, but produces higher-quality code.
#### Engaged collaboration
 * programmers are more focused than if they were working alone
 * students rely more on each other and can often find a solution together without needing to ask for additional help. Ultimately, this boosts overall confidence.

#### Learning from fellow students

* The less experienced developer benefits from the experienced developer’s knowledge and guidance, and the latter benefits from explaining the topic in their own words, further solidifying their own understanding.
#### Social skills
* Pair programming not only improves programming skills, but can also help programmers develop their interpersonal skills.
#### Job interview readiness 
* Pair programming strengthens skills like the ability to work with and learn from others and stellar communication skills are more important to a company than specific technical skills. 
#### Work environment readiness
* Many companies that utilize pair programing expect to train fresh hires
