# Bloc e MobX no Flutter

Bloc e MobX são duas bibliotecas populares para gerenciar o estado do aplicativo no Flutter. Ambas oferecem abordagens diferentes para lidar com o estado, e a escolha entre elas dependerá das necessidades específicas do seu aplicativo.

## 1. Bloc (Business Logic Component)

O Bloc é um padrão de gerenciamento de estado que separa a lógica de negócios da apresentação. Ele é baseado nos princípios do Flux e do Redux e utiliza streams e eventos para gerenciar o estado do aplicativo.

Para começar a usar o Bloc, adicione as dependências necessárias no arquivo `pubspec.yaml`:

```yaml
dependencies:
  flutter_bloc: ^8.0.1
```

Crie uma classe para representar os eventos que podem ocorrer:

```dart
abstract class CounterEvent {}

class IncrementCounter extends CounterEvent {}
```

Em seguida, crie um `Bloc` que irá processar esses eventos e atualizar o estado:

```dart
class CounterBloc extends Bloc<CounterEvent, int> {
  CounterBloc() : super(0);

  @override
  Stream<int> mapEventToState(CounterEvent event) async* {
    if (event is IncrementCounter) {
      yield state + 1;
    }
  }
}
```

Para utilizar o `Bloc` no aplicativo, envolva sua árvore de widgets com o `BlocProvider`:

```dart
BlocProvider<CounterBloc>(
  create: (context) => CounterBloc(),
  child: MaterialApp(home: HomeScreen()),
);
```

## 2. MobX

O MobX é uma biblioteca de gerenciamento de estado reativa que torna fácil conectar a interface do usuário às mudanças de estado. Ele utiliza observáveis, ações e reações para atualizar automaticamente a interface do usuário quando o estado é alterado.

Para começar a usar o MobX, adicione as dependências necessárias no arquivo `pubspec.yaml`:

```yaml
dependencies:
  flutter_mobx: ^2.0.1
  mobx: ^2.0.6

dev_dependencies:
  build_runner: ^2.1.5
  mobx_codegen: ^2.0.3
```

Crie uma classe para armazenar e gerenciar seu estado com a ajuda de anotações MobX:

```dart
import 'package:mobx/mobx.dart';

part 'counter_store.g.dart';

class CounterStore = _CounterStoreBase with _$CounterStore;

abstract class _CounterStoreBase with Store {
  @observable
  int count = 0;

  @action
  void incrementCounter() {
    count++;
  }
}
```

Em seguida, execute o comando `flutter packages pub run build_runner build` para gerar o código necessário.

Para utilizar o `CounterStore` no aplicativo, envolva sua árvore de widgets com o `Provider`:

```dart
Provider<CounterStore>(
  create: (context) => CounterStore(),
  child: MaterialApp(home: HomeScreen()),
);
```

Em resumo, Bloc e MobX são duas bibliotecas populares para gerenciar o estado do aplicativo no Flutter. O Bloc utiliza streams e eventos para gerenciar o estado, enquanto o MobX emprega observáveis, ações e reações para atualizar a interface do usuário de maneira reativa. A escolha entre Bloc e MobX dependerá das necessidades específicas do seu aplicativo.