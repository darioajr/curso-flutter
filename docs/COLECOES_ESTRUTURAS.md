# Coleções e estruturas de dados no DART

As coleções e estruturas de dados são fundamentais para armazenar e gerenciar informações em aplicações. No DART, existem várias coleções e estruturas de dados disponíveis para facilitar a manipulação de dados. A seguir, são apresentadas as principais coleções e estruturas de dados no DART.

## List

`List` é uma estrutura de dados linear que armazena elementos em uma ordem específica. A lista permite acesso indexado aos elementos, adição, remoção e atualização de itens. Exemplo:

```dart
List<int> numeros = [1, 2, 3, 4, 5];
print(numeros[0]); // Acesso ao primeiro elemento
numeros.add(6); // Adiciona o número 6 ao final da lista
```

## Set

Set é uma coleção não ordenada de elementos únicos. Não permite elementos duplicados e não garante a ordem de inserção. Exemplo:

```dart
Set<String> frutas = {'maçã', 'banana', 'laranja'};
frutas.add('maçã'); // Não adiciona 'maçã', pois já está na coleção
```

## Map

Map é uma estrutura de dados que armazena pares de chave-valor. As chaves são únicas, e cada chave está associada a um valor específico. Exemplo:

```dart
Map<String, int> estoqueFrutas = {'maçã': 5, 'banana': 10, 'laranja': 15};
print(estoqueFrutas['maçã']); // Acesso ao valor associado à chave 'maçã'
estoqueFrutas['pera'] = 8; // Adiciona um novo par chave-valor ao mapa
```

## Queue

Queue é uma coleção que permite inserir elementos no final e remover do início, seguindo o princípio FIFO (First In, First Out). É necessário importar o pacote dart:collection para utilizar a estrutura Queue. Exemplo:

```dart
import 'dart:collection';

Queue<int> fila = Queue<int>.from([1, 2, 3]);
fila.addLast(4); // Adiciona o número 4 no final da fila
int primeiroElemento = fila.removeFirst(); // Remove e retorna o primeiro elemento da fila
```

## Stack

DART não possui uma estrutura de dados Stack nativa, mas é possível utilizar a lista (List) para criar uma pilha (LIFO - Last In, First Out). Exemplo:

```dart
List<int> pilha = [1, 2, 3];
pilha.add(4); // Adiciona o número 4 no topo da pilha
int elementoTopo = pilha.removeLast(); // Remove e retorna o elemento do topo da pilha
```


Com essas coleções e estruturas de dados, você pode manipular informações de maneira eficiente no DART, adaptando-se às necessidades específicas de sua aplicação.