# Componentes de interação e entrada de dados no Flutter

O Flutter oferece uma ampla variedade de componentes de interação e entrada de dados para criar aplicativos interativos e fáceis de usar. Aqui estão alguns dos principais componentes:

## 1. TextField

O widget `TextField` permite que os usuários insiram texto em seu aplicativo.

```dart
TextField(
  decoration: InputDecoration(labelText: 'Digite algo'),
  onChanged: (value) {
    print(value);
  },
);
```

## 2. RaisedButton

O widget RaisedButton é um botão com elevação que pode ser pressionado para executar uma ação.

```dart
RaisedButton(
  child: Text('Clique aqui'),
  onPressed: () {
    print('Botão pressionado');
  },
);
```

## 3. Checkbox

O widget Checkbox permite que os usuários selecionem ou desmarquem uma opção.

```dart
Checkbox(
  value: _isChecked,
  onChanged: (bool newValue) {
    setState(() {
      _isChecked = newValue;
    });
  },
);
```

## 4. Radio

O widget Radio permite que os usuários escolham uma opção em um conjunto de opções.

```dart
Radio(
  value: 1,
  groupValue: _selectedValue,
  onChanged: (int newValue) {
    setState(() {
      _selectedValue = newValue;
    });
  },
);
```

## 5. DropdownButton

O widget DropdownButton permite que os usuários selecionem uma opção em uma lista suspensa.

```dart
DropdownButton<String>(
  value: _selectedOption,
  items: <String>['Opção 1', 'Opção 2', 'Opção 3'].map((String value) {
    return DropdownMenuItem<String>(
      value: value,
      child: Text(value),
    );
  }).toList(),
  onChanged: (String newValue) {
    setState(() {
      _selectedOption = newValue;
    });
  },
);
```

## 6. Slider

O widget Slider permite que os usuários selecionem um valor arrastando um controle deslizante.

```dart
Slider(
  value: _sliderValue,
  min: 0,
  max: 100,
  onChanged: (double newValue) {
    setState(() {
      _sliderValue = newValue;
    });
  },
);
```

## 7. Switch

O widget Switch permite que os usuários ativem ou desativem um recurso.

```dart
Switch(
  value: _isSwitched,
  onChanged: (bool newValue) {
    setState(() {
      _isSwitched = newValue;
    });
  },
);
```


Esses são apenas alguns dos componentes de interação e entrada de dados disponíveis no Flutter. Ao combinar e personalizar esses componentes, você pode criar aplicativos interativos e fáceis de usar.