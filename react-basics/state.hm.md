# React State HW

## Pre Request
- [Состояние и жизненный цикл](https://ru.reactjs.org/docs/state-and-lifecycle.html)
- [Обработка событий](https://ru.reactjs.org/docs/handling-events.html)
- [Формы](https://ru.reactjs.org/docs/forms.html)
- [Подъём состояния](https://ru.reactjs.org/docs/lifting-state-up.html)
- [Философия React](https://ru.reactjs.org/docs/thinking-in-react.html)

## Keep in Mind
- Никогда не мутируем state.
- Если новый state рассчитываем на основе предыдущего, то всегда используем синтаксис колбека. Пример: ```this.setState((prevState) => ({ isVisible: !prevState.isVisible })```
 
## Life "TODO" App
- Смержить ветку с прошлым дз в main и создать новую `feature/todo_state`.
- Переписать существующий функциональный компонент App на классовый.
- Внедрить в него state и сделать приложение полностью функциональным (работает инпут, кнопки добавления и удаления задачи, тогла статуса задачи, фильтры)
- Попробовать на практике все 3 метода жизненного цикла (componentDidMount / componentDidUpdate / componentWillUnmount) - внедрить реализации консоль логов и посмотреть когда отрабатывают. Метод жизненного цикла componentWillUnmount будет у чекбоксов, которые удаляются (а значит размонтируются) при измении фильтра.
- Добавить синхронизацию залач с localStorage (на старте приложения загружаются задачи из localStorage, при измении / доавлении / удалении задачи - localStorage обновляется)
- Сделать Pull Request в main ветку и скинуть мне ссылку на него.

[Пример схожего приложения](https://github.com/fetchMachine/react-simple-todo)
