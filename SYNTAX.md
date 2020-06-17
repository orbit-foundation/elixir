# Project Calculus - Syntax
_Note: Project Calculus is a codename. The language is called SumScript._

### Pots
All of SumScript is based around pots. A pot is a collection of expressions revolving around variables. You can declare a pot like so:
```
pot <potname> {
  <expressions>
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

You can then solve the value using **solve(pot.<potname>.<variable>)**. For that, we need an undefined value. Let's make a value called `undefined` and set it to the sum of `variable1` and `variable2`. Here's the updated code plus the `solve` command:
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

#### More information soon!
