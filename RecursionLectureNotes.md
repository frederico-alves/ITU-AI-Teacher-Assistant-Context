# Recursion — Lecture Notes

> **What is recursion?**
> Defining a computation in terms of smaller instances of itself. Each recursive solution must have:
>
> * **Base case(s):** trivial case(s) that stop the recursion.
> * **Recursive case(s):** reduce the problem to strictly smaller subproblems and combine their results.

---

## 1 From Induction to Recursion (the mindset)

* **Mathematical induction** proves a claim for all `n` by showing:

  1. it holds at a base value (e.g., `n=0`), and
  2. if it holds for `n-1`, it holds for `n`.
* **Recursive programming** mirrors that idea:

  * **Base case** ↔ induction base.
  * **Recursive step** assumes the routine works for smaller inputs and builds the larger answer.

---

## 2 A Simple Recipe for Designing Recursive Functions

1. **Identify the base case(s)** (the smallest input where you can answer directly).
2. **Decompose** the problem into smaller instances of the same problem.
3. **Recurse** on the smaller instance(s) and **recombine** the partial results into the final result.

> If each step strictly reduces the input and we eventually hit a base case, the recursion terminates.

---

## 3 Classic Examples

### 3.1 Factorial

**Spec:** `n! = n × (n-1)!`, with `0! = 1`.

```java
static int fac(int n) {
    if (n == 0) return 1;            // base
    return n * fac(n - 1);           // recursive
}
```

* **Termination:** `n` decreases to `0`.
* **Correctness:** follows the factorial definition.

---

### 3.2 Summation

**Spec:** `sum(n) = n + sum(n-1)`, with `sum(0) = 0`.

```java
static int sum(int n) {
    if (n == 0) return 0;            // base
    return n + sum(n - 1);           // recursive
}
```

---

### 3.3 Binary Representation

Return the **string** representing `n` in base 2.

```java
static String bin(int n) {
    if (n < 2) return Integer.toString(n);  // base: 0 or 1
    return bin(n / 2) + (n % 2);            // recurse on floor(n/2), append remainder
}
```

(Alternative that **prints** the bits left-to-right:)

```java
static void binPrint(int n) {
    if (n < 2) {
        System.out.print(n);
    } else {
        binPrint(n / 2);
        System.out.print(n % 2);
    }
}
```

---

### 3.4 Fibonacci Numbers

**Spec (naïve):**
`fib(0) = 0`, `fib(1) = 1`, and `fib(n) = fib(n-1) + fib(n-2)` for `n ≥ 2`.

```java
static int fib(int n) {
    if (n < 2) return n;             // base: 0, 1
    return fib(n - 1) + fib(n - 2);  // exponential time
}
```

> Note: This is clear but **exponential**. Prefer memoization or iteration:

```java
static int fibMemo(int n, int[] memo) {
    if (n < 2) return n;
    if (memo[n] != -1) return memo[n];
    return memo[n] = fibMemo(n - 1, memo) + fibMemo(n - 2, memo);
}

static int fibFast(int n) {
    int[] memo = new int[n + 1];
    java.util.Arrays.fill(memo, -1);
    return fibMemo(n, memo);
}
```

---

### 3.5 Palindromes

A string is a palindrome if its first and last characters match and the **substring** between them is a palindrome; empty and single-character strings are palindromes.

```java
static boolean isPalindrome(String s) {
    if (s.length() < 2) return true;                       // base
    if (s.charAt(0) != s.charAt(s.length() - 1)) return false;
    return isPalindrome(s.substring(1, s.length() - 1));   // shrink ends
}
```

> For sentences, you’d first **normalize** (lowercase, remove non-letters) and then call the same routine.

---

### 3.6 Towers of Hanoi

**Rules:** Move a stack of `n` disks from `source` to `target` using `temp`, moving one disk at a time and never placing a larger disk on a smaller one.
**Key idea:** To move `n` disks:

1. move `n-1` from `source` to `temp`,
2. move the largest disk to `target`,
3. move `n-1` from `temp` to `target`.

```java
static void move(int n, String source, String target, String temp) {
    if (n > 0) {
        move(n - 1, source, temp, target);
        System.out.println("Move disk " + n + " from " + source + " to " + target);
        move(n - 1, temp, target, source);
    }
}

static void demo(int n) {
    move(n, "source", "target", "[temp]");
}
```

* **Moves needed:** `2^n - 1`.
* **Growth:** exponential; even moderate `n` explodes in steps.

---

## 4 Recursion vs. Iteration

* **Iteration** tends to be **faster** and uses **constant stack** space.
* **Recursion** often gives a **clearer** and more direct mapping from the problem’s definition (e.g., Hanoi, tree traversals, expression evaluation).
* Always ensure:

  * iterative loops **will terminate**, or
  * recursive calls **reach a base case**.

**Example (factorial, iterative alternative):**

```java
static int facIter(int n) {
    int res = 1;
    for (int i = n; i > 0; i--) res *= i;
    return res;
}
```

---

## 5 Recursive Data Structures

### 5.1 Expression Trees

Define a tiny expression language and evaluate/print it recursively.

```java
abstract class Exp {
    public abstract void print();
    public abstract int eval();
}

class NumExp extends Exp {
    private final int number;
    public NumExp(int number) { this.number = number; }
    public void print() { System.out.print(number); }
    public int eval() { return number; }
}

class AddExp extends Exp {
    private final Exp left, right;
    public AddExp(Exp left, Exp right) { this.left = left; this.right = right; }
    public void print() { System.out.print("("); left.print(); System.out.print(" + "); right.print(); System.out.print(")"); }
    public int eval() { return left.eval() + right.eval(); }
}

// More operators (exercise): SubExp, MulExp, DivExp
class SubExp extends Exp {
    private final Exp left, right;
    public SubExp(Exp left, Exp right) { this.left = left; this.right = right; }
    public void print() { System.out.print("("); left.print(); System.out.print(" - "); right.print(); System.out.print(")"); }
    public int eval() { return left.eval() - right.eval(); }
}

class MulExp extends Exp {
    private final Exp left, right;
    public MulExp(Exp left, Exp right) { this.left = left; this.right = right; }
    public void print() { System.out.print("("); left.print(); System.out.print(" * "); right.print(); System.out.print(")"); }
    public int eval() { return left.eval() * right.eval(); }
}
```

**Usage:**

```java
static void demoExp() {
    Exp e = new SubExp(
                new MulExp(new NumExp(4), new NumExp(3)),
                new AddExp(new NumExp(2), new NumExp(1))); // (4*3)-(2+1)
    e.print();
    System.out.println(" = " + e.eval());                  // prints: ((4 * 3) - (2 + 1)) = 9
}
```

> **Why recursion fits:** the tree structure is recursive, so evaluation/printing naturally recurse down the left/right subtrees.

---

### 5.2 A Minimal Linked List (structural recursion)

```java
class LinkedList {
    int head;
    LinkedList tail;  // null marks the end

    LinkedList(int head, LinkedList tail) { this.head = head; this.tail = tail; }

    int getHead() { return head; }
    LinkedList getTail() { return tail; }
}

class RecFind {
    static void print(LinkedList list) {
        if (list == null) return;             // base
        System.out.println(list.head);
        print(list.tail);                     // recursive
    }

    static boolean find(LinkedList list, int target) {
        if (list == null) return false;       // base
        if (list.head == target) return true;
        return find(list.tail, target);       // recursive: shrink the list
    }
}
```

---

## 6 Bonus: Recursive Graphics (Fractals)

### 6.1 Koch Curve (conceptual)

```java
// Pseudo-API: turnTo(dir), forward(len)
void koch(int n, int dir, int length) {
    if (n == 0) {
        turnTo(dir);
        forward(length);
    } else {
        koch(n - 1, dir,     length / 3);
        koch(n - 1, dir + 60,length / 3);
        koch(n - 1, dir - 60,length / 3);
        koch(n - 1, dir,     length / 3);
    }
}
```

### 6.2 Sierpinski Triangle (conceptual)

```java
// Pseudo-API: line(Point a, Point b); Point.mid(Point other)
void sierpinski(int n, Point a, Point b, Point c) {
    if (n > 0) {
        line(a, b); line(b, c); line(c, a);
        Point p = a.mid(b), r = b.mid(c), q = c.mid(a);
        sierpinski(n - 1, a, p, q);
        sierpinski(n - 1, b, p, r);
        sierpinski(n - 1, c, q, r);
    }
}
```

> Each call draws three smaller triangles—self-similarity via recursion.

---

## 7 Common Pitfalls & Tips

* **Missing base case** → stack overflow.
* **Non-shrinking recursion** → infinite recursion.
* **Repeated work** (e.g., naïve Fibonacci) → consider memoization or iterative DP.
* **Stack depth limits:** deep recursion can overflow; prefer iteration or explicit stacks for very deep inputs.
* **Purity helps:** Make recursive methods free of side effects unless you’re *intentionally* doing I/O (like printing in Hanoi).

---

## 8 Exercises (quick prompts)

1. Implement `sum(n)` recursively and iteratively; prove equivalence by induction.
2. Extend the expression language with division and proper error handling (e.g., divide-by-zero).
3. Write an iterative version of Hanoi that prints the same moves for small `n`.
4. Normalize strings (lowercase, strip non-letters) and check palindromes.
5. Compare runtimes of `fib`, `fibFast`, and an iterative DP solution for increasing `n`.

---

*Based primarily on the course slides “Undervisningsgang 20: Rekursion” and expanded with additional explanations and Java examples.* 
