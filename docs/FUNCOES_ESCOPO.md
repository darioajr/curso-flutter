# Funções e escopo no DART

As funções são blocos de código que podem ser reutilizados e chamados com diferentes parâmetros, permitindo a modularização e a organização do código. O escopo define a área do código onde uma variável ou função é acessível. A seguir, são apresentadas informações sobre funções e escopo no DART.

## Funções

### 1. Declaração de funções

No DART, você pode declarar funções usando a palavra-chave `void` (caso a função não retorne um valor) ou especificando o tipo de retorno. Exemplo:

```dart
void saudacao() {
  print('Olá, mundo!');
}

String saudacaoComNome(String nome) {
  return 'Olá, $nome!';
}
```

### 2. Chamada de funções

Para chamar uma função, use seu nome seguido de parênteses e, se necessário, passe os argumentos. Exemplo:

```dart
saudacao();

String mensagem = saudacaoComNome('Maria');
print(mensagem);
```

### 3. Funções anônimas (lambda)

As funções anônimas, também conhecidas como funções lambda, são funções sem nome que podem ser usadas como expressões. Exemplo:

```dart
List<int> numeros = [1, 2, 3, 4, 5];
numeros.forEach((int numero) {
  print('Número: $numero');
});
```

## Escopo

### 1. Escopo de variáveis

O escopo de uma variável define onde ela pode ser acessada no código. No DART, o escopo é determinado pelos blocos de código, como funções e estruturas de controle.

Variáveis declaradas dentro de uma função só podem ser acessadas dentro dessa função.

Variáveis declaradas fora de funções (no escopo global) podem ser acessadas em qualquer lugar no mesmo arquivo.

### 2. Escopo de funções

As funções podem ser declaradas no escopo global ou dentro de outras funções.

Funções declaradas no escopo global podem ser chamadas em qualquer lugar no mesmo arquivo.

Funções declaradas dentro de outras funções só podem ser chamadas dentro da função em que foram declaradas.

Exemplo de escopo de variáveis e funções:

```dart
int variavelGlobal = 10;

void funcaoExterna() {
  int variavelLocal = 20;

  void funcaoInterna() {
    print('Variável global: $variavelGlobal');
    print('Variável local: $variavelLocal');
  }

  funcaoInterna();
}

void main() {
  funcaoExterna();
}
```


Compreender funções e escopo no DART é fundamental para escrever códigos modulares e organizados, facilitando a manutenção e o entendimento do código ao longo do tempo.