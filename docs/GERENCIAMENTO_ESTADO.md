# Gerenciamento de Estado no Flutter

O gerenciamento de estado é um conceito importante na construção de aplicativos. Refere-se à forma como você organiza, gerencia e atualiza os dados do aplicativo ao longo do tempo e como você lida com as mudanças na interface do usuário conforme os dados são atualizados.

No Flutter, os widgets são imutáveis e a interface do usuário é construída com base no estado atual do aplicativo. Portanto, gerenciar o estado do aplicativo é fundamental para criar aplicativos Flutter eficientes e escaláveis.

## 1. Por que o gerenciamento de estado é importante?

- Garante que a interface do usuário seja consistente e reflita o estado atual do aplicativo.
- Facilita a compreensão e a manutenção do código.
- Ajuda a evitar bugs e comportamentos inesperados.

## 2. Técnicas de gerenciamento de estado no Flutter

Há várias abordagens para gerenciar o estado no Flutter, e a escolha depende das necessidades e complexidade do seu aplicativo. Algumas técnicas comuns incluem:

### 2.1. StatefulWidget

Um `StatefulWidget` é um widget que pode ser atualizado ao longo do tempo. Ele possui um objeto de estado (`State`) separado que contém os dados mutáveis do widget. O `StatefulWidget` é adequado para gerenciar estados locais menores.

```dart
class Counter extends StatefulWidget {
  @override
  _CounterState createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _count = 0;

  void _incrementCounter() {
    setState(() {
      _count = _count + 1;
    });
  }

  // ...
}
```

## 2.2. InheritedWidget e Provider

O InheritedWidget é um widget que permite propagar dados para widgets descendentes na árvore de widgets. O `Provider` é um pacote que simplifica o uso de `InheritedWidget` e oferece uma abordagem mais flexível e escalável para o gerenciamento de estado.

```dart
class CounterProvider extends ChangeNotifier {
  int _count = 0;

  int get count => _count;

  void incrementCounter() {
    _count++;
    notifyListeners();
  }
}

// ...

Provider<CounterProvider>(
  create: (context) => CounterProvider(),
  child: MaterialApp(home: HomeScreen()),
);
```

## 2.3. Bloc

O Bloc (Business Logic Component) é um padrão de gerenciamento de estado que separa a lógica de negócios da apresentação. Ele se baseia nos princípios do Flux e do Redux e usa streams e eventos para gerenciar o estado do aplicativo.

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

O gerenciamento de estado é essencial para criar aplicativos Flutter eficientes e escaláveis. A escolha da técnica de gerenciamento de estado depende das necessidades específicas do seu aplicativo.
