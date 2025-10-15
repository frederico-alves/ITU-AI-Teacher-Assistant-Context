# Recursion Assessment

## About This Assessment

This quiz is about **Recursion** — a method of solving computational problems where the solution depends on smaller instances of the same problem.

Please note:

- It’s completely fine if you haven’t practiced recursion before.
- We are **not interested in individual results**, only the aggregated outcomes.
- Professors and TAs **cannot see your individual responses**.
- All data is **anonymous**.
- The quiz consists of **8 questions**.
- Each question includes an _“I don’t know”_ option.
- You have **1 hour** to complete the test.
- Use **only your assigned resources**:

  - **Group A** — Teaching Assistants (TAs) only
  - **Group B** — CustomGPT AI only
  - **Group C** — Both TAs and CustomGPT AI

> ❌ Do **not** use any other sources (books, blogs, videos, slides).
> 🧩 Focus on reasoning, not syntax correctness.

---

## Group Assignment

**Please indicate which experimental group you have been assigned to:**

- [ ] Group A — using Teaching Assistants (TAs) only
- [ ] Group B — using AI (our CustomGPT) only
- [ ] Group C — using both TAs and AI (our CustomGPT)

---

## 🧠 Consent to Participate in Research

We are master's students from **IT University of Copenhagen** conducting research for our thesis.

By participating, you confirm:

- Participation is **anonymous**.
- Only **group patterns** are analyzed.
- Data is **confidential**.
- Only Groups **B** and **C** may use CustomGPT.
- Proceed through the quiz **in order** — do not go back.

**I hereby consent to my data being collected and used for research:**

- [ ] Yes
- [ ] No

---

## ⚧ Gender

**What is your gender?**

- [ ] Man
- [ ] Woman
- [ ] Non-binary
- [ ] Prefer not to say

---

# 🧩 Problem 1

---

## Question 1.1

The following code implements a **recursive function** that calculates powers of two for a number `n` (i.e. 2ⁿ).

What is the sequence of function calls (including the value of the argument) if we call:
`twoPow(3)`?

### Code

```c
int twoPow(int n) {
    if (n == 0) return 1;
    return 2 * twoPow(n - 1);
}
```

### Possible Answers

- [ ] twoPow(3), twoPow(0)
- [ ] I don’t know
- [ ] twoPow(3), twoPow(2), twoPow(1), twoPow(0)
- [ ] twoPow(0), twoPow(1), twoPow(2), twoPow(3)
- [ ] twoPow(1), twoPow(2), twoPow(3)
- [ ] twoPow(0), twoPow(3)
- [ ] twoPow(3), twoPow(2), twoPow(1)

---

## Question 1.2

The following code implements a **recursive function** that calculates powers of two of a number `n` (i.e. 2ⁿ).

What is the sequence of **return values** from all function calls, if we call `twoPow(3)`?

### Code

```c
int twoPow(int n) {
    if (n == 0) return 1;
    return 2 * twoPow(n - 1);
}
```

### Possible Answers

- [ ] 8, 4, 2
- [ ] I don’t know
- [ ] 8, 4, 2, 1
- [ ] 1, 2, 4, 8
- [ ] 8, 1
- [ ] 2, 4, 8
- [ ] 1, 8

---

## Question 2

The following code implements a recursive function that calculates powers of two of a number `n` (i.e. 2ⁿ).

Modify this code so that it **recursively calculates sums of two** by adding 2 together `n` times.
You must use recursion.

> Example table of expected results:

| n   | Expression | Result |
| --- | ---------- | ------ |
| 0   | 0          | = 0    |
| 1   | 2          | = 2    |
| 2   | 2 + 2      | = 4    |
| 3   | 2 + 2 + 2  | = 6    |

### Template

```c
int twoSum(int n) {
    if (n == ...) return ...;
    return ... (n - 1);
}
```

---

## Question 3

You need to implement a **recursive function** that calculates powers of two of a number `n` (i.e. 2ⁿ).
You need to use recursion.

### Template

```c
int twoPow(int n) {
    ...
}
```

| n   | Expression | Result |
| --- | ---------- | ------ |
| 0   | 2⁰         | = 1    |
| 1   | 2¹         | = 2    |
| 2   | 2²         | = 4    |
| 3   | 2³         | = 8    |

---

# 🧩 Problem 2

---

## Question 2.1

The following code implements a **recursive function** that counts the number of `'a'` characters in a word.
Example: `countA("ada") = 2`

What is the sequence of function calls (including the value of the argument) if we call:
`countA("ada")`?

### Code

```java
int countA(String word) {
    if (word.length() == 0) return 0;
    if (word.charAt(0) == 'a') {
        return 1 + countA(word.substring(1));
    } else {
        return countA(word.substring(1));
    }
}
```

### Possible Answers

- [ ] countA(""), countA("ada")
- [ ] I don’t know
- [ ] countA("ada"), countA("da"), countA("a")
- [ ] countA("a"), countA("ad"), countA("ada")
- [ ] countA(""), countA("a"), countA("ad"), countA("ada")
- [ ] countA("ada"), countA("")
- [ ] countA("ada"), countA("da"), countA("a"), countA("")

---

## Question 2.2

The following code implements a **recursive function** that counts the number of `'a'` characters in a word.
Example: `countA("ada") = 2`

What is the sequence of **return values** from all function calls if we call:
`countA("ada")`?

### Code

```java
int countA(String word) {
    if (word.length() == 0) return 0;
    if (word.charAt(0) == 'a') {
        return 1 + countA(word.substring(1));
    } else {
        return countA(word.substring(1));
    }
}
```

### Possible Answers

- [ ] 0, 2
- [ ] 2, 1, 1, 0
- [ ] 0, 1, 1, 2
- [ ] I don’t know
- [ ] 1, 1, 2
- [ ] 2, 0
- [ ] 2, 1, 1

---

## Question 2

Modify the recursive function so that it returns **true** if the word contains an `'a'`, and **false** otherwise.
You must use recursion.

### Template

```java
boolean hasA(String word) {
    if (word.length() == 0) return false;
    if (word.charAt(0) == 'a') return true;
    return hasA(word.substring(1));
}
```

### Example Results

| Input     | Result |
| --------- | ------ |
| `""`      | false  |
| `"bo"`    | false  |
| `"abe"`   | true   |
| `"abama"` | true   |

---

## Question 3

Implement a **recursive function** that counts the number of `'a'` characters in a word.
Example: `countA("ada") = 2`.
You must use recursion.

### Template

```java
int countA(String word) {
    ...
}
```

| Input     | Result |
| --------- | ------ |
| `""`      | 0      |
| `"bo"`    | 0      |
| `"abe"`   | 1      |
| `"abama"` | 3      |

---

# 🎓 Thank You

Thank you for taking the time to complete this quiz.
Your participation is **anonymous** and contributes to our **master’s thesis research** on how students interact with AI and TAs in learning environments.
