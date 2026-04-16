# 📚 Libft — Your First Own Library

[Leia em Português](README.pt.md)

> **42 School Project** | Version 16.1

![C](https://img.shields.io/badge/Language-C-blue?style=flat-square)
![42](https://img.shields.io/badge/School-42-black?style=flat-square)
![Norm](https://img.shields.io/badge/Norm-compliant-green?style=flat-square)

---

## 📖 Table of Contents

- [About](#about)
- [Structure](#structure)
- [Compilation](#compilation)
- [Part 1 — Libc Functions](#part-1--libc-functions)
- [Part 2 — Additional Functions](#part-2--additional-functions)
- [Bonus — Linked List Functions](#bonus--linked-list-functions)
- [Technical Rules](#technical-rules)

---

## About

**Libft** is the very first project at 42 School. The goal is to recode a set of standard C library functions from scratch, and to add extra utility functions that will be reused throughout the rest of the curriculum.

By building this library, you gain a deep understanding of how fundamental C functions work under the hood — memory, strings, characters, and linked lists.

---

## Structure

```
libft/
├── Makefile
├── libft.h
├── ft_*.c          ← mandatory source files
└── ft_*_bonus.c    ← bonus source files
```

The compiled output is a static library: **`libft.a`**

---

## Compilation

```bash
# Build the mandatory library
make

# Build with bonus functions
make bonus

# Clean object files
make clean

# Clean everything including libft.a
make fclean

# Full rebuild
make re
```

---

## Part 1 — Libc Functions

These functions replicate standard `libc` functions. All are prefixed with `ft_`.  
They do not use any external functions (except `malloc` where noted).

---

### Character Classification

#### `ft_isalpha`
```c
int ft_isalpha(int c);
```
Returns non-zero if `c` is an alphabetic letter (`a–z` or `A–Z`), zero otherwise.

---

#### `ft_isdigit`
```c
int ft_isdigit(int c);
```
Returns non-zero if `c` is a decimal digit (`0–9`), zero otherwise.

---

#### `ft_isalnum`
```c
int ft_isalnum(int c);
```
Returns non-zero if `c` is alphanumeric (letter or digit), zero otherwise.

---

#### `ft_isascii`
```c
int ft_isascii(int c);
```
Returns non-zero if `c` is a valid ASCII character (value between 0 and 127 inclusive).

---

#### `ft_isprint`
```c
int ft_isprint(int c);
```
Returns non-zero if `c` is a printable character (ASCII 32–126), zero otherwise.

---

### Character Conversion

#### `ft_toupper`
```c
int ft_toupper(int c);
```
Converts a lowercase letter to its uppercase equivalent. Returns `c` unchanged if it is not a lowercase letter.

---

#### `ft_tolower`
```c
int ft_tolower(int c);
```
Converts an uppercase letter to its lowercase equivalent. Returns `c` unchanged if it is not an uppercase letter.

---

### String Functions

#### `ft_strlen`
```c
size_t ft_strlen(const char *s);
```
Returns the number of characters in string `s`, not counting the terminating null byte `\0`.

---

#### `ft_strchr`
```c
char *ft_strchr(const char *s, int c);
```
Returns a pointer to the first occurrence of character `c` in string `s`.  
Returns `NULL` if `c` is not found.

---

#### `ft_strrchr`
```c
char *ft_strrchr(const char *s, int c);
```
Returns a pointer to the **last** occurrence of character `c` in string `s`.  
Returns `NULL` if `c` is not found.

---

#### `ft_strncmp`
```c
int ft_strncmp(const char *s1, const char *s2, size_t n);
```
Compares at most the first `n` bytes of strings `s1` and `s2`.  
Returns 0 if equal, a positive value if `s1 > s2`, a negative value if `s1 < s2`.

---

#### `ft_strlcpy`
```c
size_t ft_strlcpy(char *dst, const char *src, size_t size);
```
Copies up to `size - 1` characters from `src` to `dst`, always null-terminating the result.  
Returns the total length of `src`.

---

#### `ft_strlcat`
```c
size_t ft_strlcat(char *dst, const char *src, size_t size);
```
Appends `src` to `dst`, ensuring the result is null-terminated and does not exceed `size` bytes total.  
Returns the combined length of both strings.

---

#### `ft_strnstr`
```c
char *ft_strnstr(const char *haystack, const char *needle, size_t len);
```
Searches for the first occurrence of `needle` within the first `len` bytes of `haystack`.  
Returns a pointer to the match, or `NULL` if not found. If `needle` is empty, returns `haystack`.

---

#### `ft_atoi`
```c
int ft_atoi(const char *nptr);
```
Converts the string `nptr` to an integer.  
Skips leading whitespace. Handles optional `+` or `-` sign. Stops at the first non-digit character.

---

### Memory Functions

#### `ft_memset`
```c
void *ft_memset(void *s, int c, size_t n);
```
Fills the first `n` bytes of memory area `s` with the constant byte `c`.  
Returns a pointer to `s`.

---

#### `ft_bzero`
```c
void ft_bzero(void *s, size_t n);
```
Sets the first `n` bytes of the memory area pointed to by `s` to zero.

---

#### `ft_memcpy`
```c
void *ft_memcpy(void *dest, const void *src, size_t n);
```
Copies `n` bytes from memory area `src` to `dest`.  
**The areas must not overlap.** Returns `dest`.

---

#### `ft_memmove`
```c
void *ft_memmove(void *dest, const void *src, size_t n);
```
Copies `n` bytes from `src` to `dest`.  
**Handles overlapping memory areas safely.** Returns `dest`.

---

#### `ft_memchr`
```c
void *ft_memchr(const void *s, int c, size_t n);
```
Scans the first `n` bytes of memory area `s` for the first occurrence of byte `c`.  
Returns a pointer to the match, or `NULL` if not found.

---

#### `ft_memcmp`
```c
int ft_memcmp(const void *s1, const void *s2, size_t n);
```
Compares the first `n` bytes of memory areas `s1` and `s2`.  
Returns 0 if equal, otherwise the difference between the first differing bytes.

---

### Allocation Functions

#### `ft_calloc`
```c
void *ft_calloc(size_t nmemb, size_t size);
```
Allocates memory for `nmemb` elements of `size` bytes each.  
All allocated bytes are **zero-initialized**.  
Returns `NULL` on allocation failure.

---

#### `ft_strdup`
```c
char *ft_strdup(const char *s);
```
Allocates sufficient memory and returns a duplicate of the string `s`.  
Returns `NULL` on allocation failure.

---

## Part 2 — Additional Functions

These functions are not in the standard `libc`, or exist in a different form.

---

#### `ft_substr`
```c
char *ft_substr(char const *s, unsigned int start, size_t len);
```
Allocates and returns a substring from string `s`, beginning at index `start`, of maximum length `len`.  
Returns `NULL` if allocation fails.

| Parameter | Description |
|-----------|-------------|
| `s` | The source string |
| `start` | Start index in `s` |
| `len` | Maximum length of the substring |

---

#### `ft_strjoin`
```c
char *ft_strjoin(char const *s1, char const *s2);
```
Allocates and returns a new string that is the concatenation of `s1` followed by `s2`.  
Returns `NULL` if allocation fails.

---

#### `ft_strtrim`
```c
char *ft_strtrim(char const *s1, char const *set);
```
Allocates and returns a copy of `s1` with all characters present in `set` removed from both the beginning and end of the string.  
Returns `NULL` if allocation fails.

| Parameter | Description |
|-----------|-------------|
| `s1` | The string to trim |
| `set` | Set of characters to remove |

---

#### `ft_split`
```c
char **ft_split(char const *s, char c);
```
Allocates and returns a null-terminated array of strings, obtained by splitting `s` using `c` as a delimiter.  
Returns `NULL` if allocation fails.

| Parameter | Description |
|-----------|-------------|
| `s` | The string to split |
| `c` | The delimiter character |

---

#### `ft_itoa`
```c
char *ft_itoa(int n);
```
Allocates and returns a string representing the integer `n`.  
Handles negative numbers. Returns `NULL` if allocation fails.

---

#### `ft_strmapi`
```c
char *ft_strmapi(char const *s, char (*f)(unsigned int, char));
```
Applies function `f` to each character of string `s`, passing the index and character as arguments.  
Returns a new string built from the successive results. Returns `NULL` if allocation fails.

| Parameter | Description |
|-----------|-------------|
| `s` | The source string |
| `f` | Function to apply: receives index + character, returns new character |

---

#### `ft_striteri`
```c
void ft_striteri(char *s, void (*f)(unsigned int, char*));
```
Applies function `f` to each character of string `s` in-place, passing the index and a pointer to the character.  
The character can be modified directly through the pointer.

---

#### `ft_putchar_fd`
```c
void ft_putchar_fd(char c, int fd);
```
Outputs character `c` to the given file descriptor `fd`.

| `fd` value | Destination |
|------------|-------------|
| `0` | stdin |
| `1` | stdout |
| `2` | stderr |

---

#### `ft_putstr_fd`
```c
void ft_putstr_fd(char *s, int fd);
```
Outputs string `s` to file descriptor `fd`.

---

#### `ft_putendl_fd`
```c
void ft_putendl_fd(char *s, int fd);
```
Outputs string `s` followed by a newline `\n` to file descriptor `fd`.

---

#### `ft_putnbr_fd`
```c
void ft_putnbr_fd(int n, int fd);
```
Outputs integer `n` as a string to file descriptor `fd`.

---

## Bonus — Linked List Functions

The bonus part introduces a singly linked list type:

```c
typedef struct s_list
{
    void         *content;
    struct s_list *next;
} t_list;
```

| Field | Description |
|-------|-------------|
| `content` | Data stored in the node (any type via `void *`) |
| `next` | Pointer to the next node, or `NULL` if last |

---

#### `ft_lstnew`
```c
t_list *ft_lstnew(void *content);
```
Allocates and returns a new list node.  
Sets `content` to the given value and `next` to `NULL`.

---

#### `ft_lstadd_front`
```c
void ft_lstadd_front(t_list **lst, t_list *new);
```
Adds node `new` at the **beginning** of the list pointed to by `lst`.

---

#### `ft_lstsize`
```c
int ft_lstsize(t_list *lst);
```
Counts and returns the number of nodes in the list.

---

#### `ft_lstlast`
```c
t_list *ft_lstlast(t_list *lst);
```
Returns a pointer to the **last node** of the list.

---

#### `ft_lstadd_back`
```c
void ft_lstadd_back(t_list **lst, t_list *new);
```
Adds node `new` at the **end** of the list pointed to by `lst`.

---

#### `ft_lstdelone`
```c
void ft_lstdelone(t_list *lst, void (*del)(void *));
```
Frees the memory of a single node's content using function `del`, then frees the node itself.  
Does **not** free the `next` pointer.

---

#### `ft_lstclear`
```c
void ft_lstclear(t_list **lst, void (*del)(void *));
```
Deletes and frees the given node **and all subsequent nodes** using `del` and `free`.  
Sets the list pointer to `NULL` at the end.

---

#### `ft_lstiter`
```c
void ft_lstiter(t_list *lst, void (*f)(void *));
```
Iterates through the list and applies function `f` to the content of each node.

---

#### `ft_lstmap`
```c
t_list *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *));
```
Iterates through `lst`, applies `f` to each node's content, and builds a **new list** from the results.  
Uses `del` to free content if an allocation fails mid-way.  
Returns `NULL` on failure.

---

## Technical Rules

- All files must comply with the **42 Norm**
- No global variables allowed
- Helper functions must be declared `static`
- No unexpected crashes (segfault, double-free, etc.)
- All heap memory must be properly freed — **no leaks tolerated**
- Compile with flags: `-Wall -Wextra -Werror`
- Use `ar` to create the library — `libtool` is forbidden
- All files must be at the **root** of the repository

---
