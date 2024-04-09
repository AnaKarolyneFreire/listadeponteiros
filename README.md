# listadeponteiros

Nome: Ana Karolyne e Pâmela Marcela 

Matrícula: 20230087566 e 20230079232

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
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

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 12:

Para resumir:
             Os válidos são: 1, 4, 5, 8.
             Os inválidos são: 2, 3, 6, 7. 

1. aloha[2] = value; - É válido. Ele simplesmente atribui o valor da variável `value` ao array `aloha` com a posição 3.  

2. scanf("%f", &aloha); - Inválido. Ao invés disso, Você precisa fornecer o endereço do primeiro elemento do array, que seria `&aloha[0]` , ou seja, `scanf("%f", &aloha[0]);`. A função `scanf` espera um ponteiro para float, mas o array `aloha` não é um ponteiro para float, é um array de floats.  

3. aloha = "value"; - Inválido. Você não pode atribuir uma string diretamente a um array de floats.

4. printf("%f", aloha); - Inválido. Você está tentando imprimir todo o array `aloha` como um float, o que não é possível diretamente. Você pode imprimir os elementos do array usando um loop.

5. coisas[4][4] = aloha[3]; - Válido. Atribui o valor do quarto elemento do array `aloha` ao elemento na quarta linha e quinta coluna do array bidimensional `coisas`.

6. coisas[5] = aloha; - Inválido. Você está tentando atribuir um array unidimensional ( aloha)  a uma linha de um array bidimensional (coisas). Isso não é permitido em C.

7. pf = value; -  Você está tentando atribuir um float a um ponteiro para float, que é o 'pf'. Para fazer isso, você deve primeiro obter o endereço da variável `value`, usando o operador de referência '&'. Portanto, inválido. 

8. pf = aloha; - Atribuir `aloha` a `pf` é válido. Um ponteiro para float pode apontar para o primeiro elemento de um array de floats.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 13: 

Um vazamento de memória (do Inglês memory leak) ocorre quando o programa não libera para o sistema operacional memória que não é mais utilizada. Um problema que surge diretamente do gerenciamento incorreto da alocação dinâmica.
Como resultado, a memória alocada permanece reservada mesmo após o término da execução do programa, o que pode levar a um esgotamento gradual dos recursos do sistema.


	Abaixo estão três exemplos de programas em C que apresentam memory leaks:


1. O código abaixo, através da função 'to_italic' , recebe uma string e retorna ela com dois '*', no início e no fim dela.
Ao ser executado, o programa deve imprimir o seguinte:

**Hello, there!**
**Memory leak**


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *to_italic(char *s) {
    size_t len = strlen(s);
    char *result = malloc(len + 5); // assume que malloc não falhará
    sprintf(result, "**%s**", s);
    return result;
}
int main() {
    puts(to_italic("Hello, there!"));
    puts(to_italic("Memory leak"));
}

Perceba que em nenhum momento foi usado um ponteiro para acessar a região da memória que contém a string retornada pela função to_italic; a string foi passada diretamente para a função puts. Dessa forma, não é possível usar o free para liberar essa memória. Toda vez que a função to_italic for usada de forma similar a essa, a memória será perdida.

2. **Memory Leak em Função que Retorna um Ponteiro Alocado Dinamicamente:**

#include <stdlib.h>
int *allocate_memory() {
    int *ptr = (int *)malloc(sizeof(int));
    return ptr;
}
int main() {
    int *result = allocate_memory();
    // O ponteiro 'result' recebe a memória alocada dinamicamente,
    // mas nunca é liberado.
    return 0;
}

Neste exemplo, a função `allocate_memory()` aloca dinamicamente memória e retorna um ponteiro para ela. Mas, o ponteiro retornado nunca é liberado em `main()`, resultando em um memory leak.


3. **Memory Leak em Função que Perde a Referência para Memória Alocada:**

#include <stdlib.h>
void allocate_and_forget() {
    int *ptr = (int *)malloc(sizeof(int));
    // Nenhuma referência ao ponteiro 'ptr' é mantida após o término desta função,
    // então a memória alocada é perdida e não pode ser liberada.
}
int main() {
    allocate_and_forget();
    // A memória alocada dentro de 'allocate_and_forget()' é perdida e não pode ser liberada.
    return 0;
}
Neste exemplo, a função `allocate_and_forget()` aloca dinamicamente memória, mas não mantém nenhuma referência ao ponteiro alocado após o término da função. Como resultado, a memória alocada é perdida e não pode ser liberada, resultando em um memory leak.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 19: 

#include <stdio.h>

void soma_vetores(int vet1[], int vet2[], int resultado[], int tamanho) {
    for (int i = 0; i < tamanho; i++) {
        resultado[i] = vet1[i] + vet2[i];
    }
}
int main() {
    int tamanho;
    
    printf("Digite o tamanho dos vetores: ");
    scanf("%d", &tamanho);
    
    int vet1[tamanho], vet2[tamanho], resultado[tamanho];
    
    printf("Digite os elementos do primeiro vetor: ");
    for (int i = 0; i < tamanho; i++) {
        scanf("%d", &vet1[i]);
    }
    printf("Digite os elementos do segundo vetor: ");
    for (int i = 0; i < tamanho; i++) {
        scanf("%d", &vet2[i]);
    }
    soma_vetores(vet1, vet2, resultado, tamanho);
    printf("Vetor de soma: ");
    for (int i = 0; i < tamanho; i++) {
        printf("%d ", resultado[i]);
    }
    printf("\n");
    return 0;
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 20: 

#include <stdio.h>

void multiplica_matrizes(int *A, int *B, int *C, int linhas_A, int colunas_A, int colunas_B) {
    for (int i = 0; i < linhas_A; i++) {
        for (int j = 0; j < colunas_B; j++) {
            C[i * colunas_B + j] = 0; // Inicializa o elemento (i, j) de C com zero
            for (int k = 0; k < colunas_A; k++) {
                C[i * colunas_B + j] += A[i * colunas_A + k] * B[k * colunas_B + j]; // Realiza a multiplicação e acumula o resultado
            }
        }
    }
}

void imprime_matriz(int *matriz, int linhas, int colunas) {
    for (int i = 0; i < linhas; i++) {
        for (int j = 0; j < colunas; j++) {
            printf("%d ", matriz[i * colunas + j]);
        }
        printf("\n");
    }
}

int main() {
    int linhas_A = 2, colunas_A = 3, colunas_B = 4;
    
    int A[2][3] = {{1, 2, 3}, {4, 5, 6}};
    int B[3][4] = {{1, 2, 3, 4}, {5, 6, 7, 8}, {9, 10, 11, 12}};
    int C[2][4];
    
    multiplica_matrizes((int *)A, (int *)B, (int *)C, linhas_A, colunas_A, colunas_B);
    
    printf("Matriz A:\n");
    imprime_matriz((int *)A, linhas_A, colunas_A);
    
    printf("\nMatriz B:\n");
    imprime_matriz((int *)B, colunas_A, colunas_B);
    
    printf("\nMatriz C (resultado da multiplicação AxB):\n");
    imprime_matriz((int *)C, linhas_A, colunas_B);
    
    return 0;
}
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 21: 

Letra E.

 void f(int n){
  char *m = malloc(10);
  char *n = malloc(10);
  free(m);
  m = n;
  free(m);
  free(n);
}

Por que?
Porque a memória alocada para m (linha 4) é liberada antes da mesma ser atribída à n. O código dá erro pois qunado se iguala m e n ( linha 5) ,ambos apontam para a mesma posição de memória. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Questão 22: 

Analisando o código, podemos perceber que, inicialmente, x recebe o valor de a
                                                         y recebe o valor de b
                                                         z recebe a soma de a e b.
while (a) é um loop while que continuará executando enquanto o valor de `a` for diferente de zero.

x = x | b; - Atribui o resultado a x quando o operador `|` realiza uma operação OR bit a bit entre `x` e `b`.
y = y ^ a; -Atribui o resultado a y, quando o operador `^` realiza uma operação XOR bit a bit entre `y` e `a`. 
z = z & (a+b); O operador `&` realiza uma operação AND bit a bit entre `z` e `(a+b)`, e atribui o resultado a z.
a = a >> 1; A operação `>>` desloca todos os bits de `a` uma posição para a direita (equivale a uma divisão por 2).
b = b << 1; A operação `<<` desloca todos os bits de `b` uma posição para a esquerda (equivale a uma multiplicação por 2).

Então, após executar o loop explicado acima, com `a` começando com o valor 10 e `b` com o valor 1:
após a 4º iteração no loop, 'a' se torna 0, e só então a saída dp programa vai ser igual a '14 7 0', ou seja, valores de x, y e z respectivamente. 
