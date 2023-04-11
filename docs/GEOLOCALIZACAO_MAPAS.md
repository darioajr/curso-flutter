# Geolocalização e mapas no Flutter

No Flutter, você pode acessar a geolocalização e exibir mapas usando bibliotecas de terceiros. Vamos explorar como fazer isso usando os pacotes `geolocator` e `google_maps_flutter`.

## 1. Acessando a geolocalização

Para acessar a geolocalização, primeiro adicione o pacote `geolocator` como dependência no arquivo `pubspec.yaml`:

  ```yaml
  dependencies:
    geolocator: ^7.6.2
  ```

Importe o pacote no arquivo em que você deseja usar a geolocalização:

  ```dart
  import 'package:geolocator/geolocator.dart';
  ```

Execute 
```bash 
flutter pub get
```
para baixar e instalar o pacote.

Para obter a localização atual do dispositivo, siga estas etapas:

1. Verifique se os serviços de localização estão habilitados no dispositivo.
2. Solicite permissão para acessar a localização do usuário.
3. Use o método `getCurrentPosition` para obter a posição atual do usuário.

Lembre-se de adicionar as permissões necessárias no arquivo `AndroidManifest.xml` (Android) e `Info.plist` (iOS) para acessar a geolocalização.

Exemplo:

Crie um novo arquivo chamado `location_page.dart` e adicione o seguinte código:

```dart
import 'package:flutter/material.dart';
import 'package:geolocator/geolocator.dart';

class LocationPage extends StatefulWidget {
  @override
  _LocationPageState createState() => _LocationPageState();
}

class _LocationPageState extends State<LocationPage> {
  Position _position;
  String _locationError;

  Future<void> _getCurrentLocation() async {
    try {
      final currentPosition = await Geolocator.getCurrentPosition(
        desiredAccuracy: LocationAccuracy.high,
      );
      setState(() {
        _position = currentPosition;
        _locationError = null;
      });
    } catch (e) {
      setState(() {
        _locationError = e.toString();
      });
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Localização Atual'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            _position != null
                ? Text(
                    'Latitude: ${_position.latitude}\nLongitude: ${_position.longitude}',
                    textAlign: TextAlign.center,
                  )
                : _locationError != null
                    ? Text(_locationError)
                    : Text('Localização não obtida'),
            SizedBox(height: 20),
            ElevatedButton(
              onPressed: _getCurrentLocation,
              child: Text('Obter Localização Atual'),
            ),
          ],
        ),
      ),
    );
  }
}
```

No arquivo `main.dart`, adicione a importação do arquivo `location_page.dart` e defina a `LocationPage` como a tela inicial:

```dart
import 'package:flutter/material.dart';
import 'location_page.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Exemplo de Localização',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: LocationPage(),
    );
  }
}
```

Execute o aplicativo. Na tela, você verá um botão para obter a localização atual. Quando o botão for pressionado, as coordenadas de latitude e longitude do usuário serão exibidas na tela.

## 2. Exibindo mapas

Para exibir mapas no aplicativo, primeiro adicione o pacote google_maps_flutter como dependência no arquivo pubspec.yaml:

  ```yaml
  dependencies:
    google_maps_flutter: ^2.1.1
  ```

Execute 
```bash
flutter pub get
```
para baixar e instalar o pacote.

Importe o pacote no arquivo em que você deseja exibir o mapa:

  ```dart
  import 'package:google_maps_flutter/google_maps_flutter.dart';
  ```

Para exibir um mapa, siga estas etapas:

1. Obtenha uma chave de API do Google Maps para sua plataforma (Android e/ou iOS) [aqui](COMO_OBTER_CHAVE_GOOGLE_MAPS.md).
2. Adicione a chave de API ao arquivo `AndroidManifest.xml` (Android) e `Info.plist` (iOS).
3. Crie um widget GoogleMap e defina as propriedades necessárias, como `initialCameraPosition` e `onMapCreated`.

Exemplo:

Arquivo `maps_page.dart`

```dart
import 'package:flutter/material.dart';
import 'package:google_maps_flutter/google_maps_flutter.dart';

class MapsPage extends StatefulWidget {
  @override
  _MapsPageState createState() => _MapsPageState();
}

class _MapsPageState extends State<MapsPage> {
  GoogleMapController _controller;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Google Maps')),
      body: GoogleMap(
        onMapCreated: (GoogleMapController controller) {
          _controller = controller;
        },
        initialCameraPosition: CameraPosition(
          target: LatLng(-23.550520, -46.633308), // Coordenadas de São Paulo
          zoom: 11,
        ),
      ),
    );
  }
}
```

Arquivo `main.dart`

```dart
import 'package:flutter/material.dart';
import 'maps_page.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Google Maps Exemplo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: MapsPage(),
    );
  }
}
```

Em resumo, para acessar a geolocalização e exibir mapas no Flutter, você pode usar os pacotes `geolocator` e `google_maps_flutter`. Essas bibliotecas facilitam a integração desses recursos em seu aplicativo, permitindo que você se concentre no desenvolvimento da interface do usuário e da lógica do aplicativo.


## 3. Permissões

Para acessar a geolocalização e mapas no Flutter, você precisa incluir permissões específicas nos arquivos `AndroidManifest.xml` (para Android) e `Info.plist` (para iOS).

### No Android:

Abra o arquivo `AndroidManifest.xml` que está localizado em android/app/src/main.
Adicione a permissão de LOCATION dentro da tag <manifest> e antes da tag <application>, informe também a sua APIKEY do Google:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.my_maps_app">

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

    <application
        android:label="my_maps_app"
        android:icon="@mipmap/ic_launcher">
        <activity
            android:name=".MainActivity"
            android:launchMode="singleTop"
            android:theme="@style/LaunchTheme"
            android:configChanges="orientation|keyboardHidden|keyboard|screenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
            android:hardwareAccelerated="true"
            android:windowSoftInputMode="adjustResize">
            <intent-filter>
                <action android:name="android.intent.action.MAIN"/>
                <category android:name="android.intent.category.LAUNCHER"/>
            </intent-filter>
        </activity>
        <meta-data android:name="com.google.android.geo.API_KEY"
            android:value="YOUR_API_KEY"/>
    </application>
</manifest>
```

### No iOS:

Abra o arquivo `Info.plist` que está localizado em `ios/Runner`.

O arquivo Info.plist ficará assim:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>CFBundleDevelopmentRegion</key>
    <string>en</string>
    <key>CFBundleExecutable</key>
    <string>$(EXECUTABLE_NAME)</string>
    <key>CFBundleIdentifier</key>
    <string>$(PRODUCT_BUNDLE_IDENTIFIER)</string>
    <key>CFBundleInfoDictionaryVersion</key>
    <string>6.0</string>
    <key>CFBundleName</key>
    <string>$(PRODUCT_NAME)</string>
    <key>CFBundlePackageType</key>
    <string>APPL</string>
    <key>CFBundleShortVersionString</key>
    <string>$(FLUTTER_BUILD_NAME)</string>
    <key>CFBundleSignature</key>
    <string>????</string>
    <key>CFBundleVersion</key>
    <string>$(FLUTTER_BUILD_NUMBER)</string>
    <key>LSRequiresIPhoneOS</key>
    <true/>
    <key>UILaunchStoryboardName</key>
    <string>LaunchScreen</string>
    <key>UIMainStoryboardFile</key>
    <string>Main</string>
    <key>UISupportedInterfaceOrientations</key>
    <array>
        <string>UIInterfaceOrientationPortrait</string>
        <string>UIInterfaceOrientationLandscapeLeft</string>
        <string>UIInterfaceOrientationLandscapeRight</string>
    </array>
    <key>UISupportedInterfaceOrientations~ipad</key>
    <array>
        <string>UIInterfaceOrientationPortrait</string>
        <string>UIInterfaceOrientationPortraitUpsideDown</string>
        <string>UIInterfaceOrientationLandscapeLeft</string>
        <string>UIInterfaceOrientationLandscapeRight</string>
    </array>
    <key>UIViewControllerBasedStatusBarAppearance</key>
    <false/>
    <key>NSAppTransportSecurity</key>
    <dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
    </dict>
    <key>NSCameraUsageDescription</key>
    <string>Esta aplicação precisa acessar a câmera para tirar fotos.</string>
    <key>NSLocationWhenInUseUsageDescription</key>
    <string>Esta aplicação precisa acessar sua localização para exibir o mapa.</string>
    <key>NSLocationAlwaysUsageDescription</key>
    <string>Esta aplicação precisa acessar sua localização para exibir o mapa.</string>
    <key>NSPhotoLibraryUsageDescription</key>
    <string>Esta aplicação precisa acessar a galeria de fotos para selecionar imagens.</string>
    <key>io.flutter.embedded_views_preview</key>
    <true/>
    <key>com.google.android.geo.API_KEY</key>
    <string>YOUR_API_KEY</string>
  </dict>
  </plist>
```

Substitua `YOUR_API_KEY` pela chave de API do Google Maps que você obteve anteriormente.

Depois de adicionar as permissões necessárias e instalar os pacotes, sua aplicação Flutter poderá acessar os recursos no Android e no iOS. Lembre-se de que o usuário ainda precisa conceder permissão para o aplicativo acessar recursos quando solicitado.