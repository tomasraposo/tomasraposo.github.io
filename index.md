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

* itoa implementation

```
char* itoa(int n) {
	if (n > INT_MAX) {
		fprintf(stderr, "Potential integer overflow.");
		exit(1);
	}
	int temp = n, len;
	char *str;
	if (n == 0) {
		*str = '\0';
		*str++ = '0';
		return str;
	} 
	if (n > 0) { 
		len = 0;
	} else { 
		len = 1; /* accommodate '-' sign */
		*str = '-';
	}
	while (temp) {
		temp /= 10;
		len++;
	}
	str = malloc(len * sizeof(char));
	if (!str) {
		fprintf(stderr, "%s\n.", "Unable to allocate sufficient memory.");
		exit(1);
	}
	temp = n;
	int i = len-1;
	while (temp) {
		*(str+i) = temp % 10 + '0';
		temp /= 10;
		i--;
	}
	return str;
}

```

* atoi implementation
```
int atoi(char* str) {
	int n = 0;
	int sign = 1;
	if (str[0] == '-') {
		sign = -1;
		str++;
	}
	while (str) {
		if (*str < '0' || *str > '9') {
			break;
		}
		n = n * 10 + *str - '0';
		str++;
	}
	return sign * n;
}
```
