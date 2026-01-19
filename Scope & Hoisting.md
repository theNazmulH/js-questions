# JavaScript Interview Prep: Scope & Hoisting

---

## 🔹 JavaScript Scope – Questions & Answers

### 1. What is scope in JavaScript?
**Answer:**  
Scope determines where variables, functions, and objects are accessible in your code. It defines the visibility and lifetime of variables.

---

### 2. What are the types of scope in JavaScript?
**Answer:**  
1. **Global Scope**  
2. **Function Scope**  
3. **Block Scope** (introduced with `let` and `const`)  
4. **Lexical Scope**

---

### 3. What is global scope?
**Answer:**  
Variables declared outside any function or block are in the global scope and can be accessed from anywhere in the program.

* **Risk:** Global variables can lead to "namespace pollution," where different parts of a program accidentally overwrite each other's data.
---

### 4. What is a function (Local) scope?
**Answer:**  
Variables declared with `var` inside a function are accessible only within that function.

```javascript
function sayHello() {
  let message = "Hi!"; // Local Scope
}
console.log(message); // ReferenceError: message is not defined
```
---

### 5. What is block scope?
**Answer:**  
Variables declared with `let` and `const` inside `{}` are only accessible within that block.

**Block:**
Any code between { } (if statements, loops, switch, etc.).

**Behavior:**
var does not recognize block scope; let and const do.

```
{
  var x = 1;
  let y = 2;
}
console.log(x); // 1
console.log(y); // ReferenceError: y is not defined
```

---

### 6. Does `var` have block scope?
**Answer:**  
No. `var` is function-scoped, not block-scoped.

---

### 7. What is lexical scope?

**Concept:** 
JavaScript uses Lexical Scoping (also called Static Scoping). This means that the scope of a variable is determined by its position within the source code (at write-time), not where it is called (at run-time).

**Answer:**  
Lexical scope means that a function can access variables from its parent scope where it was defined.

```
function outer() {
  let name = "Gemini";
  function inner() {
    console.log(name); // Accesses 'name' from outer lexical scope
  }
  inner();
}
```
---

### 8. What is scope chain?
**Answer:**  

When a variable is used in JavaScript, the engine looks up its value in the current scope. If it cannot find it, it looks in the outer scope and continues until it reaches the global scope. This "climbing" of scopes is called the Scope Chain.

Current scope → Parent scope → Global scope.

---

### 9. Can inner functions access outer variables?
**Answer:**  
Yes. Inner functions can access variables from their outer (parent) scope.

---

### 10. Can outer functions access inner variables?
**Answer:**  
No. Variables declared inside an inner function are not accessible outside it.

---

### 11. What happens if a variable is not found in any scope?
**Answer:**  
JavaScript throws a `ReferenceError`.

---

### 12. What is shadowing in JavaScript?
**Answer:**  
When a variable declared in an inner scope has the same name as one in an outer scope, it shadows the outer variable.

---

### 13. Is shadowing allowed with `var`, `let`, and `const`?
**Answer:**  
- `let` and `const` → allowed  
- `var` → can cause unexpected behavior

---

### 14. What is illegal shadowing?
**Answer:**  
Declaring a `let` or `const` variable with the same name as a `var` variable in the same scope.

---

### 15. What is a closure?
**Answer:**  
A closure is a function that remembers variables from its lexical scope even after the outer function has finished execution.

---

---

## 🔹 JavaScript Hoisting – Questions & Answers

### 16. What is hoisting?
**Answer:**  
Hoisting is JavaScript’s behavior of moving declarations to the top of their scope during compilation.

---

### 17. Are variables hoisted in JavaScript?
**Answer:**  
Yes, but behavior differs:
- `var` → hoisted and initialized as `undefined`
- `let` & `const` → hoisted but not initialized

---

### 18. Are functions hoisted?
**Answer:**  
- **Function declarations** → fully hoisted  
- **Function expressions** → hoisted like variables

---

### 19. What is the Temporal Dead Zone (TDZ)?
**Answer:**  
The time between entering a block and initializing a `let` or `const` variable, where accessing it throws an error.

---

### 20. What happens if you access a `var` variable before declaration?
**Answer:**  
It returns `undefined`.

---

### 21. What happens if you access a `let` or `const` before declaration?
**Answer:**  
It throws a `ReferenceError`.

---

### 22. Are arrow functions hoisted?
**Answer:**  
No. Arrow functions behave like function expressions.

---

### 23. Is `const` hoisted?
**Answer:**  
Yes, but it stays in the Temporal Dead Zone until initialized.

---

### 24. Can `const` variables be hoisted and used?
**Answer:**  
They are hoisted but cannot be accessed before declaration.

---

### 25. Difference between hoisting of `var`, `let`, and `const`?
**Answer:**  

| Keyword | Hoisted | Initialized | Scope |
|------|--------|------------|-------|
| var | Yes | undefined | Function |
| let | Yes | No (TDZ) | Block |
| const | Yes | No (TDZ) | Block |

---

### 26. What is function hoisting?
**Answer:**  
Function declarations are hoisted with their full definition.

---

### 27. What happens if two functions with the same name are declared?
**Answer:**  
The last function declaration overrides the previous one.

---

### 28. Is hoisting done at runtime?
**Answer:**  
No. Hoisting happens during the compilation phase.

---

### 29. Does JavaScript hoist initializations?
**Answer:**  
No. Only declarations are hoisted, not initializations.

---

### 30. How to avoid hoisting-related bugs?
**Answer:**  
- Use `let` and `const`
- Declare variables at the top
- Avoid `var`
- Enable strict mode

---
