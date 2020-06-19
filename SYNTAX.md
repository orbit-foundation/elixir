# Elixir Math - Syntax

### Pots
All of SumScript is based around pots. A pot is a collection of expressions revolving around variables. You can declare a pot like so:
```
pot [potname] {
  [expressions]
}
```

Let's create a draft pot called `pot1`. Here it is in the first line:
```
pot pot1 {
```

Now we need to add some expressions to `pot1`. We're going to make two variables called `variable1` and `variable2`. Let's add some random values. Here's the code so far:
```
pot pot1 {
var variable1 = 10;
var variable2 = 4;
}
```

You can then solve the value using solve(pot.[potname].[variable]). For that, we need an undefined value. Let's make a value called `undefined` and set it to the sum of `variable1` and `variable2`. Here's the updated code plus the `solve` command:
```
pot pot1 {
var variable1 = 10;
var variable2 = 4;
var variable3 = variable1 + variable2;
}

solve(pot.pot1.variable3)
```

The output of this will, of course, be 14.

---

### The `root` element
You can define as many pots as you want, but to mingle variables between pots, you need to set them as root variables. A `root` element looks a little like this, and must always be at the start of your SumScript program.:
```
root {
var variablename = value;
}
```

Let's add our code to the example from [Pots](#Pots):
```
root {
var toBeAppendedTo = undefined;
}

pot pot1 {
var variable1 = 10;
var variable2 = 4;
var variable3 = variable1 + variable2;
}

solve(pot.pot1.variable3, toBeAppendedTo)

print(toBeAppendedTo)
```

You will have noticed the extra code, here's a rundown of what it means:
* The "undefined" value of the variable "toBeAppendedTo" in the root area means that there isn't a defined value or data type for that value.
* We've added an extra bit after "pot.pot1.variable3", which is a comma followed by the variable we created in the root area. Because it's undefined, we can add the value of variable3 to it so it can be printed.
* The print element is fairly self-explanatory, continuing from above.

---

### Pot content
Pots can contain three types of data:
* **Expressions** are formed of integers or variables and are comprised of operators, equal keys and variable or constant keywords.
* **Sequences** are formed of integers in a linear or quadratic sequence. You can solve the sequence using the `find` keyword.
* *Variable alterations* are identifiers that modify, within that pot only, a `root` variable.

Here's an example of some expression content in a pot, as you've seen above:
```
pot pot1 {
var a = 12
var b = 45 + 76
var c = a + b
}

solve(pot.pot1.c, final)
print(final)
```
And here's some sequence content:
```
pot pot2 {

  define sequence seq1 {1, 3, 7, 13, 21}
  
}

find(pot.pot2.seq1, n)
```
_The n at the end of the `find` keyword denotes that the program should find the nth term._
<br>
And here is some variable alteration content, with a `root` area for functionality:
```
root {
var a = 2
var b = 4
var c = 10
}

pot pot3 {
  a += 3
  b = a+c
}

solve(pot.pot3.b, final)
print(final)
```
_This will print 15._

---

#### More soon!
