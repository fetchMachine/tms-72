# React Basic HW

## Pre Request
- [Кротчайшее резюме](./resume.md)
- [Знакомство с JSX](https://ru.reactjs.org/docs/introducing-jsx.html)
- [Рендеринг элементов](https://ru.reactjs.org/docs/rendering-elements.html)
- [Компоненты и пропсы](https://ru.reactjs.org/docs/components-and-props.html)
- [Условный рендеринг](https://ru.reactjs.org/docs/conditional-rendering.html)
- [Списки и ключи](https://ru.reactjs.org/docs/lists-and-keys.html)
- [Фрагменты](https://ru.reactjs.org/docs/fragments.html)
- [Философия React. Шаги 1 - 2](https://ru.reactjs.org/docs/thinking-in-react.html)

## Подготовить проект
- Создать отдельный репозиторий
- Создать базовое React приложение с помощью create-react-app ```npx create-react-app myApp --template typescript```
- Опционально - удалить неиспользуемые файлы
- Установить и настроить editorconfig (создать файл .editorconfig с конфигами как в примере ниже + установить расширение для VSCode)
- Получившееся базовое приложение запушить в main

[Пример готового пустого приложения](https://github.com/fetchMachine/clean-cra)
 
## "TODO" App
- Todo App делать в отельной ветке feature/todo
- Создаем разметку для Todo App:
    - Присутствует инпут + кнопка для создания новой задачи
    - Присутствует список отображающий массив задач вида ```const tasks = [{ id: 1, label: 'Выучить JS', isDone: true }, { id: 2, label: 'Выучить React', isDone: false }]```. Каждый элемент списка представляет собой чекбокс с соответствующим статусом (задача выполнена / невыполнена), label задачи и кнопка удалить (кнопка отображается только для выполненных задач)
    - Есть радиогруппа для фильтрации списка задача - "Все" / "Сделать" / "Сделано". Один из фильтров всегда выбран и при изменении выбора (изменение пока только руками в коде - на ui логики выбора может не быть) фильтруется список задач. 
- Применить технологию css modules для любой стилизации по своему вкусу.
- Сделать Pull Request в main ветку и скинуть мне ссылку на него.

[Пример схожего приложения](https://github.com/fetchMachine/react-simple-todo)
