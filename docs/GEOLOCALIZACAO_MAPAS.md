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

Para obter a localização atual do dispositivo, siga estas etapas:

1. erifique se os serviços de localização estão habilitados no dispositivo.
2. Solicite permissão para acessar a localização do usuário.
3. Use o método `getCurrentPosition` para obter a posição atual do usuário.

Lembre-se de adicionar as permissões necessárias no arquivo `AndroidManifest.xml` (Android) e `Info.plist` (iOS) para acessar a geolocalização.

## 2. Exibindo mapas

Para exibir mapas no aplicativo, primeiro adicione o pacote google_maps_flutter como dependência no arquivo pubspec.yaml:

```yaml
dependencies:
  google_maps_flutter: ^2.1.1
```

Importe o pacote no arquivo em que você deseja exibir o mapa:

```dart
import 'package:google_maps_flutter/google_maps_flutter.dart';
```

Para exibir um mapa, siga estas etapas:

1. Obtenha uma chave de API do Google Maps para sua plataforma (Android e/ou iOS) aqui.
2. Adicione a chave de API ao arquivo `AndroidManifest.xml` (Android) e `Info.plist` (iOS).
3. Crie um widget GoogleMap e defina as propriedades necessárias, como `initialCameraPosition` e `onMapCreated`.

Em resumo, para acessar a geolocalização e exibir mapas no Flutter, você pode usar os pacotes `geolocator` e `google_maps_flutter`. Essas bibliotecas facilitam a integração desses recursos em seu aplicativo, permitindo que você se concentre no desenvolvimento da interface do usuário e da lógica do aplicativo.
