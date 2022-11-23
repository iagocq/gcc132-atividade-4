# Pangrama

Pangrama é uma *frase* que usa **todas** as letras do alfabeto pelo menos uma vez.

Exemplos:
- The quick brown fox jumps over the lazy dog.
- Sphinx of black quartz, judge my vow.
- TV faz quengo explodir com whisky JB.

Fontes:
- <https://en.wikipedia.org/wiki/Pangram>
- <https://pt.wikipedia.org/wiki/Pangrama>

![Uma raposa pulando sobre um cachorro](https://upload.wikimedia.org/wikipedia/commons/8/80/Fox_Jumping_Over_A_Dog_in_Signaling_for_Boys.png)

## Verificação de Pangrama

```c
#include <stdio.h>
#include <ctype.h>

int main() {
    char letras[] = "abcdefghijklmnopqrstuvwxyz";
    int vistas[256 << sizeof(char)] = {};
    char c;

    while ((c = getchar()) != EOF) {
      vistas[tolower(c)] = 1;
    }

    int pangrama = 1;
    for (int i = 0; i < sizeof(letras)-1 && pangrama; i++) {
      c = letras[i];
      if (vistas[c] == 0) {
        pangrama = 0;
      }
    }

    return !pangrama;
}

```
