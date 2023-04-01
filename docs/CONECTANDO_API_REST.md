# Conectando-se a uma API REST no Flutter

No Flutter, você pode se conectar a uma API REST usando bibliotecas de terceiros como `http` e `dio`. Neste exemplo, vamos explorar como fazer isso usando o pacote `http`.

## 1. Adicionando a dependência

Primeiro, adicione o pacote `http` como dependência no arquivo `pubspec.yaml`:

```yaml
dependencies:
  http: ^0.13.3
```

Importe o pacote no arquivo em que você deseja se conectar à API REST:

```dart
import 'package:http/http.dart' as http;
```

## 2. Realizando uma requisição GET

Para realizar uma requisição GET, siga estas etapas:

1. Utilize o método `get` do pacote `http` e passe a URL da API REST como parâmetro.
2. Verifique o código de status da resposta.
3. Decodifique o JSON da resposta e processe os dados conforme necessário.

Exemplo:

```dart
Future<void> fetchPosts() async {
  final response = await http.get('https://jsonplaceholder.typicode.com/posts');

  if (response.statusCode == 200) {
    // Processar os dados
  } else {
    // Tratar o erro
  }
}
```

## 3. Realizando uma requisição POST

Para realizar uma requisição POST, siga estas etapas:

1. Utilize o método `post` do pacote `http` e passe a URL da API REST como parâmetro.
2. Passe os dados a serem enviados no corpo da requisição usando o parâmetro `body`.
3. Verifique o código de status da resposta.
4. Decodifique o JSON da resposta e processe os dados conforme necessário.

Exemplo:

```dart
Future<void> createPost(Map<String, dynamic> data) async {
  final response = await http.post(
    'https://jsonplaceholder.typicode.com/posts',
    body: data,
  );

  if (response.statusCode == 201) {
    // Processar os dados
  } else {
    // Tratar o erro
  }
}
```


Em resumo, para se conectar a uma API REST no Flutter, você pode usar o pacote `http`. Este pacote facilita a realização de requisições HTTP e o processamento das respostas, permitindo que você se concentre no desenvolvimento da interface do usuário e da lógica do aplicativo.