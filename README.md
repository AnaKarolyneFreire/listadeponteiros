# listadeponteiros

Nome: Ana Karolyne e Pâmela Marcela 

Matrícula: 20230087566 e 20230079232

Questão 1: 
#include <stdio.h>

int main() {
    int i = 3, j = 5;
    int *p, *q;
    p = &i;
    q = &j;

    printf("1° p == &i: %d\n", p == &i);
  //Aqui, 'p' é um ponteiro que aponta para o endereço de memória da variável 'i', enquanto '&i' é o endereço de memória de 'i'. Portanto, 'p' é igual a '&i'. A expressão resultará em verdadeiro, ou seja, 1 em C, porque ambos 'p' e '&i' apontam para o mesmo endereço de memória.
    printf("2° *p - *q: %d\n", *p - *q);
  //Aqui, '*p' representa o valor armazenado no endereço de memória apontado por 'p', ou seja, o valor de 'i' (que é 3). '*q' representa o valor armazenado no endereço de memória apontado por 'q', ou seja, o valor de 'j' (que é 5). Portanto, a expressão resultará em '3 - 5', que é igual 'a -2'.
    printf("3° **&p: %d\n", **&p);
  //'&p' é o endereço de memória do ponteiro 'p', que aponta para o endereço de memória de 'i'. '*' aplicado duas vezes dereferencia esse ponteiro duas vezes, o que significa que obtemos o valor armazenado na variável 'i'. Portanto, a expressão resultará em 3.
    printf("4° 3 - *p/(*q) + 7: %d\n", 3 - *p/(*q) + 7);
  //Primeiro, '*p' resulta no valor de 'i', que é 3. Em seguida, '(*q)' resulta no valor de 'j', que é 5. Então, temos '3 - 3/5 + 7'. A operação de divisão (3/5) em C entre inteiros resulta em 0, porque o resultado é um inteiro. Portanto, a expressão se torna '3 - 0 + 7', que é igual a 10.

    return 0;
}
