# Recursion Assessment DEMO

## About This Assessment

This quiz is about **Recursion** — a method of solving computational problems where the solution depends on smaller instances of the same problem.

Please note:

* You are **not graded** on syntax; focus on reasoning.
* There are **8 questions**.
* Each question includes an *“I don’t know”* option.
* You have **1 hour** to complete the test.

You must use only the resources assigned to your group:

* **Group A** — Teaching Assistants (TAs) only
* **Group B** — CustomGPT AI only
* **Group C** — Both TAs and CustomGPT AI

---

## 🧩 Group Assignment

**Please indicate which experimental group you have been assigned to:**

* [ ] Group A — using Teaching Assistants (TAs) only
* [ ] Group B — using AI (our CustomGPT) only
* [ ] Group C — using both TAs and AI (our CustomGPT)

---

## 🧠 Consent to Participate in Research

We are master's students from IT University of Copenhagen conducting research for our thesis.

By participating, you confirm:

* Participation is **anonymous**.
* We only analyze **group data**.
* Data is **confidential** and used only for research.
* Only Groups **B** and **C** may use CustomGPT.
* Follow the test in order; do not go back.

**I hereby consent to my data being collected and used for research:**

* [ ] Yes
* [ ] No

---

## ⚧ Gender

**What is your gender?**

* [ ] Man
* [ ] Woman
* [ ] Non-binary
* [ ] Prefer not to say

---

# 🧩 Problem 1

---

## Question 1.1

Following code implements a **recursive** function that computes the factorial value of `n`.
Example: `fac(3) = 6`.

What is the sequence of recursive calls and their arguments, if we call `fac(3)`?

### Code

```c
int fac(int n) {
    if (n == 0) return 1;
    return n * fac(n - 1);
}
```

### Possible answers

* [ ] fac(0), fac(6)
* [ ] fac(6), fac(0)
* [ ] fac(1), fac(2), fac(3)
* [ ] fac(3), fac(2), fac(1)
* [ ] fac(0), fac(1), fac(2), fac(3)
* [ ] fac(3), fac(2), fac(1), fac(0)
* [ ] I don't know

---

## Question 1.2

Following code implements a **recursive** function that computes the factorial value of `n`.
Example: `fac(3) = 6`.

What is the sequence of **return values** from all recursive calls, if we call `fac(3)`?

### Code

```c
int fac(int n) {
    if (n == 0) return 1;
    return n * fac(n - 1);
}
```

### Possible answers

* [ ] 6, 2, 1
* [ ] 6, 2, 1, 1
* [ ] 6, 0
* [ ] 1, 2, 6
* [ ] 1, 1, 2, 6
* [ ] 0, 6
* [ ] I don't know

---

## Question 2

The following code implements a recursive function that computes the factorial value of `n` (`n!`).

Rewrite the code so that it computes the **accumulated sum of n** instead of the factorial value.
Use recursion.

### Instruction

> Example: `sum(3) = 6`, since `3 + 2 + 1 + 0 = 6`.

### Template

```c
int sum(int n) {
    if (n == ...) return ...;
    return n ... sum(n - 1);
}
```

### Reference Table

| n | Calculation   | Result |
| - | ------------- | ------ |
| 0 | 0             | = 0    |
| 1 | 1 + 0         | = 1    |
| 2 | 2 + 1 + 0     | = 3    |
| 3 | 3 + 2 + 1 + 0 | = 6    |

---

## Question 3

You must implement a **recursive** function that computes the factorial value of `n`.

Example:

> `fact(3) = 6`, since `3 * 2 * 1 = 6`.

### Template

```c
int fac(int n) {
    // your code here
}
```

### Reference Table

| n | Expression | Result |
| - | ---------- | ------ |
| 0 | 1          | = 1    |
| 1 | 1          | = 1    |
| 2 | 2 * 1      | = 2    |
| 3 | 3 * 2 * 1  | = 6    |

---

# 🎓 Thank You!

Thank you for participating in this quiz.
Your responses are anonymous and will be used solely for research in the IT University of Copenhagen master’s thesis.

---

Would you like me to also **convert this quiz into an interactive Markdown form** (e.g., for GitHub Pages or Jupyter Notebook use, with radio buttons and text inputs)?
