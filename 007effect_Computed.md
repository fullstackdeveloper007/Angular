# ✅ **1. What is a Computed?**

A **computed** is a **derived value** that automatically recalculates when its dependent signals change.

👉 **No side-effects**
👉 **Pure function**
👉 **Returns a value**
👉 **Used in templates or logic**

### Example

```ts
count = signal(1);

double = computed(() => count() * 2);
```

If `count()` changes → `double()` recomputes.

✔ Runs lazily (only when needed)
✔ Cannot modify state
✔ No async calls

---

# 🧨 **2. What is an Effect?**

An **effect** is used for **side-effects** — reacting to signal changes.

👉 Logs
👉 API calls
👉 localStorage updates
👉 DOM operations
👉 Service communication

### Example

```ts
effect(() => {
  console.log("Count changed:", count());
});
```

✔ Runs immediately
✔ Automatically tracks signals
✔ Can run many times
✔ Can perform async or impure operations
✔ No return value

---

# 🔥 **Computed vs Effect — Quick Comparison Table**

| Feature                            | **Computed**                 | **Effect**              |
| ---------------------------------- | ---------------------------- | ----------------------- |
| Purpose                            | Derive a new value           | Perform a side-effect   |
| Returns value                      | ✔ Yes                        | ✖ No                    |
| Pure?                              | ✔ Yes                        | ✖ No                    |
| Reacts to signals                  | ✔ Yes                        | ✔ Yes                   |
| Runs when dependent signals change | ✔ Yes                        | ✔ Yes                   |
| Should modify signals              | ✖ No                         | ✔ Sometimes allowed     |
| Use in template                    | ✔ Yes (`{{ double() }}`)     | ✖ No                    |
| Lazy execution                     | ✔ Yes                        | ✖ No (runs immediately) |
| Analogy                            | Computed property / selector | Listener / subscriber   |

---

# ⭐ **When to Use What?**

### ✔ Use **Computed** when:

* You want a **derived value**
* No external operation needed
* You want memoization
* You want a value usable in UI

**Example:**

```ts
fullName = computed(() => firstName() + " " + lastName());
```

---

### ✔ Use **Effect** when:

* You want a **side-effect**
* API call when signal changes
* Logging or analytics
* Writing to localStorage
* Updating a service or DOM

**Example:**

```ts
effect(() => {
  localStorage.setItem('count', count());
});
```

---

# 🔥 Example to Compare Both

```ts
count = signal(1);

double = computed(() => count() * 2);

effect(() => {
  console.log("Effect fired: ", double());
});
```

Flow:

* `count = 1` → effect runs once
* `count = 2` → computed recalculates, effect runs
* `count = 3` → same

---

# ⭐ Interview Answer (Short Version)

> **Computed** is a *derived, pure, lazy value* that recalculates when its signals change.
> **Effect** is a *side-effect function* that runs whenever its dependent signals change.
> Computeds return values; effects do not.
> Computeds are pure; effects handle async or impure work.

---

If you want, I can give you **real-world examples** like:

✔ API pagination
✔ Shopping cart total
✔ Auto-saving forms
✔ Debouncing search with signals and effect

Just ask!
