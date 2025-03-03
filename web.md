## **✅ 1주차: Flutter Web 기초 & 환경 설정 **
**목표:**  
- Flutter Web의 기본 개념을 익히고, 간단한 UI를 구현한다.  
- 반응형 웹 UI를 이해하고, 간단한 프로젝트를 만든다.

---

### **📌 Day 1: Flutter Web 환경 설정 및 실행**
**🔹 할 일**
- Flutter 최신 버전 설치 확인 (`flutter doctor` 실행)
- Flutter Web 프로젝트 생성 및 실행
- 기본적인 `MaterialApp`, `Scaffold`, `Column`, `Row` 이해
- **[실습]** "Hello Flutter Web!" 웹 앱 실행해보기

**📌 실습 코드**
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Web Demo',
      home: Scaffold(
        appBar: AppBar(title: const Text('Flutter Web 시작하기')),
        body: const Center(child: Text('Hello Flutter Web!')),
      ),
    );
  }
}
```

**🔹 공부할 개념**
- Flutter Web과 모바일 Flutter의 차이점  
- 웹 실행 방법 (`flutter run -d chrome`)  

**📌 추천 자료**
- [Flutter Web 공식 문서](https://docs.flutter.dev/web)
- [Flutter 설치 가이드](https://docs.flutter.dev/get-started/install)

---

### **📌 Day 2: Flutter Web 레이아웃 기초**
**🔹 할 일**
- Flutter에서 웹 UI를 구성하는 주요 위젯 학습  
  - `Column`, `Row`, `Container`, `SizedBox`, `Expanded` 등  
- 반응형 디자인을 위한 `MediaQuery` 사용법 익히기  
- **[실습]** 간단한 네비게이션 바 만들기

**📌 실습 코드 (네비게이션 바 예제)**
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Web',
      home: Scaffold(
        appBar: AppBar(title: const Text('Flutter Web Navigation')),
        body: Column(
          children: [
            Container(
              padding: const EdgeInsets.all(10),
              color: Colors.blue,
              child: Row(
                mainAxisAlignment: MainAxisAlignment.spaceAround,
                children: const [
                  Text('Home', style: TextStyle(color: Colors.white, fontSize: 18)),
                  Text('About', style: TextStyle(color: Colors.white, fontSize: 18)),
                  Text('Contact', style: TextStyle(color: Colors.white, fontSize: 18)),
                ],
              ),
            ),
            const Expanded(
              child: Center(child: Text('Welcome to Flutter Web!')),
            ),
          ],
        ),
      ),
    );
  }
}
```

**🔹 공부할 개념**
- `Row`, `Column`, `Expanded` 활용법  
- `Container`를 활용한 스타일링  
- `mainAxisAlignment`와 `crossAxisAlignment` 이해  

**📌 추천 자료**
- [Flutter 레이아웃 공식 문서](https://docs.flutter.dev/ui/layout)

---

### **📌 Day 3: Flutter Web 네비게이션 및 페이지 이동**
**🔹 할 일**
- 웹에서 **Navigator 2.0 (페이지 이동 방식)** 익히기  
- `onGenerateRoute`를 사용한 페이지 이동  
- **[실습]** 2~3개의 화면을 가진 웹 페이지 만들기

**📌 실습 코드 (페이지 이동 예제)**
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Web Navigation',
      initialRoute: '/',
      routes: {
        '/': (context) => const HomePage(),
        '/about': (context) => const AboutPage(),
      },
    );
  }
}

class HomePage extends StatelessWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Home')),
      body: Center(
        child: ElevatedButton(
          onPressed: () => Navigator.pushNamed(context, '/about'),
          child: const Text('Go to About Page'),
        ),
      ),
    );
  }
}

class AboutPage extends StatelessWidget {
  const AboutPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('About')),
      body: Center(
        child: ElevatedButton(
          onPressed: () => Navigator.pop(context),
          child: const Text('Back to Home'),
        ),
      ),
    );
  }
}
```

**🔹 공부할 개념**
- `Navigator.pushNamed()`, `Navigator.pop()` 사용법  
- 웹에서의 `onGenerateRoute` 설정  

**📌 추천 자료**
- [Flutter 네비게이션 공식 문서](https://docs.flutter.dev/cookbook/navigation)

---

### **📌 Day 4: 반응형 UI 및 화면 크기 대응**
**🔹 할 일**
- 반응형 웹 UI 만들기  
  - `MediaQuery` 활용  
  - `LayoutBuilder`를 사용하여 다양한 화면 크기에 대응  
- `responsive_builder` 패키지 활용하기  
- **[실습]** 화면 크기에 따라 레이아웃이 바뀌는 웹 페이지 만들기

**📌 실습 코드 (반응형 UI 예제)**
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Responsive UI',
      home: Scaffold(
        appBar: AppBar(title: const Text('Responsive UI')),
        body: LayoutBuilder(
          builder: (context, constraints) {
            if (constraints.maxWidth > 600) {
              return const Center(child: Text('Large Screen'));
            } else {
              return const Center(child: Text('Small Screen'));
            }
          },
        ),
      ),
    );
  }
}
```

**🔹 공부할 개념**
- `MediaQuery`와 `LayoutBuilder` 차이점  
- 웹에서 반응형 UI를 어떻게 처리하는지  

**📌 추천 자료**
- [Flutter 반응형 UI 공식 문서](https://docs.flutter.dev/ui/layout/responsive)

---

### **📌 Day 5-6: 미니 프로젝트 (Todo 리스트)**
**🔹 할 일**
- **Flutter Web을 활용한 간단한 프로젝트** 만들기
  - 사용자가 입력한 할 일을 리스트로 저장
  - 완료한 일은 체크박스로 표시
  - 데이터를 `ListView.builder`로 화면에 출력
- 버튼 클릭 이벤트 핸들링 연습
- `setState()`와 상태 관리 기초 익히기

**📌 실습 코드 (간단한 Todo 앱)**
```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatefulWidget {
  const MyApp({super.key});

  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  final List<String> todos = [];

  void addTodo(String task) {
    setState(() {
      todos.add(task);
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text('Todo List')),
        body: Column(
          children: [
            TextField(
              onSubmitted: addTodo,
              decoration: const InputDecoration(hintText: 'Enter task'),
            ),
            Expanded(
              child: ListView.builder(
                itemCount: todos.length,
                itemBuilder: (context, index) {
                  return ListTile(title: Text(todos[index]));
                },
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

---

### **📌 Day 7: 복습 및 정리**
- 배운 개념 정리  
- Flutter Web 프로젝트 배포 실습 (GitHub Pages 또는 Firebase Hosting)  

---


