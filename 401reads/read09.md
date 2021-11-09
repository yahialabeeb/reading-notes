# Dunder Methods & Probability

## Dunder method
### What Are Dunder Methods?
* special methods are a set of predefined methods start and end with double underscores, for example \__init__ or \__str__.

* “dunder methods”, a short form of “double under.”

* Dunder methods let you emulate the behavior of built-in types. for example "len" by using \__len__


### 1. Object Initialization: \__init__

* To construct account objects from the Account class I need a constructor which in Python is the __init__ dunder.
* It receives the owner name, an optional start amount and defines an internal transactions list to keep track of deposits and withdrawals.

### 2. Object Representation: \__str__, \__repr__
#### To provide a string representation of your object for the consumer of your class there are two methods 
1. \__repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of \__repr__ is to be unambiguous.

2. \__str__: The “informal” or nicely printable string representation of an object. This is for the enduser.

```python
class Account:
    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
```
### 3. Iteration: \__len__, \__getitem__, \__reversed__
* In order to iterate over our account object I need to add some transactions.

* These Method are used to know:

1. How many transactions were there?

2. Index the account object to get transaction number …

3. Loop over the transactions

how to define them 
```python 
class Account:
    def add_transaction(self, amount):
    if not isinstance(amount, int):
        raise ValueError('please use int for amount')
    self._transactions.append(amount)

    def __len__(self):
        return len(self._transactions)

    def __getitem__(self, position):
        return self._transactions[position]
    
    def __reversed__(self):
    return self[::-1]
```

### 4. Operator Overloading for Comparing Accounts: \__eq__, \__lt__
* Why does (>) work equally well on integers, strings and other objects (as long as they are the same type)?
* because these objects implement one or more comparison dunder methods.An easy way to verify this is to use the dir() builtin

* now compare classes by adding these methods 
```python 
class Account:
    # ... (see above)

    def __eq__(self, other):
        return self.balance == other.balance

    def __lt__(self, other):
        return self.balance < other.balance
```
### 5. Operator Overloading for Merging Accounts: \__add__
* When you try to add two instances of any class there’s a TypeError you need to implement __add__ to be able to use +
* Example 
```python 
def __add__(self, other):
    owner = self.owner + other.owner
    start_amount = self.balance + other.balance
    return Account(owner, start_amount)
```

### 6. Callable Python Objects: \__call__
* You can make an object callable like a regular function (call the object with the double-parentheses) by adding the __call__ dunder method.
```python 
def __call__(self):
        print('Start amount: {}'.format(self.amount))
        print('Transactions: ')
        for transaction in self:
            print(transaction)
        print('\nBalance: {}'.format(self.balance))
```

### 7. Context Manager Support and the With Statement: \__enter__, \__exit__

> A context manager is a simple “protocol” (or interface) that your object needs to follow so it can be used with the with statement. Basically all you need to do is add __enter__ and __exit__ methods to an object if you want it to function as a context manager.

* We can leverage the Pythonic with statement by adding two dunder methods (\__enter__, \__exit__)
```python 

class Account:
    # ... (see above)

    def __enter__(self):
        print('ENTER WITH: Making backup of transactions for rollback')
        self._copy_transactions = list(self._transactions)
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('EXIT WITH:', end=' ')
        if exc_type:
            self._transactions = self._copy_transactions
            print('Rolling back to previous transactions')
            print('Transaction resulted in {} ({})'.format(
                exc_type.__name__, exc_val))
        else:
            print('Transaction OK')
```
### Some Recommended Linkes 

1. [Python reference documentation.](https://docs.python.org/3/reference/datamodel.html)
2. [dunder method coding challenge](https://pybit.es/codechallenge24.html)


## Basic statistics in python probability

### What is probability?
* Probability seeks to answer the question, “What is the chance of an event happening?” An event is some outcome of interest.

### From statistics to probability
* There are no easy ways to calculate probabilities in many case, so we must fall back on using data and statistics to calculate them. Given more and more data, we can become more confident that what we calculate represents the true probability of these important events happening. 

### The data and the distribution
* The normal distribution refers to a particularly important phenomenon in the realm of probability and statistics.The most important qualities its symmetry and the shape of normal distribution looks like this 

![image](https://i.imgur.com/3vDS2Au.png)

* When the two score distributions overlap too much, it’s probably better to assume thy actually come from the same distribution and aren’t different. On the other extreme with no overlap, it’s safe to assume that the distributions aren’t the same. Our trouble lay in the case of some overlap. Given that the extreme highs of one distribution may intersect with the extreme lows of another.

![mm](https://i.imgur.com/h4FR5XL.jpg)

### Revisiting the normal
1. Central Limit Theorem
* If we make many estimates, the Central Limit Theorem dictates that the distribution of these estimates will look like a normal distribution. The zenith of this distribution will line up with the true value that the estimates should take on. In statistics, the peak of the normal distribution lines up with the mean, and that’s exactly what we observed.
* Thus, given multiple “trials” as our data, the Central Limit Theorem suggests that we can hone in on the theoretical ideal given by probability, even when we don’t know the true probability. 
* Central Limit Theorem lets us know that the average of many trials means will approach the true mean
2. Three Sigma Rule
* The Three Sigma Rule tell us how much the data will be spread out around this mean.
* The Three Sigma rule dictates that given a normal distribution, 68% of your observations will fall between one standard deviation of the mean. 95% will fall within two, and 99.7% will fall within three.
![rules](https://i.imgur.com/Mt3RyE0.png)
3. Z-score
* The Z-score is a simple calculation that answers the question, “Given a data point, how many standard deviations is it away from the mean?” The equation below is the Z-score equation.

![](https://i.imgur.com/3TuDF4G.jpg)