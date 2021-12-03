```
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      home: HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  const HomePage({Key? key}) : super(key: key);

  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  TextEditingController primeiroNumero = TextEditingController();
  TextEditingController segundoNumero = TextEditingController();
  int resultado = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Primeiro App"),
      ),
      body: Column(
        crossAxisAlignment: CrossAxisAlignment.stretch,
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          Text(
            "$resultado",
            style: const TextStyle(
              fontSize: 50,
            ),
            textAlign: TextAlign.center,
          ),
          Padding(
            padding: const EdgeInsets.all(20),
            child: TextFormField(
              controller: primeiroNumero,
              decoration: const InputDecoration(
                label: Text(
                  "Primeiro número",
                ),
              ),
            ),
          ),
          Padding(
            padding: const EdgeInsets.all(20),
            child: TextFormField(
              controller: segundoNumero,
              decoration: const InputDecoration(
                label: Text(
                  "Segundo número",
                ),
              ),
            ),
          ),
          Padding(
            padding: const EdgeInsets.all(20),
            child: ElevatedButton(
              onPressed: () {
                int primeiro = int.parse(primeiroNumero.text);
                int segundo = int.parse(segundoNumero.text);
                resultado = primeiro + segundo;
                setState(() {
                  primeiroNumero.clear();
                  segundoNumero.clear();
                });
              },
              child: const Text("Somar"),
            ),
          ),
          Padding(
            padding: const EdgeInsets.all(20),
            child: ElevatedButton(
              onPressed: () {
                primeiroNumero.clear();
                segundoNumero.clear();
                resultado = 0;
                setState(() {});
              },
              child: const Text("Limpar"),
            ),
          ),
        ],
      ),
    );
  }
}


```