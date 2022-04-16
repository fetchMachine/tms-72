# Redux HW

## Pre Request
- [Документация. "Redux Quick Start"](https://redux.js.org/tutorials/quick-start)
- [Документация. Весь раздел "Redux Essentials"](https://redux.js.org/tutorials/essentials/part-1-overview-concepts)
- **ВАЖНО!** [Документация. 3 принципа Redux](https://redux.js.org/understanding/thinking-in-redux/three-principles)

## Redux ToDo App
Перевести управление состоянием текущего todo app на redux
- Установить необходимые зависимости `npm i redux` и `npm i react-redux`
- Перевести весь стейт компонента (кроме значения инпута) на редакс:
    -  фильтры и таски лежат в redux
    -  логика создания / удаления / тогла таски находится в редюсере
    -  фильтрация тасок согласно выбранному фильтру происходит в селекторах, а не компоненте
- Установить `redux devtools` и его попробовать на практике (посмотреть на список задиспатченных экшенов, на состояние store, тайм тревел). [Документация по установке](https://github.com/reduxjs/redux-devtools/tree/main/extension#installation)
- Применить на практике combineReducers, сделав стейт вложенным, т.е. вместо `state = { users: [], filter: '' }` получить `state = { users: { users: [], filter: '' } }`. [Пример combineReducers из документации](https://redux.js.org/api/combinereducers#example)

[Пример начального внедрения Redux в Users App](https://github.com/fetchMachine/react-simple-todo/pull/1/files)
