# Random Module

### When to use it?
* We want the computer to pick a random number in a given range or pick a random element from a list.

## Random functions
* Random module contains some very useful functions
1. Randint
>  To generate random integer  between tow integer numbers (a lowest and a highest number).
2. Random
> random float from 0 to 1
3. Choice
> Generate a random value from the sequence sequence.
4. Shuffle
> To shuffle the elements in list in place to get them in random order
5. Randrange
> Generate a randomly selected element from range

# Risk Analysis in Software

* Risk is The probability of any unwanted incident

## Risk analysis:
 1. The process of identifying the risks in applications or software. 
 2. assigning the level of risk is done. 
 3. The categorization of the risks takes place.
 4. calculate the impact of the risk.


 ### Why use Risk Analysis
 > It helps the developers and managers to mitigate the risks. When a test plan has been created, risks involved in testing the product are to be taken into consideration along with the possibility of the damage they may cause to your software along with solutions.

 ### The possible risks that could be encounter
  1. Use of new hardware
  2. Use of new technology
  3. Use of new automation tool
  4. The sequence of code
  5. Availability of test resources for the application

 ### risks that are unavoidable
 1. The time of testing
 2. A defect leakage due to the complexity or size of the application
 3. Urgency from the clients to deliver the project
 4. Incomplete requirements

## Risk Identification


 * Business Risks: This risk is the most common risk associated with our topic. It is the risk that may come from your company or your customer, not from your project.

 * Testing Risks: You should be well acquainted with the platform you are working on, along with the software testing tools being used.

 * Premature Release Risk: a fair amount of knowledge to analyze the risk associated with releasing unsatisfactory or untested software is required

 * Software Risks: You should be well versed with the risks associated with the software development process.

## The perspective of Risk Assessment

 1. Effect – To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.

 2. Cause – To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.

 3. Likelihood – To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.

## Steps to perform Risk Analysis?

 1. Searching the risk
 2. Analyzing the impact of each individual risk
 3. Measures for the risk identified
 
# TestCoverage

 > Test coverage is a useful tool for finding untested parts of a codebase. Test coverage is of little use as a numeric statement of how good your tests are.

 * TDD is a very useful, but certainly not sufficient, tool to help you get good tests.

 > Sufficiency of testing is much more complicated attribute than coverage can answer
 * The reason of why people focus on coverage numbers is because they want to know if they are testing enough 
 * low coverage numbers are a sign of trouble.
 * high numbers don't necessarily mean much,

I would say you are doing enough testing if the following is true:

1. rarely get bugs that escape into production and rarely hesitant to change some code for fear it will cause production bugs.
2. You are testing too much if you can remove tests while still having enough. But this is a difficult thing to sense. 
3. One sign you are testing too much is if your tests are slowing you down. If it seems like a simple change to code causes excessively long changes to tests, that's a sign that there's a problem with the tests. 

## Summary
 helps you find which bits of your code aren't being tested.
 It's worth running coverage tools every so often and looking at these bits of untested code. 