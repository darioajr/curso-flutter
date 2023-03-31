# Tratamento de erros e exceções no DART

O tratamento de erros e exceções é fundamental para garantir a estabilidade e a confiabilidade de um aplicativo. No DART, você pode usar blocos `try`, `catch`, `finally` e `throw` para lidar com erros e exceções. A seguir, são apresentadas informações sobre o tratamento de erros e exceções no DART.

## Blocos try, catch e finally

### 1. Bloco try

O bloco `try` é usado para envolver o código que pode gerar uma exceção. Se ocorrer uma exceção dentro do bloco `try`, a execução será transferida para o bloco `catch` correspondente.

```dart
try {
  // Código que pode gerar uma exceção
}
```

### 2. Bloco catch

O bloco catch é usado para capturar e lidar com exceções geradas no bloco try. Você pode especificar o tipo de exceção a ser capturado e ter acesso à exceção e à pilha de chamadas.

```dart
catch (e, s) {
  // Código para lidar com a exceção 'e' e a pilha de chamadas 's'
}
```

### 3. Bloco finally

O bloco finally é usado para executar código que deve ser executado independentemente de ter ocorrido uma exceção ou não. O bloco finally é opcional e é executado após o bloco try e/ou catch.

```dart
finally {
  // Código que será executado independentemente de uma exceção
}
```

### Exemplo de uso
```dart
void dividir(int a, int b) {
  try {
    int resultado = a ~/ b;
    print('Resultado da divisão: $resultado');
  } catch (e, s) {
    print('Exceção: $e');
    print('Pilha de chamadas: $s');
  } finally {
    print('Operação de divisão concluída.');
  }
}

void main() {
  dividir(10, 2);
  dividir(10, 0);
}
```

## Exceções personalizadas e uso do throw

### 1. Exceções personalizadas

Você pode criar suas próprias exceções personalizadas estendendo a classe Exception e sobrescrevendo o método toString(). Exemplo:

```dart
class DivisaoPorZeroException extends Exception {
  @override
  String toString() {
    return 'Não é possível dividir por zero!';
  }
}
```

### 2. Uso do throw

Você pode lançar exceções usando a palavra-chave throw. Exemplo:

```dart
void dividir(int a, int b) {
  if (b == 0) {
    throw DivisaoPorZeroException();
  }
  int resultado = a ~/ b;
  print('Resultado da divisão: $resultado');
}

void main() {
  try {
    dividir(10, 0);
  } catch (e) {
    print('Exceção: $e');
  }
}
```


Com o tratamento adequado de erros e exceções no DART, você pode garantir que seu aplicativo seja mais robusto e confiável, evitando falhas e melhorando a experiência do usuário.