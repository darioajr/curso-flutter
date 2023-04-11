# Sensores e recursos de hardware no Flutter

No Flutter, você pode acessar sensores e recursos de hardware usando bibliotecas de terceiros. Vamos explorar como fazer isso usando alguns pacotes populares, como `sensors`, `battery`, e `connectivity`.

## 1. Acessando sensores

Para acessar os sensores do dispositivo, primeiro adicione o pacote `sensors` como dependência no arquivo `pubspec.yaml`:

  ```yaml
  dependencies:
    sensors: ^2.0.0
  ```

Importe o pacote no arquivo em que você deseja usar os sensores:

  ```dart
  import 'package:sensors/sensors.dart';
  ```

Execute o comando `flutter pub get` para baixar e instalar o pacote.

O pacote `sensors` fornece acesso aos seguintes sensores:

- Acelerômetro
- Giroscópio
- Orientação do dispositivo

Para usar um sensor, siga estas etapas:

1. Registre-se para receber atualizações do sensor utilizando os streams disponíveis no pacote.
2. Processe os eventos do sensor conforme necessário.

Exemplo:

Crie um novo arquivo chamado `sensors_page.dart` e adicione o seguinte código:

  ```dart
  import 'package:flutter/material.dart';
  import 'package:sensors/sensors.dart';

  class SensorsPage extends StatefulWidget {
    @override
    _SensorsPageState createState() => _SensorsPageState();
  }

  class _SensorsPageState extends State<SensorsPage> {
    AccelerometerEvent _accelerometer;
    GyroscopeEvent _gyroscope;
    UserAccelerometerEvent _userAccelerometer;

    @override
    void initState() {
      super.initState();
      accelerometerEvents.listen((AccelerometerEvent event) {
        setState(() {
          _accelerometer = event;
        });
      });
      gyroscopeEvents.listen((GyroscopeEvent event) {
        setState(() {
          _gyroscope = event;
        });
      });
      userAccelerometerEvents.listen((UserAccelerometerEvent event) {
        setState(() {
          _userAccelerometer = event;
        });
      });
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text('Sensores'),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text('Acelerômetro:'),
              Text(_accelerometer != null
                  ? 'X: ${_accelerometer.x}\nY: ${_accelerometer.y}\nZ: ${_accelerometer.z}'
                  : 'Indisponível'),
              SizedBox(height: 20),
              Text('Giroscópio:'),
              Text(_gyroscope != null
                  ? 'X: ${_gyroscope.x}\nY: ${_gyroscope.y}\nZ: ${_gyroscope.z}'
                  : 'Indisponível'),
              SizedBox(height: 20),
              Text('Orientação do dispositivo:'),
              Text(_userAccelerometer != null
                  ? 'X: ${_userAccelerometer.x}\nY: ${_userAccelerometer.y}\nZ: ${_userAccelerometer.z}'
                  : 'Indisponível'),
            ],
          ),
        ),
      );
    }
  }
  ```

No arquivo `main.dart`, adicione a importação do arquivo `sensors_page.dart` e defina a `SensorsPage` como a tela inicial:

  ```dart
  import 'package:flutter/material.dart';
  import 'sensors_page.dart';

  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Exemplo de Sensores',
        theme: ThemeData(
          primarySwatch: Colors.blue,
        ),
        home: SensorsPage(),
      );
    }
  }
  ```

  Execute o aplicativo. Na tela, você verá as informações do acelerômetro, giroscópio e orientação do dispositivo atualizadas em tempo real.

Esse exemplo demonstra como usar o pacote sensors para acessar os dados do acelerômetro, giroscópio e orientação

## 2. Acessando o nível da bateria

Para acessar o nível da bateria, primeiro adicione o pacote `battery` como dependência no arquivo `pubspec.yaml`:

```yaml
dependencies:
  battery: ^1.0.8
```

Execute `flutter pub get` para baixar e instalar o pacote.

Importe o pacote no arquivo em que você deseja usar o nível da bateria:

```dart
import 'package:battery/battery.dart';
```

Para obter o nível atual da bateria, siga estas etapas:

1. Crie uma instância da classe `Battery`.
2. Use o método `batteryLevel` para obter o nível atual da bateria.

Exemplo:

Crie um novo arquivo chamado `battery_page.dart` e adicione o seguinte código:

  ```dart
  import 'package:flutter/material.dart';
  import 'package:battery/battery.dart';

  class BatteryPage extends StatefulWidget {
    @override
    _BatteryPageState createState() => _BatteryPageState();
  }

  class _BatteryPageState extends State<BatteryPage> {
    Battery _battery = Battery();
    int _batteryLevel;

    @override
    void initState() {
      super.initState();
      _getBatteryLevel();
    }

    Future<void> _getBatteryLevel() async {
      final batteryLevel = await _battery.batteryLevel;
      setState(() {
        _batteryLevel = batteryLevel;
      });
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text('Nível da Bateria'),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text('Nível da bateria:'),
              SizedBox(height: 10),
              Text(_batteryLevel != null
                  ? '$_batteryLevel%'
                  : 'Indisponível'),
              SizedBox(height: 20),
              ElevatedButton(
                onPressed: _getBatteryLevel,
                child: Text('Atualizar Nível da Bateria'),
              ),
            ],
          ),
        ),
      );
    }
  }
  ```

No arquivo `main.dart`, adicione a importação do arquivo `battery_page.dart` e defina a `BatteryPage` como a tela inicial:

  ```dart
  import 'package:flutter/material.dart';
  import 'battery_page.dart';

  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Exemplo de Bateria',
        theme: ThemeData(
          primarySwatch: Colors.blue,
        ),
        home: BatteryPage(),
      );
    }
  }
  ```

Execute o aplicativo. Na tela, você verá o nível atual da bateria e um botão para atualizar o nível da bateria.

Lembre-se de que, para que o aplicativo funcione corretamente, você deve ter concedido as permissões necessárias para acessar a bateria no dispositivo.

## 3. Verificando a conectividade

Para verificar a conectividade do dispositivo, primeiro adicione o pacote `connectivity` como dependência no arquivo `pubspec.yaml`:

```yaml
dependencies:
  connectivity: ^6.0.0
```

Importe o pacote no arquivo em que você deseja verificar a conectividade:

```dart
import 'package:connectivity/connectivity.dart';
```

Execute `flutter pub get` para baixar e instalar o pacote.

Para verificar a conectividade, siga estas etapas:

1. Crie uma instância da classe `Connectivity`.
2. Use o método `checkConnectivity` para verificar o estado atual da conexão.
3. Registre-se para receber atualizações de conectividade utilizando o `onConnectivityChanged` stream.

Exemplo:

Crie um novo arquivo chamado `connectivity_page.dart` e adicione o seguinte código:

  ```dart
  import 'dart:async';
  import 'package:flutter/material.dart';
  import 'package:connectivity/connectivity.dart';

  class ConnectivityPage extends StatefulWidget {
    @override
    _ConnectivityPageState createState() => _ConnectivityPageState();
  }

  class _ConnectivityPageState extends State<ConnectivityPage> {
    Connectivity _connectivity = Connectivity();
    StreamSubscription<ConnectivityResult> _subscription;
    String _connectionStatus;

    @override
    void initState() {
      super.initState();
      _checkConnectivity();
      _subscription = _connectivity.onConnectivityChanged.listen((ConnectivityResult result) {
        setState(() {
          _connectionStatus = _getResultString(result);
        });
      });
    }

    @override
    void dispose() {
      _subscription.cancel();
      super.dispose();
    }

    Future<void> _checkConnectivity() async {
      final result = await _connectivity.checkConnectivity();
      setState(() {
        _connectionStatus = _getResultString(result);
      });
    }

    String _getResultString(ConnectivityResult result) {
      switch (result) {
        case ConnectivityResult.wifi:
          return 'Wi-Fi';
        case ConnectivityResult.mobile:
          return 'Celular';
        case ConnectivityResult.none:
          return 'Sem conexão';
        default:
          return 'Indisponível';
      }
    }

    @override
    Widget build(BuildContext context) {
      return Scaffold(
        appBar: AppBar(
          title: Text('Conectividade'),
        ),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              Text('Conexão atual:'),
              SizedBox(height: 10),
              Text(_connectionStatus ?? 'Indisponível'),
            ],
          ),
        ),
      );
    }
  }
  ```

No arquivo `main.dart`, adicione a importação do arquivo `connectivity_page.dart` e defina a `ConnectivityPage` como a tela inicial:

  ```dart
  import 'package:flutter/material.dart';
  import 'connectivity_page.dart';

  void main() {
    runApp(MyApp());
  }

  class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      return MaterialApp(
        title: 'Exemplo de Conectividade',
        theme: ThemeData(
          primarySwatch: Colors.blue,
        ),
        home: ConnectivityPage(),
      );
    }
  }
  ```

Execute o aplicativo. Na tela, você verá a conexão atual do dispositivo. Quando a conexão mudar, o texto será atualizado automaticamente.

Em resumo, para acessar sensores e recursos de hardware no Flutter, você pode usar pacotes como `sensors`, `battery`, e `connectivity`. Essas bibliotecas facilitam a integração desses recursos em seu aplicativo, permitindo que você se concentre no desenvolvimento da interface do usuário e da lógica do aplicativo.
