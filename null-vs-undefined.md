# JavaScript Null vs. Undefined

Understanding the distinction between `null` and `undefined` is fundamental to mastering JavaScript's type system and memory management.

---

## 1. Core Definitions

### Undefined
`undefined` means a variable has been **declared** but has **not yet been assigned a value**. It is the default state provided by the JavaScript engine.
* **Analogy:** A box that has been labeled but is currently empty.

### Null
`null` is an **assignment value**. It represents the **intentional absence** of any object value. It must be explicitly assigned by the developer.
* **Analogy:** A box that has been labeled and then deliberately emptied or marked as "none."

---

## 2. Technical Comparison Table

| Feature | `undefined` | `null` |
| :--- | :--- | :--- |
| **Meaning** | Unintentional absence (Missing). | Intentional absence (Empty). |
| **Type (`typeof`)** | `"undefined"` | `"object"` (Legacy bug). |
| **Arithmetic context** | Becomes `NaN`. | Becomes `0`. |
| **Equality (`==`)** | `null == undefined` is **true**. | `null == undefined` is **true**. |
| **Strict Equality (`===`)**| `null === undefined` is **false**. | `null === undefined` is **false**. |

---

## 3. Common Scenarios

### When you will see `undefined`:
1. **Uninitialized variables:** `let x;`
2. **Missing function arguments:** When a caller doesn't provide a value for a parameter.
3. **Missing object properties:** Accessing `user.age` when `age` doesn't exist.
4. **No return statement:** A function that completes execution without a `return` keyword.

### When you should use `null`:
* When you want to reset a variable that previously held an object.
* When you are fetching data and want to explicitly show that a value is currently "empty" or "not found" (as opposed to simply being missing).

---

## 4. Interview "Deep Dive" Points

### The `typeof null` Bug
If an interviewer asks why `typeof null` is `"object"`, explain that it is a **legacy bug** from the first version of JavaScript. In the original implementation, values were stored in 32-bit units. The type tag for objects was `0`, and since `null` was represented as a null pointer (all zeros), it mistakenly flagged as an object.

### The Nullish Coalescing Operator (`??`)
Modern JS uses the "Nullish" concept to group these two together.

```javascript
let settings = user.theme ?? "default"; 
// Returns "default" ONLY if user.theme is null or undefined.
```

## 5. Quick Reference Code Snippet
```javascript
let a;
let b = null;

console.log(typeof a); // "undefined"
console.log(typeof b); // "object"

console.log(a + 10);   // NaN (undefined is not a number)
console.log(b + 10);   // 10  (null is treated as 0)

console.log(a == b);   // true
console.log(a === b);  // false
```

## 6. The Null/Undefined Type Paradox

### a. Is undefined a type?
Yes. undefined itself is a data type. There are 7 primitive types (String, Number, BigInt, Boolean, Undefined, Symbol, and Null) in JavaScript. 

### b. Is null a primitive or non-primitive ( As it is an object )
* **Technically:** It is a **Primitive**.
* **The typeof quirk:** `typeof null` returns `"object"`.
* **The Reason:** This is a legacy bug from JS version 1. Objects were tagged with `0` in memory, and `null` (the null pointer) was also represented as `0`. 
* **Interview Tip:** Always clarify that while `typeof` says object, `null` is fundamentally a primitive because it is immutable and does not have properties or methods.
