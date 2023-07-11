# Persistência de Dados com Hive no Flutter

Hive é uma biblioteca de armazenamento de dados leve e rápida para Flutter, que é ideal para armazenar dados estruturados no dispositivo. Hive é fácil de usar e altamente performático, tornando-se uma ótima opção para armazenamento local no Flutter. Neste capítulo, exploraremos como usar o Hive para armazenar e recuperar dados no Flutter.

## Introdução ao Hive

Hive é uma base de dados NoSQL que armazena dados na forma de pares chave-valor. É extremamente rápido e simples de usar, e também suporta a leitura e gravação de objetos personalizados.

## Instalando o Hive

Para começar a usar o Hive, precisamos adicioná-lo ao nosso projeto Flutter. Adicione as seguintes dependências ao seu arquivo `pubspec.yaml`:

```yaml
dependencies:
  hive: ^latest_version
  hive_flutter: ^latest_version

dev_dependencies:
  hive_generator: ^latest_version
  build_runner: ^latest_version
```

## Configurando o Hive

Antes de podermos usar o Hive, precisamos inicializá-lo. A inicialização do Hive geralmente é feita na função `main` do seu aplicativo.

```dart 
void main() async {
  await Hive.initFlutter();
  runApp(MyApp());
}
```

## Criando um Modelo

Hive pode armazenar qualquer tipo de valor primitivo, List, Map, DateTime, mas também é capaz de armazenar objetos personalizados. Para isso, devemos primeiro definir a classe e suas anotações.

```dart
import 'package:hive/hive.dart';

part 'person.g.dart';

@HiveType(typeId: 0)
class Person extends HiveObject {
  @HiveField(0)
  String name;

  @HiveField(1)
  int age;
}
```

## Gerando o Código Hive

Para armazenar e recuperar os objetos da classe `Person`, precisamos gerar o código de adaptação Hive. Podemos fazer isso usando o pacote `build_runner`:

```bash
flutter packages pub run build_runner build
```

## Abrindo uma Box

Para armazenar e recuperar dados, precisamos abrir uma `box`. Uma  `box` no Hive é como uma tabela em um banco de dados SQL.

```dart
void main() async {
  await Hive.initFlutter();
  Hive.registerAdapter(PersonAdapter());
  final box = await Hive.openBox<Person>('persons');
  runApp(MyApp());
}
```

## Armazenando e Recuperando Dados

Agora que temos uma `box`, podemos armazenar e recuperar dados dela.

```dart
// Armazenando dados
final person = Person()
  ..name = 'John'
  ..age = 30;

await box.put('mykey', person);

// Recuperando dados
final storedPerson = box.get('mykey');
```

## Limpando

Para fechar todas as boxes e deletar os arquivos da box do dispositivo, você pode usar Hive.`deleteFromDisk`().

```dart
await Hive.deleteFromDisk();
```

## Conclusão

Neste capítulo, exploramos como usar a biblioteca Hive para persistência de dados no Flutter. Hive é uma biblioteca de armazenamento leve e rápida, ideal para armazenar dados estruturados no dispositivo. Através de exemplos, mostramos como configurar, criar um modelo, abrir uma 'box', armazenar e recuperar dados usando o Hive. No próximo capítulo, exploraremos o gerenciamento de estado com o Provider.