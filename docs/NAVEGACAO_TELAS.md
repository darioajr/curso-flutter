# Navegação entre telas no Flutter

A navegação entre telas é um aspecto essencial dos aplicativos móveis. O Flutter oferece uma abordagem simples e eficiente para lidar com a navegação entre telas usando o `Navigator` e o conceito de "rotas".

## 1. Navigator e rotas

O `Navigator` é um widget que gerencia uma pilha de rotas (ou seja, telas). Você pode usar o `Navigator.push` e `Navigator.pop` para adicionar ou remover rotas dessa pilha.

```dart
// Navegando para uma nova tela
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen()),
);

// Retornando à tela anterior
Navigator.pop(context);
```

## 2. Roteamento nomeado

O Flutter também suporta o roteamento nomeado, o que facilita a organização e a manutenção das rotas do seu aplicativo. Para usar o roteamento nomeado, defina um mapa de rotas no widget `MaterialApp` ou `CupertinoApp`.

```dart
MaterialApp(
  initialRoute: '/',
  routes: {
    '/': (context) => FirstScreen(),
    '/second': (context) => SecondScreen(),
  },
);
```

Agora, você pode navegar para a segunda tela usando o nome da rota:

```dart
Navigator.pushNamed(context, '/second');
```

## 3. Passando dados entre telas

Frequentemente, é necessário passar dados entre telas. Isso pode ser feito facilmente através do construtor da tela de destino.

```dart
class SecondScreen extends StatelessWidget {
  final String data;

  SecondScreen({required this.data});

  // ...
}

// Navegando para a segunda tela e passando dados
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen(data: 'Olá, Flutter!')),
);
```

A navegação entre telas é uma parte fundamental dos aplicativos Flutter. Com o `Navigator` e as rotas, você pode criar aplicativos com uma experiência de usuário intuitiva e fácil de usar.

