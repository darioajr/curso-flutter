# Estrutura de um aplicativo Flutter

Um aplicativo Flutter possui uma estrutura de diretórios e arquivos padrão que ajuda a organizar o código e os recursos. Aqui está uma visão geral dos diretórios e arquivos mais importantes em um projeto Flutter.

nome_do_projeto/
├─ .dart_tool/
├─ .idea/
├─ android/
├─ ios/
├─ lib/
│ ├─ main.dart
├─ test/
│ ├─ widget_test.dart
├─ web/
├─ .gitignore
├─ .metadata
├─ .packages
├─ .flutter-plugins
├─ .flutter-plugins-dependencies
├─ .pubspec.lock
└─ pubspec.yaml


## Descrição dos diretórios e arquivos

- **`.dart_tool/`**: Diretório gerado automaticamente pelo Dart e Flutter, contendo informações de configuração e arquivos temporários.

- **`.idea/`**: Diretório gerado automaticamente pelo IntelliJ IDEA, contendo arquivos de configuração específicos do editor.

- **`android/`**: Diretório que contém o código específico da plataforma Android e arquivos de configuração do projeto.

- **`ios/`**: Diretório que contém o código específico da plataforma iOS e arquivos de configuração do projeto.

- **`lib/`**: Diretório que contém o código-fonte Dart do aplicativo. O arquivo `main.dart` é o ponto de entrada do aplicativo, onde a lógica principal e a interface do usuário são definidas.

- **`test/`**: Diretório que contém arquivos de teste para o aplicativo.

- **`web/`**: Diretório que contém o código específico da plataforma Web e arquivos de configuração do projeto (gerado apenas ao habilitar o suporte à web no Flutter).

- **`.gitignore`**: Arquivo que define quais arquivos e diretórios devem ser ignorados pelo sistema de controle de versão Git.

- **`.metadata`**: Arquivo gerado automaticamente pelo Flutter que armazena informações sobre o projeto, como a versão do Flutter SDK.

- **`.packages`**: Arquivo gerado automaticamente pelo Flutter e Dart que lista todos os pacotes e suas versões usadas no projeto.

- **`.flutter-plugins`**: Arquivo gerado automaticamente pelo Flutter que lista todos os plugins e suas localizações usados no projeto.

- **`.flutter-plugins-dependencies`**: Arquivo gerado automaticamente pelo Flutter que armazena informações sobre as dependências dos plugins usados no projeto.

- **`.pubspec.lock`**: Arquivo gerado automaticamente pelo Flutter e Dart que armazena informações detalhadas sobre as versões e dependências dos pacotes.

- **`pubspec.yaml`**: Arquivo de configuração do projeto que lista as dependências e recursos do aplicativo, como pacotes, imagens e fontes.

Essa estrutura de diretórios e arquivos permite organizar e gerenciar de maneira eficiente os recursos e o código-fonte do aplicativo Flutter.

