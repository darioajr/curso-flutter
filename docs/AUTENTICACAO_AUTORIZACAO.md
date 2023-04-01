# Autenticação e autorização no Flutter

No Flutter, você pode implementar autenticação e autorização usando bibliotecas de terceiros. Neste exemplo, vamos explorar como fazer isso usando o Firebase Authentication.

## 1. Configurando o Firebase

Primeiro, configure o Firebase em seu projeto Flutter seguindo as etapas disponíveis na [documentação oficial](https://firebase.google.com/docs/flutter/setup).

## 2. Adicionando as dependências

Adicione os pacotes `firebase_auth` e `google_sign_in` como dependências no arquivo `pubspec.yaml`:

```yaml
dependencies:
  firebase_auth: ^3.3.6
  google_sign_in: ^5.2.3
```

Importe os pacotes nos arquivos em que você deseja usar a autenticação e autorização:

```dart
import 'package:firebase_auth/firebase_auth.dart';
import 'package:google_sign_in/google_sign_in.dart';
```

## 3. Autenticando com o Google

Para autenticar o usuário com o Google, siga estas etapas:

1. Crie uma instância da classe `GoogleSignIn`.
2. Chame o método `signIn` para abrir a tela de login do Google.
3. Obtenha as credenciais do usuário (ID token e token de acesso) após o login bem-sucedido.
4. Use as credenciais para autenticar o usuário no Firebase.

Exemplo:

```dart
Future<UserCredential> signInWithGoogle() async {
  final GoogleSignInAccount googleUser = await GoogleSignIn().signIn();
  final GoogleSignInAuthentication googleAuth = await googleUser.authentication;

  final credential = GoogleAuthProvider.credential(
    accessToken: googleAuth.accessToken,
    idToken: googleAuth.idToken,
  );

  return FirebaseAuth.instance.signInWithCredential(credential);
}
```

## 4. Autenticando com e-mail e senha

Para autenticar o usuário com e-mail e senha, siga estas etapas:

1. Crie uma instância da classe `FirebaseAuth`.
2. Use o método `createUserWithEmailAndPassword` para registrar um novo usuário.
3. Use o método `signInWithEmailAndPassword` para autenticar um usuário existente.

Exemplo:

```dart
Future<UserCredential> signUp(String email, String password) async {
  return FirebaseAuth.instance.createUserWithEmailAndPassword(
    email: email,
    password: password,
  );
}

Future<UserCredential> signIn(String email, String password) async {
  return FirebaseAuth.instance.signInWithEmailAndPassword(
    email: email,
    password: password,
  );
}
```

## 5. Acessando os dados do usuário autenticado

Para acessar os dados do usuário autenticado, utilize a propriedade `currentUser` da instância de `FirebaseAuth`.

```dart
User user = FirebaseAuth.instance.currentUser;
```

## 6. Encerrando a sessão do usuário

Para encerrar a sessão do usuário, use o método `signOut`:

```dart
Future<void> signOut() async {
  await FirebaseAuth.instance.signOut();
}
```


Em resumo, para implementar autenticação e autorização no Flutter, você pode usar bibliotecas como `firebase_auth` e `google_sign_in`. Essas bibliotecas facilitam a integração com o Firebase Authentication e outros provedores de autenticação, permitindo que você se concentre no desenvolvimento da interface do usuário e da lógica do aplicativo.
