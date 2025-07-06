# 🔗 Master C Pointers

Welcome to **Master C Pointers** — a beginner-to-advanced guide that helps you understand how pointers work in C with **real code examples**, **simple explanations**, and **clear structure**. Whether you're a student, a beginner in systems programming, or diving into reverse engineering/malware dev, this repo is built to help you gain **confidence with pointers**.

---

## 📘 What You'll Learn

- What pointers are and why they're used
- How to manipulate variables using addresses
- Function pointers and callbacks
- Dynamic memory and how malloc/free work
- Pointer-related bugs (like memory leaks)
- Practical use cases (arrays, strings, function return)

---

## 📚 Pointer Concepts with Code

Each concept is explained with a small code snippet and beginner-friendly explanation.

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

- `&a` gives address of `a`
- `*p` gives value stored at that address (dereferencing)

---

### 2. 🧪 Swap Variables with Pointers

```c
int x = 10, y = 20;
int *p1 = &x, *p2 = &y;

int temp = *p1;
*p1 = *p2;
*p2 = temp;
```

Swaps the values of `x` and `y` using pointers.

---

### 3. 🔒 Why Pointers are Strong Types

```c
int a = 100;
float *fp = (float*)&a;
printf("%f\n", *fp);  // garbage output
```

Pointers are **type-specific** — don’t mix `int*` with `float*`.

---

### 4. 🧭 Void Pointer

```c
int a = 10;
void *vp = &a;
printf("%d\n", *(int*)vp);  // must cast to correct type
```

`void *` can store any address but can't be directly dereferenced.

---

### 5. 🧬 Pointer to Pointer

```c
int a = 42;
int *p = &a;
int **pp = &p;

printf("%d\n", **pp);  // 42
```

Use double `**` to dereference pointer to pointer.

---

### 6. 🔁 Call by Reference with Pointers

```c
void update(int *n) {
    *n += 5;
}

int x = 10;
update(&x);  // x becomes 15
```

---

### 7. 📚 Pointers and Arrays

```c
int arr[] = {1, 2, 3};
int *p = arr;

printf("%d\n", *(p + 1));  // 2
```

---

### 8. 📨 Array as Function Argument

```c
void print(int *arr, int size) {
    for(int i = 0; i < size; i++)
        printf("%d ", arr[i]);
}
```

---

### 9. ✍️ Character Arrays & Pointers

```c
char str[] = "hello";
char *p = str;

while (*p)
    putchar(*p++);
```

---

### 10. 🧱 Multi-Dimensional Arrays & Pointers

```c
int arr[2][2] = {{1, 2}, {3, 4}};
int (*p)[2] = arr;

printf("%d\n", p[1][1]);  // 4
```

---

### 11. 💾 Dynamic Memory Allocation

```c
int *arr = malloc(3 * sizeof(int));
arr[0] = 10; arr[1] = 20; arr[2] = 30;

for(int i = 0; i < 3; i++) printf("%d ", arr[i]);

free(arr);
```

Use `malloc()` to allocate memory on heap, and always `free()` it later.

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

Use `static` or `malloc()` if you want to return pointers from functions.

---

### 13. 🎯 Function Pointers

```c
void greet() {
    printf("Hello!\n");
}

void (*fptr)() = greet;
fptr();  // call via pointer
```

---

### 14. 🔁 Callback using Function Pointer

```c
void sayHi() {
    printf("Hi!\n");
}

void callFunction(void (*f)()) {
    f();  // callback
}

callFunction(sayHi);
```

---

### 15. 🧨 What is Memory Leak?

```c
int *ptr = malloc(sizeof(int));
*ptr = 50;
// forgot free(ptr); → memory leak
```

Always use `free()` to release dynamically allocated memory.

---


## 🧠 Learn • Practice • Master
