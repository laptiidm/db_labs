**Концептуальне (інфологічне) проектування бази даних**

### 1. Опис предметної області
Система управління навчальним процесом призначена для організації та контролю виконання завдань студентами. Вона дозволяє викладачам створювати навчальні предмети, додавати завдання та відстежувати їх виконання. Студенти отримують завдання, виконують їх і отримують оцінки.

### 2. Інформаційні об'єкти та їх зв’язки
#### Основні інформаційні об'єкти:
1. **Студенти** (Students) – користувачі системи, які виконують завдання.
2. **Викладачі** (Teachers) – користувачі системи, які створюють завдання та оцінюють їх.
3. **Ролі** (Roles) – визначають, чи є користувач студентом, викладачем або адміністратором.
4. **Предмети** (Subjects) – дисципліни, які викладаються.
5. **Завдання** (Tasks) – навчальні завдання, які створюються викладачами в межах предметів.
6. **Призначені завдання** (Assigned_Tasks) – завдання, які були призначені конкретним студентам.
7. **Оцінки** (Grades) – результати перевірки завдань студентів.

#### Структурні зв’язки між об'єктами:
- Кожен **студент** має роль "Студент".
- Кожен **викладач** має роль "Викладач".
- Кожен **предмет** викладається певним викладачем.
- Кожне **завдання** належить до певного предмета.
- Кожне **завдання** може бути призначене одному або декільком студентам.
- Кожне **призначене завдання** отримує статус ("To Do", "In Progress", "Done").
- Кожне **призначене завдання** може мати оцінку, яку виставляє викладач.

### 3. Атрибути об'єктів

| **Об'єкт**       | **Атрибути**                                   |
|------------------|---------------------------------------------|
| Students        | id, first_name, last_name, email, role_id   |
| Teachers        | id, first_name, last_name, email, role_id   |
| Roles           | id, name ("Student", "Teacher", "Admin")   |
| Subjects        | id, name, teacher_id                        |
| Tasks           | id, title, description, subject_id         |
| Assigned_Tasks  | id, task_id, student_id, assigned_at, status |
| Grades          | id, assigned_task_id, value, graded_at     |

### 4. Діаграма зв'язків
[ER-діаграма бази даних](https://miro.com/welcomeonboard/dUdIM2I0WmlvaVM0MGhwM3VnRFozMzA2NWE0dFhmd3AxbUxhR1JvWDBUd0JZbmRkS2dlOE1pVFBsNzF1bzgrdmYrSDY2YmlLeU9nYnlYY3VncjJUc09vR2EzTkpDbThkdUw0dVNRS3MyWXcyakp2bC9MN21VU0I0OXRqOTVWMWtBd044SHFHaVlWYWk0d3NxeHNmeG9BPT0hdjE=?share_link_id=473611988203)

[Схема бази даних](https://dbdiagram.io/d/borda-67c4da1c263d6cf9a0f75dec)



### 5. Обмеження цілісності даних
- `role_id` у таблиці `students` і `teachers` має посилатися на `id` у таблиці `roles`.
- `teacher_id` у таблиці `subjects` має посилатися на `id` у таблиці `teachers`.
- `subject_id` у таблиці `tasks` має посилатися на `id` у таблиці `subjects`.
- `task_id` у таблиці `assigned_tasks` має посилатися на `id` у таблиці `tasks`.
- `student_id` у таблиці `assigned_tasks` має посилатися на `id` у таблиці `students`.
- `assigned_task_id` у таблиці `grades` має посилатися на `id` у таблиці `assigned_tasks`.

### 6. Висновки
Проектована база даних дозволяє ефективно управляти навчальним процесом, зберігаючи інформацію про студентів, викладачів, предмети, завдання та оцінки. Запропонована структура гарантує узгодженість даних та забезпечує підтримку основних операцій навчального процесу.

