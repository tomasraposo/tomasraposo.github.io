_Notes on C programming_

* Debugging in C

```C
#define DEBUG(fmt, ...) \
  do { 
      if (DEBUG) { \
      fprintf(stderr, fmt, __VA_ARGS__); \
      fflush(stderr); \ 
      } \ 
     } \
    while (0)
```
