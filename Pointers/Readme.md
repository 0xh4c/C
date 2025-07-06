# 🔗 Master C Pointers

Welcome to **Master C Pointers** — a beginner-to-advanced guide that helps you understand how pointers work in C with **real code examples**, **simple explanations**, and **clear structure**. Whether you're a student, a beginner in systems programming, or diving into reverse engineering/malware dev, this repo is built to help you gain **confidence with pointers**.

---

## 📘 What You'll Learn

* What pointers are and why they're used
* How to manipulate variables using addresses
* Function pointers and callbacks
* Dynamic memory and how malloc/free work
* Pointer-related bugs (like memory leaks)
* Practical use cases (arrays, strings, function return)

---

## 📚 Pointer Concepts with Code (For Beginners to Advanced)

---

### 1. 🧠 What Are Pointers?

```c
int a = 5;
int *p = &a;

printf("%d\n", a);     // 5
printf("%p\n", &a);    // address of a
printf("%p\n", p);     // same as &a
printf("%d\n", *p);    // 5 — value at that address
```

✅ A pointer holds the memory address of another variable.
✅ `*p` dereferences the pointer and gives the value at that address.
✅ `&a` gives the address of variable `a`.

---

### 2. 🧪 Swap Variables Using Pointers

```c
int x = 10, y = 20;
int *p1 = &x, *p2 = &y;

int temp = *p1;
*p1 = *p2;
*p2 = temp;
```

✅ Swap values using pointer dereferencing.

---

### 3. 🔒 Why Pointers are Strong Types

```c
int a = 100;
float *fp = (float*)&a;
printf("%f\n", *fp);  // garbage output
```

⚠️ You can't use `float*` on an `int` safely.
Pointers are **type-sensitive** to avoid misinterpretation of data.

---

### 4. 🫭 Void Pointer

```c
int a = 10;
void *vp = &a;

printf("%d\n", *(int*)vp);  // cast required
```

✅ `void *` is a **generic pointer**, useful in libraries.
✅ Must **typecast** before dereferencing.

---

### 5. 🧬 Pointer to Pointer

```c
int a = 42;
int *p = &a;
int **pp = &p;

printf("%d\n", **pp);  // outputs 42
```

✅ Use `**pp` to go one level deeper.
✅ Useful in argv, double-pointer APIs, and matrix manipulations.

---

### 6. 🔁 Call by Reference with Pointers

```c
void update(int *n) {
    *n += 5;
}

int x = 10;
update(&x);
printf("%d\n", x);  // 15
```

✅ Pass address to modify the variable **inside a function**.

---

### 7. 📚 Pointers and Arrays

```c
int arr[] = {10, 20, 30};
int *p = arr;

printf("%d\n", *(p + 1));  // 20
```

✅ Array name behaves like a pointer to the first element.

---

### 8. 📨 Array as Function Argument

```c
void print(int *arr, int size) {
    for(int i = 0; i < size; i++)
        printf("%d ", arr[i]);
}

int main() {
    int a[] = {1, 2, 3};
    print(a, 3);
}
```

✅ Arrays are passed to functions as pointers.

---

### 9. ✍️ Character Arrays & Pointers

```c
char str[] = "hello";
char *p = str;

while (*p)
    putchar(*p++);
```

✅ Strings are character arrays, accessed using `char *`.

---

### 10. 🧱 Multi-Dimensional Arrays & Pointers

```c
int arr[2][2] = {{1, 2}, {3, 4}};
int (*p)[2] = arr;

printf("%d\n", p[1][1]);  // 4
```

✅ `int (*p)[2]` means p points to a full row (2 ints).

---

### 11. 📂 Dynamic Memory Allocation

```c
int *arr = malloc(3 * sizeof(int));
arr[0] = 10; arr[1] = 20; arr[2] = 30;

for(int i = 0; i < 3; i++)
    printf("%d ", arr[i]);

free(arr);
```

✅ `malloc()` allocates memory on heap.
✅ Always `free()` allocated memory.

---

### 12. 🔄 Pointers as Function Return

```c
int* getVal() {
    static int x = 99;
    return &x;
}

int *p = getVal();
printf("%d\n", *p);  // 99
```

✅ Use `static` or `malloc()` to safely return pointers.

---

### 13. 🎯 Function Pointers

```c
void greet() {
    printf("Hello!\n");
}

void (*fptr)() = greet;
fptr();  // calls greet
```

✅ Used to call functions indirectly.

---

### 14. 🔁 Callback using Function Pointer

```c
void sayHi() {
    printf("Hi!\n");
}

void callFunction(void (*f)()) {
    f();
}

callFunction(sayHi);
```

✅ Common in event-driven and plugin-based systems.

---

### 15. 💨 What is Memory Leak?

```c
int *ptr = malloc(sizeof(int));
*ptr = 50;
// forgot to free(ptr);  → memory leak
```

⚠️ A memory leak happens when allocated memory is not freed.
✅ Always use `free()` after `malloc()`.

---

> ✨ Feel free to fork this, play with code, and contribute fixes or new examples!

Happy Coding ☕
