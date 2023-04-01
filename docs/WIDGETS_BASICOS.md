# Widgets básicos do Flutter

O Flutter utiliza widgets para construir a interface do usuário. Os widgets são elementos básicos da interface, como botões, textos e imagens. Existem vários widgets disponíveis no Flutter que facilitam a criação de interfaces atraentes e funcionais. Aqui estão alguns dos widgets básicos do Flutter:

## 1. MaterialApp

O `MaterialApp` é um widget que encapsula várias funcionalidades do Material Design. É geralmente usado como o widget raiz do aplicativo e pode configurar temas, rotas e outros recursos do aplicativo.

```dart
MaterialApp(
  home: Scaffold(),
);
```

## 2. Scaffold

O Scaffold é um widget que fornece uma estrutura básica para a tela do aplicativo. Ele permite adicionar facilmente elementos como AppBar, FloatingActionButton e Drawer.

```dart
Scaffold(
  appBar: AppBar(),
  body: Center(),
  floatingActionButton: FloatingActionButton(),
);
```

## 3. AppBar

O AppBar é um widget que representa uma barra de aplicativo superior com um título e (opcionalmente) botões de ação e um menu suspenso.

```dart
AppBar(
  title: Text('Meu aplicativo'),
  actions: [
    IconButton(icon: Icon(Icons.search), onPressed: () {}),
  ],
);
```

## 4. Text

O widget Text exibe uma string de texto com estilo opcional.

```dart
Text(
  'Olá, Flutter!',
  style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
);
```

## 5. Center

O widget Center centraliza seu widget filho na tela.

```dart
Center(
  child: Text('Olá, Flutter!'),
);
```

## 6. Column e Row

Os widgets Column e Row são usados para organizar seus widgets filhos vertical e horizontalmente, respectivamente.

```dart
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Text('Linha 1'),
    Text('Linha 2'),
    Text('Linha 3'),
  ],
);

Row(
  mainAxisAlignment: MainAxisAlignment.spaceBetween,
  children: [
    Text('Coluna 1'),
    Text('Coluna 2'),
    Text('Coluna 3'),
  ],
);
```

## 7. Container

O widget Container permite personalizar o layout e o estilo de seus widgets filhos. Você pode ajustar a largura, altura, cor de fundo, margem, preenchimento e muito mais.

```dart
Container(
  width: 100,
  height: 100,
  margin: EdgeInsets.all(8),
  padding: EdgeInsets.all(8),
  color: Colors.blue,
  child: Text('Contêiner'),
);
```


```dart
Center(
  child: Text('Olá, Flutter!'),
);
```

## 8. Image

O widget Image exibe uma imagem de uma fonte local ou remota.

```dart
Image.network('https://example.com/image.jpg');
Image.asset('assets/images/image.jpg');
```

## 9. FloatingActionButton

O FloatingActionButton é um botão circular com um ícone que geralmente é usado para executar a ação principal da tela.

```dart
FloatingActionButton(
  child: Icon(Icons.add),
  onPressed: () {},
);
```


Estes são apenas alguns dos muitos widgets disponíveis no Flutter. Combinando e personalizando esses widgets básicos, você pode criar interfaces de usuário ricas e atraentes para seus aplicativos.