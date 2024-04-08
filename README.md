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

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 2:

/* 1. Endereço de memória apontado por 'p': 4094.
2. Endereço de memória 'p+1': 4094 + 2 = 4096.
3. Valor de '*p+2': Valor no endereço apontado por 'p' é 5, somando 2, resulta em 7.
4. Valor de '**&p': O endereço de 'p' é 4094, o valor no endereço 4094 é 5.
6. Valor de '3**p': 3 multiplicado por 5 resulta em 15.
7. Valor de '**&p+4': O endereço de 'p' é 4094, ao adicionar 4 ao valor nesse endereço, obtemos 4098 (4094 + 4 = 4098).*/

#include <stdio.h>

int main(void) {
  int i=5, *p;
  p = &i;
  printf("%p %p %d %d %d %d\n", p, p+1, *p+2, **&p, 3**p, **&p+4);
  return 0;
}

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 3:

1. `p = &i;`: Esta expressão é legal. Atribui o endereço de `i` ao ponteiro `p`.

2. `*q = &j;`: Esta expressão é ilegal. O lado esquerdo da atribuição espera um valor inteiro, mas o lado direito é um endereço de memória.

3. `p = &*&i;`: Esta expressão é legal. Aplica-se o operador de referência `&` a `i`, que retorna o endereço de `i`. Em seguida, o operador de dereferência `*` é aplicado a esse endereço, o que efetivamente faz `p` apontar para `i`.

4. `i = (*&)j;`: Esta expressão é ilegal. `(*&)` não é uma operação válida em C.

5. `i = *&j;`: Esta expressão é legal. Aplica-se o operador de referência `&` a `j`, que retorna o endereço de `j`. Em seguida, o operador de dereferência `*` é aplicado a esse endereço, obtendo o valor de `j`, que é atribuído a `i`.

6. `i = *&*&j;`: Esta expressão é legal. Aplica-se três vezes o operador de dereferência `*` ao endereço de `j`, resultando no valor de `j`, que é atribuído a `i`.

7. `q = *p;`: Esta expressão é ilegal. O lado direito da atribuição espera um valor inteiro, mas o lado esquerdo é um ponteiro.

8. `i = (*p)++ + *q;`: Esta expressão é ilegal. `(*p)++` tenta incrementar o valor apontado por `p`, mas `p` não é um ponteiro para uma variável, é apenas um ponteiro que aponta para um endereço de memória. Além disso, `*q` tenta acessar o valor apontado por `q`, mas `q` não foi inicializado corretamente para apontar para uma variável inteira.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 4:

#include <stdio.h>
int main() {
  int valor;
  int *p1;
  float temp;
  float *p2;
  char aux;
  char *nome = "Ponteiros";
  char *p3;
  int idade;
  int vetor[3];
  int *p4;
  int *p5;
  
  /* (a) */
  valor = 10;
  p1 = &valor;
  *p1 = 20;
  printf("%d \n", valor);
  //Isso atribui 10 à variável 'valor', faz 'p1' apontar para 'valor', e então altera o valor de 'valor' através de 'p1' para 20. Portanto, a saída será '20'.
  
  /* (b) */
  temp = 26.5;
  p2 = &temp;
  *p2 = 29.0;
  printf("%.1f \n", temp);
  //Semelhante ao anterior, isso altera o valor de 'temp' através do ponteiro 'p2'. Então a saída será '29.0'
  
  /* (c) */
  p3 = &nome[0];
  aux = *p3;
  printf("%c \n", aux);
  //'nome' é uma string literal, então 'p3' apontará para o primeiro caractere, que é 'P'. Portanto, a saída será 'P'.
  
  /* (d) */
  p3= &nome[4];
  aux= *p3;
  printf("%c \n", aux);
  //Isso faz 'p3' apontar para o quinto caractere da string (índice 4), que é 'e'. Então a saída será 'e'.
  
  /* (e) */
  p3= nome;
  printf("%c \n", *p3);
  //'p3' agora aponta para o início da string 'nome', então a saída será 'P'.
  
  /* (f) */
  p3= p3+4;
  printf("%c \n", *p3);
  //'p3' agora aponta para o quinto caractere da string 'nome', que é 'e', ntão a saída será 'e'.
  
  /* (g) */
  p3--;
  printf("%c \n", *p3);
  //'p3' é decrementado, então agora ele aponta para o quarto caractere da string, que é 't'.
  
  /* (h) */
  vetor[0]= 31;
  vetor[1]= 45;
  vetor[2]= 27;
  p4= vetor;
  idade= *p4;
  printf("%d \n", idade);
  //Isso atribui valores ao vetor e então faz 'p4' apontar para o primeiro elemento do vetor, que é 31. Então a saída será '31'.
  
  /* (i) */
  p5= p4+1;
  idade= *p5;
  printf("%d \n", idade);
  //Isso faz 'p5' apontar para o segundo elemento do vetor, que é 45. Então a saída será '45'.
  
  /* (j) */
  p4= p5+1;
  idade= *p4;
  printf("%d \n", idade);
  //Isso faz 'p4' apontar para o terceiro elemento do vetor, que é 27. Então a saída será '27'.

  /* (l) */
  p4= p4-2;
  idade= *p4;
  printf("%d \n", idade);
  //Isso faz 'p4' voltar dois elementos, então ele aponta para o primeiro elemento do vetor, que é 31. Então a saída será '31'.
  
  /* (m) */
  p5= &vetor[2]-1;
  printf("%d \n", *p5);
  //Isso faz 'p5' apontar para o penúltimo elemento do vetor, que é 45. Então a saída será '45'.
  
  /* (n) */
  p5++;
  printf("%d \n", *p5);
  //Isso faz 'p5' avançar para o último elemento do vetor, que é 27. Então a saída será '27'.
  
  return(0);
}

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 5:

int main(void){
  float vet[5] = {1.1,2.2,3.3,4.4,5.5};
  float *f;
  int i;
  f = vet;
  printf("contador/valor/valor/endereco/endereco\n");
  for(i = 0 ; i <= 4 ; i++){
  printf("i = %d",i); 
  // Imprime o valor do contador 'i'.
  printf(" vet[%d] = %.1f",i, vet[i]);
  //Imprime o valor do elemento 'vet[i]'.
  printf(" *(f + %d) = %.1f",i, *(f+i)); 
  //Imprime o valor apontado por 'f+i', que é equivalente a 'vet[i]'.
  printf(" &vet[%d] = %X",i, &vet[i]);
  //Imprime o endereço de memória do elemento 'vet[i]'.
  printf(" (f + %d) = %X",i, f+i);
  //Imprime o endereço de memória apontado por 'f+i', que é equivalente ao endereço de memória de 'vet[i]'.
  printf("\n");
  }
}

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 6:

/*A expressão que referencia o valor do terceiro elemento do vetor é 
*(pulo + 2). Isso ocorre porque pulo + 2 calcula o endereço de memória do terceiro elemento do vetor, e *(pulo + 2) dereferencia esse endereço para obter o valor armazenado lá.*/

#include <stdio.h>

int main() {
  int pulo[] = {1, 2, 3, 4, 5};

  int valor_terceiro_elemento = *(pulo + 2);

  printf("O valor do terceiro elemento do vetor pulo[] é: %d\n", valor_terceiro_elemento);

  return 0;
} 

Questão 7:

/*Todas as expressões são válidas. Este código declara um array mat com 4 elementos e inicializa-o com alguns valores. Em seguida, declara um ponteiro p e uma variável x. Cada expressão é executada e os resultados são impressos na tela.*/
#include <stdio.h>
int main() {
  int mat[4] = {10, 20, 30, 40};
  int *p, x;
  
  p = mat + 1;
  // Atribui o endereço do segundo elemento do array 'mat' a 'p'
  printf("Endereço do segundo elemento: %p\n", (void *)p);
  
   p = mat;
  // Atribui o endereço do primeiro elemento do array 'mat' a 'p'
  printf("Endereço do primeiro elemento: %p\n", (void *)p);
  
  x = (*mat);
  // Atribui o valor do primeiro elemento do array 'mat' a 'x'
  printf("Valor do primeiro elemento: %d\n", x);
   
   return 0;
}

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Questão 8:

Código 1

#include <stdio.h>
int main(){
  int vet[] = {4, 9, 13};
 //Isso cria um array de inteiros chamado 'vet' e inicializa-o com os valores {4, 9, 13}.
  int i; 
 //Declara uma variável inteira 'i' que será usada como contador no loop.
  
  for(i=0;i<3;i++)
 //Inicia um loop for que itera de 'i = 0' até 'i < 3', incrementando 'i' em cada iteração.
  {
  printf("%d ", *(vet+i));
  /*Em cada iteração do loop, isso imprime o valor do elemento atual do array 'vet'. '*(vet+i)' é a notação de ponteiro para acessar o valor do element no índice 'i' do array 'vet'. '*(vet+i)' é equivalente a vet[i].*/
  }
  return 0;
}

Código 2

#include <stdio.h>
int main(){
  int vet[] = {4, 9, 13};
  //Isso cria um array de inteiros chamado 'vet' e inicializa-o com os valores {4, 9, 13}.
  int i; 
  //Declara uma variável inteira 'i' que será usada como contador no loop.
  
  for(i=0;i<3;i++){ 
  //Inicia um loop for que itera de 'i = 0 até i < 3', incrementando 'i'em cada iteração.
  printf("%X ",vet+i);
  //Em cada iteração do loop, isso imprime o endereço de memória do elemento atual do array 'vet'. 'vet+i' é o endereço do elemento no índice 'i' do array 'vet'. '%X' é o especificador de formato usado para imprimir um valor em hexadecimal.
  }
  return 0;
}

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 9:

O programa contém alguns erros e, portanto, não irá compilar corretamente.
1. Em C, você não pode inicializar membros de uma estrutura dentro da definição da estrutura. Isso deve ser feito fora da definição da estrutura. Portanto, a definição int x = 3; e char nome[] = "jose"; está incorreta.

2. O ponteiro struct teste *s; está sendo usado sem inicialização. Isso pode resultar em comportamento indefinido ao tentar acessar membros da estrutura s sem atribuir um endereço válido a ele.

3. O nome do membro nome da estrutura é declarado como nome[], mas está sendo acessado como s->name no printf, o que causará um erro de compilação porque não existe nenhum membro chamado name na estrutura.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 10:

1. 'int const *x = 3;': Esta linha declara um ponteiro para uma constante inteira e tenta inicializá-lo com o valor '3'. No entanto, isso é incorreto, pois 'x' é um ponteiro para uma constante, o que significa que ele não pode ser usado para modificar o valor apontado.

2. '++(*x)': Esta linha tenta incrementar o valor apontado por 'x', mas como `x` é um ponteiro para uma constante, isso resulta em um comportamento indefinido. O compilador pode emitir um aviso ou erro, mas isso não é garantido. Em geral, tentar modificar o valor de uma constante resulta em comportamento indefinido.


