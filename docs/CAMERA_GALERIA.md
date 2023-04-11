# Câmera e galeria de fotos no Flutter

No Flutter, você pode acessar a câmera e a galeria de fotos do dispositivo usando bibliotecas de terceiros. Vamos explorar como acessar esses recursos usando os pacotes `camera` e `image_picker`.

## 1. Acessando a câmera

Para acessar a câmera, primeiro adicione o pacote `camera` como dependência no arquivo `pubspec.yaml`:

```yaml
dependencies:
  camera: ^0.9.4+5
```

Execute 
```bash 
flutter pub get
```
para baixar e instalar o pacote.

Importe o pacote no arquivo em que você deseja usar a câmera:

```dart
import 'package:camera/camera.dart';
```

Para acessar e inicializar a câmera, siga estas etapas:

1. Liste todas as câmeras disponíveis no dispositivo.
2. Selecione uma câmera da lista.
3. Crie um `CameraController` e inicialize-o com a câmera selecionada.
4. Exiba a visualização da câmera na tela usando o `CameraPreview` widget.

Exemplo:

Crie um novo arquivo chamado `camera_page.dart` e adicione o seguinte código:

```dart
import 'package:camera/camera.dart';
import 'package:flutter/material.dart';

class CameraPage extends StatefulWidget {
  @override
  _CameraPageState createState() => _CameraPageState();
}

class _CameraPageState extends State<CameraPage> {
  List<CameraDescription> cameras;
  CameraController _controller;
  int _selectedCameraIndex;

  @override
  void initState() {
    super.initState();
    _initCameras();
  }

  Future<void> _initCameras() async {
    try {
      cameras = await availableCameras();
      if (cameras.isNotEmpty) {
        setState(() {
          _selectedCameraIndex = 0;
        });
        _initCameraController(cameras[_selectedCameraIndex]);
      }
    } catch (e) {
      print('Erro ao listar câmeras: $e');
    }
  }

  Future<void> _initCameraController(CameraDescription camera) async {
    if (_controller != null) {
      await _controller.dispose();
    }

    _controller = CameraController(camera, ResolutionPreset.high);
    _controller.addListener(() {
      if (mounted) {
        setState(() {});
      }

      if (_controller.value.hasError) {
        print('Erro no controlador de câmera: ${_controller.value.errorDescription}');
      }
    });

    try {
      await _controller.initialize();
    } catch (e) {
      print('Erro ao inicializar controlador de câmera: $e');
    }

    if (mounted) {
      setState(() {});
    }
  }

  @override
  void dispose() {
    _controller?.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Câmera')),
      body: Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        children: <Widget>[
          Expanded(
            child: _controller == null || !_controller.value.isInitialized
                ? Center(child: CircularProgressIndicator())
                : CameraPreview(_controller),
          ),
          _buildCameraList(),
        ],
      ),
    );
  }

  Widget _buildCameraList() {
    if (cameras == null || cameras.isEmpty) {
      return Spacer();
    }

    return Container(
      height: 100,
      child: ListView.builder(
        scrollDirection: Axis.horizontal,
        itemCount: cameras.length,
        itemBuilder: (BuildContext context, int index) {
          return InkWell(
            onTap: () {
              setState(() {
                _selectedCameraIndex = index;
              });
              _initCameraController(cameras[_selectedCameraIndex]);
            },
            child: Container(
              width: 100,
              height: 100,
              child: Center(
                child: Text(
                  'Câmera ${index + 1}',
                  style: TextStyle(
                    color: _selectedCameraIndex == index ? Colors.white : Colors.grey,
                  ),
                ),
              ),
              decoration: BoxDecoration(
                color: _selectedCameraIndex == index ? Colors.blue : Colors.black,
                border: Border.all
                (color: _selectedCameraIndex == index ? Colors.blueAccent : Colors.grey),
              ),
            ),
          );
        },
      ),
    );
  }
}
```

 No arquivo `main.dart`, adicione a importação do arquivo `camera_page.dart` e defina a `CameraPage` como a tela inicial:

```dart
import 'package:flutter/material.dart';
import 'camera_page.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Exemplo de Câmera',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: CameraPage(),
    );
  }
}
```

Execute o aplicativo. A lista de câmeras disponíveis será exibida na parte inferior da tela. Ao selecionar uma câmera, a visualização será atualizada com a câmera selecionada.

Este exemplo cria uma aplicação Flutter que lista todas as câmeras disponíveis no dispositivo e permite ao usuário selecionar uma câmera. Ele cria um `CameraController` e o inicializa com a câmera selecionada, e exibe a visualização da câmera na tela usando o widget `CameraPreview`.


## 2. Acessando a galeria de fotos

Para acessar a galeria de fotos, primeiro adicione o pacote `image_picker` como dependência no arquivo `pubspec.yaml`:

```yaml
dependencies:
  image_picker: ^0.8.4+4
```

Importe o pacote no arquivo em que você deseja usar a galeria de fotos:

```dart
import 'package:image_picker/image_picker.dart';
```

Para acessar a galeria de fotos, siga estas etapas:

1. Crie uma instância do `ImagePicker`.
2. Chame o método `pickImage` ou `pickVideo` para abrir a galeria e permitir que o usuário selecione um arquivo.

Lembre-se de adicionar as permissões necessárias no arquivo `AndroidManifest.xml` (Android) e `Info.plist` (iOS) para acessar a câmera e a galeria de fotos.

Em resumo, para acessar a câmera e a galeria de fotos no Flutter, você pode usar os pacotes `camera` e `image_picker`. Essas bibliotecas facilitam a integração desses recursos em seu aplicativo, permitindo que você se concentre no desenvolvimento da interface do usuário e da lógica do aplicativo.

## 3. Permissões

Para acessar a câmera e a galeria no Flutter, você precisa incluir permissões específicas nos arquivos `AndroidManifest.xml` (para Android) e `Info.plist` (para iOS).

### Android:

Abra o arquivo `AndroidManifest.xml` que está localizado em android/app/src/main.
Adicione a permissão CAMERA dentro da tag <manifest> e antes da tag <application>:

```xml
<uses-permission android:name="android.permission.CAMERA" />
```

Adicione a permissão `READ_EXTERNAL_STORAGE` e `WRITE_EXTERNAL_STORAGE` (para versões do Android abaixo da API 29) dentro da tag <manifest> e antes da tag <application>:

```xml
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

O arquivo `AndroidManifest.xml` ficará assim:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.my_camera_app">
    <uses-permission android:name="android.permission.CAMERA" />
  
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    
    <application
        ...
    </application>
</manifest>
```

### iOS:

Abra o arquivo `Info.plist` que está localizado em `ios/Runner`.

Adicione a chave `NSCameraUsageDescription` com uma descrição do motivo pelo qual sua aplicação precisa acessar a câmera do dispositivo:

```xml
<key>NSCameraUsageDescription</key>
<string>Esta aplicação precisa acessar a câmera para tirar fotos.</string>
```

Adicione a chave `NSPhotoLibraryUsageDescription` com uma descrição do motivo pelo qual sua aplicação precisa acessar a galeria de fotos do dispositivo:

```xml
<key>NSPhotoLibraryUsageDescription</key>
<string>Esta aplicação precisa acessar a galeria de fotos para selecionar imagens.</string>
```

O arquivo Info.plist ficará assim:

```xml
<dict>
    ...
    <key>NSCameraUsageDescription</key>
    <string>Esta aplicação precisa acessar a câmera para tirar fotos.</string>
    <key>NSPhotoLibraryUsageDescription</key>
    <string>Esta aplicação precisa acessar a galeria de fotos para selecionar imagens.</string>
</dict>
```

Depois de adicionar as permissões necessárias e instalar os pacotes camera e image_picker, sua aplicação Flutter poderá acessar a galeria de fotos no Android e no iOS. Lembre-se de que o usuário ainda precisa conceder permissão para o aplicativo acessar a galeria quando solicitado.