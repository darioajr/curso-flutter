# Estruturas condicionais e de repetição no DART

As estruturas condicionais e de repetição são fundamentais em qualquer linguagem de programação, e no DART não é diferente. Essas estruturas permitem controlar o fluxo de execução do código e realizar tarefas repetitivas. A seguir, são apresentadas as principais estruturas condicionais e de repetição no DART.

## Estruturas condicionais

### 1. `if` e `else`

A estrutura condicional `if` permite executar um bloco de código se uma determinada condição for verdadeira. A cláusula `else` é opcional e permite executar um bloco de código caso a condição seja falsa. Exemplo:

```dart
int idade = 18;

if (idade >= 18) {
  print('Maior de idade');
} else {
  print('Menor de idade');
}
```

### 2. else if

A cláusula else if permite verificar várias condições em sequência. Exemplo:

```dart
int nota = 75;

if (nota >= 90) {
  print('A');
} else if (nota >= 80) {
  print('B');
} else if (nota >= 70) {
  print('C');
} else if (nota >= 60) {
  print('D');
} else {
  print('F');
}
```

## Estruturas de repetição

### 1. for

O laço for permite repetir um bloco de código por um número determinado de vezes. Exemplo:

```dart
for (int i = 0; i < 10; i++) {
  print('Repetição $i');
}
```

### 2. while

O laço while permite repetir um bloco de código enquanto uma condição for verdadeira. Exemplo:

```dart
int contador = 0;

while (contador < 10) {
  print('Repetição $contador');
  contador++;
}
```

### 3. do-while

O laço do-while é semelhante ao laço while, mas a condição é verificada após a execução do bloco de código. Isso garante que o bloco de código seja executado pelo menos uma vez. Exemplo:

```dart
int contador = 0;

do {
  print('Repetição $contador');
  contador++;
} while (contador < 10);
```

### 4. for-in

O laço for-in permite iterar sobre os elementos de uma coleção, como uma lista ou um conjunto. Exemplo:

```dart
List<String> frutas = ['maçã', 'banana', 'laranja'];

for (String fruta in frutas) {
  print(fruta);
}
```


Com essas estruturas condicionais e de repetição, você pode controlar o fluxo de execução do seu código DART e realizar tarefas complexas e repetitivas de maneira eficiente.

