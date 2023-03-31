# Variáveis, tipos de dados e operadores no DART

A linguagem DART possui diversos tipos de dados e operadores para manipulação de valores e variáveis. Abaixo, segue uma descrição desses elementos:

## Variáveis

No DART, uma variável é um espaço na memória onde um valor pode ser armazenado e posteriormente recuperado. Para declarar uma variável, você pode usar a palavra-chave `var` ou especificar diretamente o tipo de dado. Aqui estão alguns exemplos:

```dart
var nome = 'João';
String sobrenome = 'Silva';
int idade = 30;
double altura = 1.75;
bool maiorIdade = true;
```


## Tipos de dados

DART possui vários tipos de dados básicos para representar números, texto, valores booleanos e outros. Alguns dos tipos de dados mais comuns são:


### 1. int

Representa números inteiros. Exemplo:

```dart
int idade = 25;
```

### 2. double

Representa números de ponto flutuante (números reais). Exemplo:

```dart
double altura = 1.80;
```

### 3. String

Representa sequências de caracteres (texto). Exemplo:

```dart
String nome = 'Maria';
```

### 4. bool

Representa valores booleanos (true ou false). Exemplo:

```dart
bool ativo = true;
```

### 5. List

Representa uma coleção de itens (também chamada de array). Exemplo:

```dart
List<int> numeros = [1, 2, 3, 4, 5];
```

### 6. Map

Representa um conjunto de pares chave-valor. Exemplo:

```dart
Map<String, int> frutas = {'maçã': 5, 'banana': 10, 'laranja': 15};
```

## Operadores

DART possui diversos operadores que permitem realizar operações matemáticas, lógicas e de comparação. Alguns dos operadores mais comuns são:

### Operadores matemáticos

Adição: +

Subtração: -

Multiplicação: *

Divisão: /

Divisão inteira: ~/

Resto da divisão: %


### Operadores de comparação

Igualdade: ==

Desigualdade: !=

Maior que: >

Menor que: <

Maior ou igual a: >=

Menor ou igual a: <=


### Operadores lógicos

E lógico (AND): &&

Ou lógico (OR): ||

Negação lógica (NOT): !


### Operadores de atribuição

Atribuição simples: =

Atribuição com adição: +=

Atribuição com subtração: -=

Atribuição com multiplicação: *=

Atribuição com divisão: /=

Atribuição com divisão inteira: ~/=

Atribuição com resto da divisão: %=


### Operadores de incremento e decremento

Incremento: ++

Decremento: --


Esses são alguns dos tipos de dados e operadores básicos disponíveis no DART para manipulação de variáveis.