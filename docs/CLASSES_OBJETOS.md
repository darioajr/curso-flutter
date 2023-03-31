# Classes, objetos e herança no DART

A orientação a objetos é um paradigma de programação amplamente utilizado que facilita a organização, a modularização e a reutilização de código. No DART, você pode criar classes, objetos e usar herança para aproveitar ao máximo esse paradigma. A seguir, são apresentadas informações sobre classes, objetos e herança no DART.

## Classes e objetos

### 1. Declaração de classes

Para declarar uma classe no DART, use a palavra-chave `class` seguida pelo nome da classe. A classe pode conter campos (variáveis), construtores e métodos (funções). Exemplo:

```dart
class Pessoa {
  String nome;
  int idade;

  Pessoa(this.nome, this.idade);

  void falar() {
    print('Olá, meu nome é $nome e eu tenho $idade anos.');
  }
}
```

### 2. Criação de objetos

Para criar um objeto a partir de uma classe, use o operador new (opcional) seguido pelo nome da classe e um construtor. Exemplo:

```dart
Pessoa pessoa1 = Pessoa('João', 30);
Pessoa pessoa2 = new Pessoa('Maria', 28);
```

### 3. Acesso a campos e métodos

Para acessar os campos e métodos de um objeto, use o operador .. Exemplo:

```dart
print(pessoa1.nome); // Acessa o campo 'nome' do objeto 'pessoa1'
pessoa1.falar(); // Chama o método 'falar()' do objeto 'pessoa1'
```

## Herança

A herança permite criar uma nova classe que herda campos e métodos de uma classe existente, facilitando a reutilização e a extensibilidade do código.

### 1. Classe base e classe derivada

A classe base é a classe que fornece campos e métodos para outras classes. A classe derivada é a classe que herda campos e métodos de uma classe base.

Para criar uma classe derivada, use a palavra-chave extends seguida pelo nome da classe base. Exemplo:

```dart
class Funcionario extends Pessoa {
  double salario;

  Funcionario(String nome, int idade, this.salario) : super(nome, idade);

  void receberSalario() {
    print('$nome recebeu o salário de $salario.');
  }
}
```

### 2. Uso de super

A palavra-chave super permite chamar construtores e métodos da classe base dentro da classe derivada. No exemplo acima, o construtor da classe Funcionario chama o construtor da classe Pessoa usando super(nome, idade).

### 3. Sobrescrita de métodos

É possível sobrescrever um método da classe base na classe derivada, alterando sua implementação. Use a palavra-chave @override para indicar que um método está sendo sobrescrito. Exemplo:

```dart
class Gerente extends Funcionario {
  Gerente(String nome, int idade, double salario) : super(nome, idade, salario);

  @override
  void receberSalario() {
    print('$nome recebeu o salário de $salario e uma bonificação.');
  }
}
```


Com classes, objetos e herança, você pode criar estruturas de código organizadas e reutilizáveis no DART, aproveitando os benefícios da orientação a objetos para desenvolver aplica