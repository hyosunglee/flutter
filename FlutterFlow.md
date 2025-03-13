FlutterFlow에서는 코드를 직접 추가할 수 있는 기능이 제한적이지만, Custom Actions 및 Custom Functions을 활용하여 일부 Dart 코드를 실행할 수 있습니다.

⸻

✅ FlutterFlow에서 코드 추가 방법

FlutterFlow에서 기본적으로 룰렛 애니메이션 기능이 없으므로 다음 방법을 사용할 수 있습니다.

1️⃣ Custom Actions (사용자 정의 액션)

FlutterFlow에서 Custom Action을 생성하여 랜덤 선택 로직을 직접 구현할 수 있습니다.

📌 Custom Action을 만드는 방법
	1.	FlutterFlow 대시보드에서 프로젝트 열기
	2.	왼쪽 메뉴 → “Custom Functions” → “Add Action” 클릭
	3.	이름을 randomChoice로 설정
	4.	Dart 코드 추가 (랜덤 선택 기능 구현)

import 'dart:math';

String randomChoice(List<String> choices) {
  if (choices.isEmpty) return "선택지가 없습니다.";
  int randomIndex = Random().nextInt(choices.length);
  return choices[randomIndex];
}

	5.	Save & Compile 후 저장
	6.	“선택하기” 버튼의 Action 설정에서 "Run Custom Action" 선택 → randomChoice 사용

➡️ 이 방식은 FlutterFlow에서 랜덤으로 선택하는 기능을 추가하는 데 적합합니다.

⸻

2️⃣ Custom Widgets (Flutter 위젯 직접 추가)

FlutterFlow에서는 완전히 자유로운 코드를 추가할 수는 없지만, Custom Widgets 기능을 사용하면 일부 Flutter 코드를 직접 추가할 수 있습니다.

📌 Custom Widget을 활용하여 룰렛 애니메이션 추가
	1.	FlutterFlow에서 “Custom Widgets” 메뉴로 이동
	2.	새 위젯 추가 → “FortuneWheel” 생성
	3.	아래 룰렛 애니메이션 코드 추가

import 'package:flutter_fortune_wheel/flutter_fortune_wheel.dart';
import 'dart:math';
import 'package:flutter/material.dart';

class RouletteWheel extends StatefulWidget {
  final List<String> choices;
  const RouletteWheel({Key? key, required this.choices}) : super(key: key);

  @override
  _RouletteWheelState createState() => _RouletteWheelState();
}

class _RouletteWheelState extends State<RouletteWheel> {
  final _selectedIndex = StreamController<int>();

  @override
  void dispose() {
    _selectedIndex.close();
    super.dispose();
  }

  void _spinWheel() {
    if (widget.choices.isEmpty) return;
    int randomIndex = Random().nextInt(widget.choices.length);
    _selectedIndex.add(randomIndex);
  }

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Expanded(
          child: FortuneWheel(
            selected: _selectedIndex.stream,
            items: [
              for (var choice in widget.choices)
                FortuneItem(
                  child: Text(choice, style: TextStyle(fontSize: 18)),
                )
            ],
          ),
        ),
        SizedBox(height: 20),
        ElevatedButton(
          onPressed: _spinWheel,
          child: Text("룰렛 돌리기"),
        ),
      ],
    );
  }
}

	4.	Custom Widget을 UI에 추가
	5.	choices 값을 FlutterFlow에서 동적으로 설정

➡️ 이 방식은 FlutterFlow에서 완전히 새로운 룰렛 위젯을 추가하는 방법입니다.

⸻

✅ 결론: FlutterFlow에서 가능한 방법

✔ Custom Action → 랜덤 선택 기능 구현 (FlutterFlow UI와 쉽게 연결 가능)
✔ Custom Widget → 직접 Dart 코드 추가하여 룰렛 애니메이션 구현

👉 어떤 방식이 더 적합할까요?
	1.	빠른 구현이 필요하면 Custom Action 추천
	2.	룰렛 애니메이션까지 포함하려면 Custom Widget 활용

질문이 있으면 추가로 설명해 드릴게요! 🚀