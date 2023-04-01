# Testes unitários e de widget no Flutter

No Flutter, você pode escrever testes unitários e de widget para garantir a qualidade e a confiabilidade do código do seu aplicativo. Neste guia, vamos explorar como fazer isso.

## 1. Adicionando as dependências

Primeiro, adicione os pacotes `flutter_test` e `mockito` como dependências de desenvolvimento no arquivo `pubspec.yaml`:

```yaml
dev_dependencies:
  flutter_test:
    sdk: flutter
  mockito: ^5.0.0
```

## 2. Testes unitários

Testes unitários são usados para verificar a corretude das funções e classes individuais. No Flutter, você pode escrever testes unitários usando a biblioteca `test`.

### 2.1. Escrevendo um teste unitário

Para escrever um teste unitário, siga estas etapas:

1. Crie um arquivo de teste na pasta `test` com o sufixo `_test.dart`.
2. Importe a biblioteca `test` e o código a ser testado.
3. Use a função `test` para criar um caso de teste.
4. Use as funções `expect` e `group` para organizar e verificar os resultados dos testes.

Exemplo:

```dart
// test/calculadora_test.dart

import 'package:test/test.dart';
import 'package:meu_app/calculadora.dart';

void main() {
  group('Calculadora:', () {
    test('Soma corretamente', () {
      final calculadora = Calculadora();
      expect(calculadora.somar(2, 3), 5);
    });

    test('Subtrai corretamente', () {
      final calculadora = Calculadora();
      expect(calculadora.subtrair(5, 3), 2);
    });
  });
}
```

## 2.2. Executando testes unitários

Para executar os testes unitários, use o comando:

```bash
flutter test
```

## 3. Testes de widget

Testes de widget são usados para verificar a corretude da interface do usuário e das interações entre widgets. No Flutter, você pode escrever testes de widget usando a biblioteca `flutter_test`.

### 3.1. Escrevendo um teste de widget

Para escrever um teste de widget, siga estas etapas:

1. Crie um arquivo de teste na pasta test com o sufixo `_test.dart`.
2. Importe a biblioteca `flutter_test` e o código a ser testado.
3. Use a função `testWidgets` para criar um caso de teste de widget.
4. Use as funções `pumpWidget`, `tap`, `drag`, e `pump` para interagir com os widgets e atualizar a árvore de widgets.

Exemplo:

```dart
// test/meu_widget_test.dart

import 'package:flutter_test/flutter_test.dart';
import 'package:meu_app/main.dart';

void main() {
  testWidgets('MeuWidget exibe o texto correto', (WidgetTester tester) async {
    await tester.pumpWidget(MeuApp());

    expect(find.text('Olá, mundo!'), findsOneWidget);

    await tester.tap(find.byType(ElevatedButton));
    await tester.pump();

    expect(find.text('Você pressionou o botão!'), findsOneWidget);
  });
}
```

### 3.2. Executando testes de widget

Para executar os testes de widget, use o comando:

```bash
flutter test
```

## 4. Mocking e stubbing com o pacote Mockito

O pacote `mockito` permite criar objetos simulados (mocks) e substituir o comportamento de métodos (stubbing) para isolar componentes durante os testes.

### 4.1. Criando um objeto simulado

Para criar um objeto simulado, siga estas etapas:

1. Crie uma classe que estenda a classe `Mock` e implemente a interface desejada.
2. Use a anotação `@GenerateMocks` para gerar a implementação do objeto simulado.

Exemplo:

```dart
// test/mocks/mock_servico.dart

import 'package:mockito/annotations.dart';
import 'package:meu_app/servico.dart';

@GenerateMocks([Servico])
class MockServico extends Mock implements Servico {}
```

### 4.2. Usando objetos simulados e stubbing

Para usar objetos simulados e substituir o comportamento de métodos, siga estas etapas:

1. Importe o arquivo de mock e a biblioteca `mockito`.
2. Crie uma instância do objeto simulado.
3. Use a função `when` para especificar o comportamento dos métodos simulados.
4. Use a função `verify` para verificar se um método foi chamado.

Exemplo:

```dart
// test/servico_test.dart

import 'package:test/test.dart';
import 'package:mockito/mockito.dart';
import 'package:meu_app/servico.dart';
import 'mocks/mock_servico.dart';

void main() {
  group('Servico:', () {
    test('Chama o método fetchDados corretamente', () async {
      final mockServico = MockServico();
      when(mockServico.fetchDados()).thenAnswer((_) async => 'Dados obtidos');

      final servico = Servico();
      final resultado = await servico.fetchDados();

      expect(resultado, 'Dados obtidos');
      verify(mockServico.fetchDados()).called(1);
    });
  });
}
```


Em resumo, no Flutter, você pode escrever testes unitários e de widget para verificar a corretude das funções, classes e interfaces do usuário do seu aplicativo. Além disso, você pode usar bibliotecas como `mockito` para criar objetos simulados e isolar componentes durante os testes.