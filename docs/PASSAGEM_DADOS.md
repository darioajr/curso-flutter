# Passagem de dados entre telas no Flutter

A passagem de dados entre telas é um aspecto importante na construção de aplicativos móveis. No Flutter, você pode passar dados entre telas através do construtor do widget da tela de destino.

## 1. Passando dados para uma nova tela

Ao navegar para uma nova tela, você pode passar dados para essa tela como argumentos no construtor do widget da tela de destino. Por exemplo:

```dart
class SecondScreen extends StatelessWidget {
  final String data;

  SecondScreen({required this.data});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Segunda Tela')),
      body: Center(child: Text('Dados recebidos: $data')),
    );
  }
}

// Navegando para a segunda tela e passando dados
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen(data: 'Olá, Flutter!')),
);
```

Neste exemplo, a segunda tela aceita um argumento `data` no construtor. Ao navegar para a segunda tela, o argumento é passado como parte do construtor do widget `SecondScreen`.


## 2. Recebendo dados de uma tela anterior

Você também pode receber dados de volta de uma tela quando ela é fechada. Para fazer isso, você pode usar o método Navigator.pop com um valor de retorno na tela de destino e, em seguida, esperar pelo valor de retorno na tela inicial.

```dart
// Segunda tela
FloatingActionButton(
  onPressed: () {
    Navigator.pop(context, 'Dados retornados da segunda tela');
  },
  child: Icon(Icons.arrow_back),
);

// Tela inicial
Future<void> _navigateToSecondScreen() async {
  final result = await Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => SecondScreen(data: 'Olá, Flutter!')),
  );
  print('Resultado da segunda tela: $result');
}
```

Neste exemplo, a segunda tela retorna um valor quando o botão flutuante é pressionado. Na tela inicial, a função `_navigateToSecondScreen` aguarda o valor retornado pela segunda tela.

A passagem de dados entre telas é uma prática comum ao desenvolver aplicativos Flutter e facilita a comunicação entre diferentes partes do seu aplicativo.
