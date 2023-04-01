# StatefulWidget e StatelessWidget no Flutter

No Flutter, os widgets são os elementos básicos para a construção da interface do usuário. Eles podem ser divididos em dois tipos principais: `StatefulWidget` e `StatelessWidget`.

## 1. StatelessWidget

Um `StatelessWidget` é um widget que descreve uma parte da interface do usuário que não pode ser alterada. Em outras palavras, é imutável. Quando você deseja exibir informações que não mudam ao longo do tempo ou que são independentes do estado do aplicativo, o `StatelessWidget` é a escolha adequada.

Exemplo de um `StatelessWidget`:

```dart
class MyTextWidget extends StatelessWidget {
  final String text;

  MyTextWidget({required this.text});

  @override
  Widget build(BuildContext context) {
    return Text(text);
  }
}
```

Neste exemplo, o `MyTextWidget` é um widget sem estado que exibe um texto passado como argumento. A interface do usuário gerada por este widget não muda ao longo do tempo.

## 2. StatefulWidget

Um `StatefulWidget`, por outro lado, é um widget que pode mudar ao longo do tempo. Ele possui um objeto de estado (`State`) separado que contém os dados mutáveis do widget. Quando você deseja criar uma interface do usuário que responda às interações do usuário ou a mudanças no estado do aplicativo, o `StatefulWidget` é a escolha adequada.

Exemplo de um `StatefulWidget`:

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

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Você clicou $_count vezes'),
        ElevatedButton(
          onPressed: _incrementCounter,
          child: Text('Clique aqui'),
        ),
      ],
    );
  }
}
```

Neste exemplo, o `Counter` é um widget com estado que exibe e atualiza um contador. A interface do usuário gerada por este widget muda com base na interação do usuário.

Em resumo, `StatefulWidget` e `StatelessWidget` são os dois tipos principais de widgets no Flutter. O `StatelessWidget` é usado para partes imutáveis da interface do usuário, enquanto o `StatefulWidget` é usado para partes mutáveis que respondem às interações do usuário ou mudanças no estado do aplicativo.