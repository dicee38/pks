# Практическое занятие №5

**ФИО:** Демидов Иван Сергеевич 
**Группа:** ЭФБО-06-23


---

## 🎯 Цели ПЗ

1. Освоить принципы создания мобильных приложений с использованием Flutter.  
2. Научиться работать со списками данных, их добавлением, редактированием и удалением.  
3. Закрепить навыки использования состояния (`setState`), работы с виджетами и обработчиками событий.  

---

## ⚙️ Ход работы

### Шаг 1. Создание проекта
Создан новый Flutter-проект командой:
```bash
flutter create flutter_application_1
Шаг 2. Разработка интерфейса
В lib/main.dart описан интерфейс списка задач. Использованы виджеты:

Scaffold, AppBar, ListView, FloatingActionButton, TextField.

Ключевой фрагмент кода 1: создание списка задач

dart
Копировать код
List<String> tasks = [];

ListView.builder(
  itemCount: tasks.length,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text(tasks[index]),
      trailing: IconButton(
        icon: Icon(Icons.delete),
        onPressed: () {
          setState(() {
            tasks.removeAt(index);
          });
        },
      ),
    );
  },
);
🔹 Этот код отвечает за отображение динамического списка с возможностью удаления элементов.

Ключевой фрагмент кода 2: добавление новой задачи

dart
Копировать код
FloatingActionButton(
  onPressed: () {
    setState(() {
      tasks.add(_controller.text);
      _controller.clear();
    });
  },
  child: Icon(Icons.add),
);
🔹 При нажатии на кнопку задача добавляется в список.

Ключевой фрагмент кода 3: редактирование задачи

dart
Копировать код
void editTask(int index) {
  TextEditingController editController = TextEditingController(text: tasks[index]);
  showDialog(
    context: context,
    builder: (context) {
      return AlertDialog(
        title: Text('Редактировать задачу'),
        content: TextField(controller: editController),
        actions: [
          TextButton(
            onPressed: () {
              setState(() {
                tasks[index] = editController.text;
              });
              Navigator.pop(context);
            },
            child: Text('Сохранить'),
          ),
        ],
      );
    },
  );
}
🔹 Диалоговое окно позволяет редактировать выбранную задачу.

🖼️ видео работы приложения


🧭 Выводы
В ходе выполнения практической работы:

Реализовано мобильное приложение со списком задач.

Научился работать с состоянием и динамическими списками во Flutter.

Освоил базовые виджеты Material Design и принципы UI-взаимодействия.

Сложности:

Настройка окружения Flutter на Windows и ошибки сборки Gradle.

Проблема с путями, содержащими кириллицу, решена переносом проекта в директорию с латиницей.

Результат:
✅ Приложение корректно добавляет, редактирует и удаляет элементы списка.
