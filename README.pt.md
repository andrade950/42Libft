# 📚 Libft — A Tua Primeira Biblioteca

[Read in English](README.md)

> **Projecto da Escola 42** | Versão 16.1

![C](https://img.shields.io/badge/Linguagem-C-blue?style=flat-square)
![42](https://img.shields.io/badge/Escola-42-black?style=flat-square)
![Norm](https://img.shields.io/badge/Norma-conforme-green?style=flat-square)

---

## 📖 Índice

- [Sobre o Projecto](#sobre-o-projecto)
- [Estrutura](#estrutura)
- [Compilação](#compilação)
- [Parte 1 — Funções da Libc](#parte-1--funções-da-libc)
- [Parte 2 — Funções Adicionais](#parte-2--funções-adicionais)
- [Bónus — Funções de Lista Ligada](#bónus--funções-de-lista-ligada)
- [Regras Técnicas](#regras-técnicas)

---

## Sobre o Projecto

**Libft** é o primeiro projecto da 42 School. O objectivo é recodificar um conjunto de funções da biblioteca padrão de C a partir do zero, e adicionar funções utilitárias extra que serão reutilizadas ao longo de todo o percurso escolar.

Ao construir esta biblioteca, adquires uma compreensão profunda de como as funções fundamentais de C funcionam internamente — memória, strings, caracteres e listas ligadas.

---

## Estrutura

```
libft/
├── Makefile
├── libft.h
├── ft_*.c          ← ficheiros obrigatórios
└── ft_*_bonus.c    ← ficheiros de bónus
```

O resultado da compilação é uma biblioteca estática: **`libft.a`**

---

## Compilação

```bash
# Compilar a biblioteca obrigatória
make

# Compilar com as funções de bónus
make bonus

# Limpar os ficheiros objecto
make clean

# Limpar tudo, incluindo libft.a
make fclean

# Recompilar tudo
make re
```

---

## Parte 1 — Funções da Libc

Estas funções replicam funções da `libc` padrão. Todas têm o prefixo `ft_`.  
Não utilizam funções externas (excepto `malloc` onde indicado).

---

### Classificação de Caracteres

#### `ft_isalpha`
```c
int ft_isalpha(int c);
```
Devolve um valor diferente de zero se `c` for uma letra do alfabeto (`a–z` ou `A–Z`), zero caso contrário.

---

#### `ft_isdigit`
```c
int ft_isdigit(int c);
```
Devolve um valor diferente de zero se `c` for um dígito decimal (`0–9`), zero caso contrário.

---

#### `ft_isalnum`
```c
int ft_isalnum(int c);
```
Devolve um valor diferente de zero se `c` for alfanumérico (letra ou dígito), zero caso contrário.

---

#### `ft_isascii`
```c
int ft_isascii(int c);
```
Devolve um valor diferente de zero se `c` for um carácter ASCII válido (valor entre 0 e 127, inclusive).

---

#### `ft_isprint`
```c
int ft_isprint(int c);
```
Devolve um valor diferente de zero se `c` for um carácter imprimível (ASCII 32–126), zero caso contrário.

---

### Conversão de Caracteres

#### `ft_toupper`
```c
int ft_toupper(int c);
```
Converte uma letra minúscula para o equivalente maiúsculo. Devolve `c` sem alteração se não for uma minúscula.

---

#### `ft_tolower`
```c
int ft_tolower(int c);
```
Converte uma letra maiúscula para o equivalente minúsculo. Devolve `c` sem alteração se não for uma maiúscula.

---

### Funções de Strings

#### `ft_strlen`
```c
size_t ft_strlen(const char *s);
```
Devolve o número de caracteres da string `s`, sem contar o byte nulo terminador `\0`.

---

#### `ft_strchr`
```c
char *ft_strchr(const char *s, int c);
```
Devolve um apontador para a **primeira** ocorrência do carácter `c` na string `s`.  
Devolve `NULL` se `c` não for encontrado.

---

#### `ft_strrchr`
```c
char *ft_strrchr(const char *s, int c);
```
Devolve um apontador para a **última** ocorrência do carácter `c` na string `s`.  
Devolve `NULL` se `c` não for encontrado.

---

#### `ft_strncmp`
```c
int ft_strncmp(const char *s1, const char *s2, size_t n);
```
Compara, no máximo, os primeiros `n` bytes das strings `s1` e `s2`.  
Devolve 0 se forem iguais, um valor positivo se `s1 > s2`, negativo se `s1 < s2`.

---

#### `ft_strlcpy`
```c
size_t ft_strlcpy(char *dst, const char *src, size_t size);
```
Copia até `size - 1` caracteres de `src` para `dst`, garantindo sempre a terminação nula.  
Devolve o comprimento total de `src`.

---

#### `ft_strlcat`
```c
size_t ft_strlcat(char *dst, const char *src, size_t size);
```
Concatena `src` a `dst`, garantindo terminação nula e que o resultado não excede `size` bytes no total.  
Devolve o comprimento combinado das duas strings.

---

#### `ft_strnstr`
```c
char *ft_strnstr(const char *haystack, const char *needle, size_t len);
```
Procura a primeira ocorrência de `needle` nos primeiros `len` bytes de `haystack`.  
Devolve um apontador para a correspondência, ou `NULL` se não encontrar. Se `needle` for vazia, devolve `haystack`.

---

#### `ft_atoi`
```c
int ft_atoi(const char *nptr);
```
Converte a string `nptr` para um inteiro.  
Ignora espaços em branco iniciais. Suporta sinal opcional `+` ou `-`. Para no primeiro carácter que não seja dígito.

---

### Funções de Memória

#### `ft_memset`
```c
void *ft_memset(void *s, int c, size_t n);
```
Preenche os primeiros `n` bytes da zona de memória `s` com o byte constante `c`.  
Devolve um apontador para `s`.

---

#### `ft_bzero`
```c
void ft_bzero(void *s, size_t n);
```
Define os primeiros `n` bytes da zona de memória apontada por `s` como zero.

---

#### `ft_memcpy`
```c
void *ft_memcpy(void *dest, const void *src, size_t n);
```
Copia `n` bytes da zona de memória `src` para `dest`.  
**As zonas não devem sobrepor-se.** Devolve `dest`.

---

#### `ft_memmove`
```c
void *ft_memmove(void *dest, const void *src, size_t n);
```
Copia `n` bytes de `src` para `dest`.  
**Trata correctamente zonas de memória sobrepostas.** Devolve `dest`.

---

#### `ft_memchr`
```c
void *ft_memchr(const void *s, int c, size_t n);
```
Percorre os primeiros `n` bytes da zona de memória `s` à procura da primeira ocorrência do byte `c`.  
Devolve um apontador para a correspondência, ou `NULL` se não encontrar.

---

#### `ft_memcmp`
```c
int ft_memcmp(const void *s1, const void *s2, size_t n);
```
Compara os primeiros `n` bytes das zonas de memória `s1` e `s2`.  
Devolve 0 se forem iguais, caso contrário a diferença entre os primeiros bytes distintos.

---

### Funções de Alocação

#### `ft_calloc`
```c
void *ft_calloc(size_t nmemb, size_t size);
```
Aloca memória para `nmemb` elementos de `size` bytes cada.  
Todos os bytes alocados são **inicializados a zero**.  
Devolve `NULL` em caso de falha na alocação.

---

#### `ft_strdup`
```c
char *ft_strdup(const char *s);
```
Aloca memória suficiente e devolve um duplicado da string `s`.  
Devolve `NULL` em caso de falha na alocação.

---

## Parte 2 — Funções Adicionais

Estas funções não existem na `libc` padrão, ou existem de forma diferente.

---

#### `ft_substr`
```c
char *ft_substr(char const *s, unsigned int start, size_t len);
```
Aloca e devolve uma substring da string `s`, começando no índice `start`, com comprimento máximo `len`.  
Devolve `NULL` em caso de falha na alocação.

| Parâmetro | Descrição |
|-----------|-----------|
| `s` | A string de origem |
| `start` | Índice de início em `s` |
| `len` | Comprimento máximo da substring |

---

#### `ft_strjoin`
```c
char *ft_strjoin(char const *s1, char const *s2);
```
Aloca e devolve uma nova string resultante da concatenação de `s1` seguida de `s2`.  
Devolve `NULL` em caso de falha na alocação.

---

#### `ft_strtrim`
```c
char *ft_strtrim(char const *s1, char const *set);
```
Aloca e devolve uma cópia de `s1` com todos os caracteres presentes em `set` removidos do início e do fim da string.  
Devolve `NULL` em caso de falha na alocação.

| Parâmetro | Descrição |
|-----------|-----------|
| `s1` | A string a aparar |
| `set` | Conjunto de caracteres a remover |

---

#### `ft_split`
```c
char **ft_split(char const *s, char c);
```
Aloca e devolve um array de strings terminado em `NULL`, obtido por divisão de `s` usando `c` como delimitador.  
Devolve `NULL` em caso de falha na alocação.

| Parâmetro | Descrição |
|-----------|-----------|
| `s` | A string a dividir |
| `c` | O carácter delimitador |

---

#### `ft_itoa`
```c
char *ft_itoa(int n);
```
Aloca e devolve uma string que representa o inteiro `n`.  
Suporta números negativos. Devolve `NULL` em caso de falha na alocação.

---

#### `ft_strmapi`
```c
char *ft_strmapi(char const *s, char (*f)(unsigned int, char));
```
Aplica a função `f` a cada carácter da string `s`, passando o índice e o carácter como argumentos.  
Devolve uma nova string construída a partir dos resultados sucessivos. Devolve `NULL` em caso de falha.

| Parâmetro | Descrição |
|-----------|-----------|
| `s` | A string de origem |
| `f` | Função a aplicar: recebe índice + carácter, devolve novo carácter |

---

#### `ft_striteri`
```c
void ft_striteri(char *s, void (*f)(unsigned int, char*));
```
Aplica a função `f` a cada carácter da string `s` in-place, passando o índice e um apontador para o carácter.  
O carácter pode ser modificado directamente através do apontador.

---

#### `ft_putchar_fd`
```c
void ft_putchar_fd(char c, int fd);
```
Escreve o carácter `c` no descritor de ficheiro `fd`.

| Valor de `fd` | Destino |
|---------------|---------|
| `0` | stdin |
| `1` | stdout |
| `2` | stderr |

---

#### `ft_putstr_fd`
```c
void ft_putstr_fd(char *s, int fd);
```
Escreve a string `s` no descritor de ficheiro `fd`.

---

#### `ft_putendl_fd`
```c
void ft_putendl_fd(char *s, int fd);
```
Escreve a string `s` seguida de uma nova linha `\n` no descritor de ficheiro `fd`.

---

#### `ft_putnbr_fd`
```c
void ft_putnbr_fd(int n, int fd);
```
Escreve o inteiro `n` como string no descritor de ficheiro `fd`.

---

## Bónus — Funções de Lista Ligada

A parte de bónus introduz um tipo de lista simplesmente ligada:

```c
typedef struct s_list
{
    void          *content;
    struct s_list  *next;
} t_list;
```

| Campo | Descrição |
|-------|-----------|
| `content` | Dados armazenados no nó (qualquer tipo via `void *`) |
| `next` | Apontador para o próximo nó, ou `NULL` se for o último |

---

#### `ft_lstnew`
```c
t_list *ft_lstnew(void *content);
```
Aloca e devolve um novo nó de lista.  
Define `content` com o valor dado e `next` com `NULL`.

---

#### `ft_lstadd_front`
```c
void ft_lstadd_front(t_list **lst, t_list *new);
```
Adiciona o nó `new` ao **início** da lista apontada por `lst`.

---

#### `ft_lstsize`
```c
int ft_lstsize(t_list *lst);
```
Conta e devolve o número de nós da lista.

---

#### `ft_lstlast`
```c
t_list *ft_lstlast(t_list *lst);
```
Devolve um apontador para o **último nó** da lista.

---

#### `ft_lstadd_back`
```c
void ft_lstadd_back(t_list **lst, t_list *new);
```
Adiciona o nó `new` ao **fim** da lista apontada por `lst`.

---

#### `ft_lstdelone`
```c
void ft_lstdelone(t_list *lst, void (*del)(void *));
```
Liberta a memória do conteúdo de um único nó usando a função `del`, depois liberta o próprio nó.  
**Não** liberta o apontador `next`.

---

#### `ft_lstclear`
```c
void ft_lstclear(t_list **lst, void (*del)(void *));
```
Elimina e liberta o nó dado **e todos os nós seguintes** usando `del` e `free`.  
Define o apontador para a lista como `NULL` no final.

---

#### `ft_lstiter`
```c
void ft_lstiter(t_list *lst, void (*f)(void *));
```
Itera pela lista e aplica a função `f` ao conteúdo de cada nó.

---

#### `ft_lstmap`
```c
t_list *ft_lstmap(t_list *lst, void *(*f)(void *), void (*del)(void *));
```
Itera por `lst`, aplica `f` ao conteúdo de cada nó e constrói uma **nova lista** a partir dos resultados.  
Utiliza `del` para libertar conteúdo em caso de falha de alocação a meio.  
Devolve `NULL` em caso de falha.

---

## Regras Técnicas

- Todos os ficheiros devem cumprir a **Norma da 42**
- Variáveis globais não são permitidas
- Funções auxiliares devem ser declaradas como `static`
- Não são permitidos crashes inesperados (segfault, double-free, etc.)
- Toda a memória alocada no heap deve ser correctamente libertada — **não são toleradas fugas de memória**
- Compilar com as flags: `-Wall -Wextra -Werror`
- Usar `ar` para criar a biblioteca — `libtool` é proibido
- Todos os ficheiros devem estar na **raiz** do repositório

---
