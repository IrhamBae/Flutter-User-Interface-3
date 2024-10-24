import 'package:flutter/material.dart';
void main() {
runApp(const MyApp());
}
class MyApp extends StatelessWidget {
const MyApp({super.key});
@override
Widget build(BuildContext context) {
return MaterialApp(
title: '1302220077',
theme: ThemeData(
colorScheme: ColorScheme.fromSeed(seedColor:
Colors.deepPurple),
useMaterial3: true,
),
home: const MyHomePage(title: '1302220077'),
);
}
}
class MyHomePage extends StatefulWidget {
const MyHomePage({super.key, required this.title});
final String title;
@override
State<MyHomePage> createState() => _MyHomePageState();
}
class _MyHomePageState extends State<MyHomePage> {
final List<Map<String,dynamic>> appList = [
{
"name" : "Native App",
"description" : "Android, iOS",
"color" : Colors.red,
},
{
"name" : "Hybrid App",
"description" : "Android, iOS, Web\nJavascript, Dart",
"color" : Colors.grey,
}
];
void showDetailDialog(BuildContext context, String title, String
description){
showDialog(
context: context,
builder: (BuildContext context) {
return AlertDialog(
title: const Text('Detail'),
content: Column(
mainAxisSize: MainAxisSize.min,
children: [
Text(
title,
style: const TextStyle(fontWeight: FontWeight.bold, 
fontSize: 20), 
),
const SizedBox(
width: 200,
height: 10
),
Text(
description,
textAlign: TextAlign.center,
),
],
),
actions: <Widget>[
TextButton(
child: const Text('close'),
onPressed: () {
Navigator.of(context).pop();
},
)
],
);
},
);
}
@override
Widget build(BuildContext context) {
return Scaffold(
appBar: AppBar(
title: Text(widget.title),
),
body: ListView.builder(
itemCount: appList.length,
itemBuilder: (context, index) {
return ListTile(
leading: CircleAvatar(
backgroundColor: appList[index]['color'],
),
title: Text(appList[index]['name']),
onTap: () {
showDetailDialog(
context,
appList[index]['name'],
appList[index]['description'],
);
},
);
},
),
);
}
}
