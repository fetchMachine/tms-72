# Redux HW

## Pre Request
- [Все статьи из раздела "Хуки"](https://ru.reactjs.org/docs/hooks-intro.html)
- [**!Важно.** Правила хуков](https://ru.reactjs.org/docs/hooks-rules.html)

## ToDo App
1. Перевести Todo App на хуки:
    - Заменить все классовые компоненты функциональными. Вместо `this.state` / `this.setState` использовать хук [useState](https://ru.reactjs.org/docs/hooks-state.html)
    - Удалить все `connect` редакса. Вместо `mapStateToProps` использовать хук [useSelector](https://react-redux.js.org/api/hooks#useselector). Вместо `mapDispatchToProps` использовать хук [useDispatch](https://react-redux.js.org/api/hooks#usedispatch)
    - Удалить `withRouter` реакт-роутера. Для получения `match` / `location` / `history` использовать соответственно хуки [useParams](https://v5.reactrouter.com/web/api/Hooks/useparams) / [useLocation](https://v5.reactrouter.com/web/api/Hooks/uselocation) / [useHistory для v5 роутера](https://v5.reactrouter.com/web/api/Hooks/usehistory) или [useNavigate для v6 роутера](https://reactrouter.com/docs/en/v6/api#usenavigate)
2. Внедрить redux-toolkit в приложение:
    - вместо `createStore` воспользоваться [configureStore](https://redux-toolkit.js.org/api/configureStore). Теперь можно можете "мутировать" стору
    - вместо `constants` / `actionCreators` / `reducer` использовать [createSlice](https://redux-toolkit.js.org/api/createSlice)

## Weathe App
1. Перевести Todo App на хуки:
    - Выполнить все замены аналогично Todo App п.1.
    - Вместо `методов жизненного цикла` использовать хук [useState](https://ru.reactjs.org/docs/hooks-state.html)
    - Для создания debounce версии функции воспользоваться хуком [useCallback](https://ru.reactjs.org/docs/hooks-reference.html#usecallback). Подробнее в записи лекции.
2. Написать свой кастомный хук `useWeather`, куда вынести всю логику из компонента погоды. Компонент должен теперь содержать только разметку и вызовы хука `useWeather`.
3. Внедрить redux-toolkit в приложение:
    - Выполнить все замены аналогично Todo App п.2
    - Вместо функций санок воспользоваться [createAsyncThunk](https://redux-toolkit.js.org/api/createAsyncThunk).
