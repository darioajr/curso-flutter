# Configurando o ambiente de desenvolvimento Flutter

Configurar o ambiente de desenvolvimento Flutter é um passo essencial para começar a criar aplicativos com o framework. Aqui estão as etapas para configurar o ambiente de desenvolvimento Flutter em seu computador.

## 1. Instalar o Flutter SDK

### 1.1 Baixe o Flutter SDK

Visite a página oficial de instalação do Flutter em [https://flutter.dev/docs/get-started/install](https://flutter.dev/docs/get-started/install) e escolha o sistema operacional apropriado (Windows, macOS, Linux) para baixar o SDK.

### 1.2 Extraia o arquivo

Após o download, extraia o arquivo ZIP em um local adequado no seu computador (por exemplo, `C:\src\flutter` no Windows ou `/usr/local/flutter` no macOS/Linux).

### 1.3 Atualize a variável de ambiente PATH

Adicione o caminho do diretório `bin` do Flutter SDK à variável de ambiente PATH do seu sistema:

- **Windows:** Adicione o caminho do Flutter `bin` (por exemplo, `C:\src\flutter\bin`) às variáveis de ambiente do sistema.
- **macOS e Linux:** Adicione a seguinte linha ao arquivo de perfil do shell (por exemplo, `.bashrc`, `.bash_profile`, `.zshrc`):

export PATH="$PATH:[CAMINHO_DO_FLUTTER_BIN]"

Substitua `[CAMINHO_DO_FLUTTER_BIN]` pelo caminho do diretório `bin` do Flutter SDK no seu sistema.

## 2. Instalar o Android Studio

Baixe e instale o [Android Studio](https://developer.android.com/studio) para desenvolver aplicativos Flutter para Android. Durante a instalação, selecione a opção para instalar o Android SDK e o AVD Manager.

## 3. Configurar o emulador Android

Abra o Android Studio e siga estas etapas para criar um emulador Android:

1. Clique em "Configure" na tela inicial e selecione "AVD Manager".
2. Clique em "Create Virtual Device" e escolha um dispositivo da lista.
3. Selecione uma imagem do sistema (recomendamos usar uma imagem do sistema x86).
4. Confirme as configurações e clique em "Finish" para criar o emulador.

## 4. Instalar o Xcode (macOS)

Para desenvolver aplicativos Flutter para iOS, instale o [Xcode](https://developer.apple.com/xcode/) através da App Store no macOS.

## 5. Instalar extensões do VS Code ou IntelliJ (opcional)

Se você planeja usar o Visual Studio Code ou o IntelliJ IDEA como seu editor de código, instale as extensões do Flutter e do Dart para obter suporte aprimorado para codificação, depuração e refatoração.

- **Visual Studio Code:** Instale as extensões "Flutter" e "Dart" na Visual Studio Code Marketplace.
- **IntelliJ IDEA:** Instale os plugins "Flutter" e "Dart" no IntelliJ IDEA Marketplace.

## 6. Verificar a instalação

Execute o comando `flutter doctor` no terminal ou prompt de comando para verificar se o ambiente de desenvolvimento Flutter foi configurado corretamente. O comando `flutter doctor` verificará a instalação do Flutter SDK, Android Studio, Xcode (macOS) e outras dependências, e informará se algo precisa ser corrigido ou atualizado.


Se o `flutter doctor` não relatar problemas, seu ambiente de desenvolvimento Flutter está configurado e pronto para uso.

## 7. Criar e executar um aplicativo Flutter

Para criar um novo aplicativo Flutter, siga estas etapas:

1. Abra o terminal ou prompt de comando e navegue até o diretório onde você deseja criar o projeto.
2. Execute o comando `flutter create nome_do_projeto`, substituindo `nome_do_projeto` pelo nome que você deseja dar ao seu aplicativo.
3. Navegue até o diretório do projeto recém-criado e execute o comando `flutter run` para iniciar o aplicativo no emulador ou dispositivo conectado.

```bash
cd nome_do_projeto
```

```bash
flutter run
```

Seu aplicativo Flutter agora deve ser executado no emulador ou dispositivo selecionado.

Com seu ambiente de desenvolvimento Flutter configurado, você pode começar a criar aplicativos incríveis e de alto desempenho para Android, iOS e outras plataformas. Aproveite a rica coleção de widgets e recursos avançados do Flutter para criar aplicativos atraentes e envolventes.

