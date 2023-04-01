# Testes de integração no Flutter

Os testes de integração no Flutter servem para verificar se diferentes partes do aplicativo funcionam corretamente em conjunto. Eles são úteis para testar a interação entre widgets, serviços e outras camadas do aplicativo.

## 1. Adicionando as dependências

Primeiro, adicione o pacote `integration_test` como dependência de desenvolvimento no arquivo `pubspec.yaml`:

```yaml
dev_dependencies:
  integration_test:
    sdk: flutter
```

# 2. Criando um teste de integração

Para criar um teste de integração, siga estas etapas:

1. Crie uma pasta chamada `integration_test` na raiz do seu projeto.
2. Dentro desta pasta, crie um arquivo de teste com o sufixo `_test.dart`.
3. Importe a biblioteca `integration_test` e o código a ser testado.
4. Use a função `testWidgets` para criar casos de teste de integração.
5. Use as funções `pumpWidget`, `tap`, `drag`, e `pump` para interagir com os widgets e atualizar a árvore de widgets.

Exemplo:


```dart
// integration_test/app_test.dart

import 'package:flutter_test/flutter_test.dart';
import 'package:integration_test/integration_test.dart';
import 'package:meu_app/main.dart';

void main() {
  IntegrationTestWidgetsFlutterBinding.ensureInitialized();

  testWidgets('Teste de integração: navegação e interação', (WidgetTester tester) async {
    await tester.pumpWidget(MeuApp());

    expect(find.text('Olá, mundo!'), findsOneWidget);

    await tester.tap(find.byType(ElevatedButton));
    await tester.pumpAndSettle();

    expect(find.text('Você pressionou o botão!'), findsOneWidget);

    await tester.tap(find.byType(IconButton));
    await tester.pumpAndSettle();

    expect(find.text('Olá, mundo!'), findsOneWidget);
  });
}
```

## 3. Executando testes de integração

Para executar testes de integração no Flutter, siga estas etapas:

1. Conecte um dispositivo ou emulador.
2. Use o comando `flutter drive` para executar os testes de integração:

```bash
flutter drive --target=integration_test/app_test.dart
```


Os testes de integração são executados no dispositivo ou emulador conectado, e os resultados são exibidos no terminal.

Em resumo, os testes de integração no Flutter ajudam a verificar se diferentes partes do aplicativo funcionam corretamente em conjunto. Eles são úteis para testar a interação entre widgets, serviços e outras camadas do aplicativo.
