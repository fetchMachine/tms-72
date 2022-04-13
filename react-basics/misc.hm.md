# React Ctx / Portal HW

## Feautures
- [Контекст](https://ru.reactjs.org/docs/context.html)
- [Порталы](https://ru.reactjs.org/docs/portals.html)
- [Предохранители](https://ru.reactjs.org/docs/error-boundaries.html)
- [Рефы и DOM](https://ru.reactjs.org/docs/refs-and-the-dom.html)
- [Перенаправление рефов](https://ru.reactjs.org/docs/forwarding-refs.html)

## Patterns
- [Рендер-пропсы](https://ru.reactjs.org/docs/render-props.html)
- [Компоненты высшего порядка](https://ru.reactjs.org/docs/higher-order-components.html)
- [Неуправляемые компоненты](https://ru.reactjs.org/docs/uncontrolled-components.html)

## JSX
- [JSX в деталях](https://ru.reactjs.org/docs/jsx-in-depth.html)

## PropTypes
- [Проверка типов с помощью PropTypes](https://ru.reactjs.org/docs/typechecking-with-proptypes.html)

## Registration App
**Пункты можно делать в произвольном порядке, если на каком-то застряли, можно перейти к следующему, а потом вернуться.**
Делаем в отдельном репозитории. Как и раньше в ветке main делаем чистое react приложение с помощью `create-react-app`, после чего создаем ветку feature/regiostration, работает в ней, делаем МР и кидаем мне ссылку на него.
- Сверстать форму регистрации: 2 инпута (логин и пароль) + радиогруппа выбора пола (изначально выбран какой-либо пол) + чекбокс с согласием на рассылку новостей (изначально проставлен) + Кнопка "Зарегистрироваться". Все элементы должны быть управляемыми (т.е. в нашем компоненте есть `state` и мы прокидыаем во все элементы `value` и `onChange`)
- Сверстать модалку (абсолютно спозиционированный div посреди экрана). Завести в компоненте использующим модалку состояние показывающее / скрывающее модалку `this.state.isModalVisible` и использовать условный рендер для ее отображения `{this.state.isModalVisible && <Modal />}`
```css
// примерные стили модалки
.modal {
width: 250px;
    height: 250px;
    border-radius: 8px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    box-shadow: 0px 0px 32px rgb(28 41 61 / 5%), 0px 32px 32px rgb(28 41 61 / 6%);
}
```
- Модалка должна содержать все данные с которыми пользователь зарегистрировался иметь кнопку "ОК" и уметь закрываться по нажатию на эту кнопку или по нажатию клавиши esc. Для это родительский компонент прокинет ей пропс onClose. Который будет применен на onClick кнопки. Дополнительно использовать метод жизненного цикла componentDidMount, чтобы средствами JS повесить обработчик событий 'keypress' на body, который будет вызвать onClose. Использовать метод жизненного componentWillMount, чтобы снять оброботчик при демонтировании модалки.
```javascript
state = { isModalVisible: true };

modalCloseHandler = () => { this.setState({ isModalVisible: false }) };

render () {
    const { isModalVisible } = this.state;

    return (
            <div>
            ...
            {isModalVisible && (
                <Modal onClose={this.modalCloseHandler}>
                    {this.state.login}, Вы успешно зарегистрировались...
                </Modal>
            )}
            ...
        </div>
    );
}
```
- Кнопка "Зарегистрироваться" при нажатии валидирует введенные значения (логин и пароль больше 5 символов)
    - в случае невалидных значений (`state.login.length < 5 || state.password.length < 5`) под каждым невалидным инпутом вывести сообщение об ошибке "Минимальная длинна поля 5 символов"
    - в случае в валдиных значений показать модалку об успешной регистрации (`state.isModalVisible` переводим в true)
- Применить портал для модалки - модалка должна рендерится в body.
- Протипизировать все пропсы с помощью библиоткеи `prop-types`
- Создать компоненте ErroBoundary как в примере документации реакта или лекции и обернуть в него модалку.
- Применить контекст - Модалка должна получать данные о зарегистрированном пользователе через контекст
