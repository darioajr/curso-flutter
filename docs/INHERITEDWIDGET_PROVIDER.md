# InheritedWidget e Provider no Flutter

O gerenciamento de estado é uma parte essencial do desenvolvimento de aplicativos no Flutter. `InheritedWidget` e `Provider` são duas abordagens populares para gerenciar o estado do aplicativo.

## 1. InheritedWidget

O `InheritedWidget` é um widget especial que permite propagar informações aos widgets descendentes na árvore de widgets. Ele armazena dados que podem ser acessados por widgets filhos sem a necessidade de passá-los manualmente por meio do construtor.

Exemplo de um `InheritedWidget`:

```dart
class MyInheritedData extends InheritedWidget {
  final int counter;

  MyInheritedData({required Widget child, required this.counter}) : super(child: child);

  @override
  bool updateShouldNotify(MyInheritedData oldWidget) {
    return counter != oldWidget.counter;
  }

  static MyInheritedData of(BuildContext context) {
    return context.dependOnInheritedWidgetOfExactType<MyInheritedData>()!;
  }
}
```

Para acessar os dados armazenados em `MyInheritedData` em um widget filho, você pode usar o método `of`:

```dart
MyInheritedData.of(context).counter;
```

## 2. Provider

Embora o `InheritedWidget` seja útil, ele pode ser verboso e difícil de gerenciar em aplicativos maiores. O pacote `Provider` simplifica e aprimora o uso de `InheritedWidget`, oferecendo uma abordagem mais escalável e flexível para gerenciar o estado do aplicativo.

Para usar o `Provider`, adicione-o como dependência no arquivo `pubspec.yaml`:

```yaml
dependencies:
  provider: ^6.0.1
```

Em seguida, crie uma classe que estende `ChangeNotifier` para armazenar e gerenciar seu estado:

```dart
class CounterProvider extends ChangeNotifier {
  int _count = 0;

  int get count => _count;

  void incrementCounter() {
    _count++;
    notifyListeners();
  }
}
```

Agora você pode fornecer seu `CounterProvider` para a árvore de widgets usando o widget `Provider`:

```dart
Provider<CounterProvider>(
  create: (context) => CounterProvider(),
  child: MaterialApp(home: HomeScreen()),
);
```

Para acessar e manipular os dados do `CounterProvider` em um widget filho, use o método `Provider.of`:

```dart
int counter = Provider.of<CounterProvider>(context, listen: false).count;
```

Em resumo, `InheritedWidget` e `Provider` são duas abordagens para gerenciar o estado do aplicativo no Flutter. O `InheritedWidget` permite propagar dados aos widgets descendentes, enquanto o `Provider` simplifica e aprimora o uso de `InheritedWidget`, tornando-o mais escalável e flexível.
