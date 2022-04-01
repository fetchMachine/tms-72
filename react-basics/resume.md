# JSX
Компонент - функция, названная с большой буквы, которая принимает один единственный параметр возвращает JSX разметку (один единственный элемент).
Можно работать, как и с любой js функцией - вызывать одну в другой, передавать как параметр и проч.

```javascript
const MyGreetComponent = (props) => {
    return <div>Привет, {props.name}</div>
}
```

JSX - расширение (надмножество) над язык JS, которое позволяет писать html в JS файлах.
Для написания JS в html используются фигурные скобки, пример: ```{props.name}```

# Условный рендер
1. Условный оператор if/else
2. Тернарный оператор
3. Операторы сравнения (&&)

```javascript
// если пользователю больше 18 лет - показывает приветствие, иначе показываем предупреждение
const Msg = (props) => {
    return <span>{props.message}</span>
}

const GreetMsg = () => {
    return <Msg message="Добро пожаловать на сайт" />
}

const ForbiddenMsg = () => {
    return <Msg message="Вы еще молоды, покиньте сайт" />
}

сonst ConditionalCheck = (props) => {
    if (props.age > 18) {
        return <GreetMsg />
    }
    
    return <ForbiddenMsg />
}


const TernaryCheck = () => {
    return props.age > 18 ? <GreetMsg /> : <ForbiddenMsg />;
}

const BooleanCheck = () => {
    return (
        <div>
            {props.age > 18 && <GreetMsg />}
            {props.age < 18 && <ForbiddenMsg />}
        </div>
    );
}
```

# Обходи массива
Не забываем про пропс key, который нужен для оптимизации рендеров react и обязательно должен быть уникальным среди элементов братьев.

```javascript
const TodoList = () => {
    const tasks = [
        { id: 1, title: 'Выучить JS', isDone: true },
        { id: 2, title: 'Выучить React', isDone: false },
        { id: 3, title: 'Увидеть Париж и умереть', isDone: false },
    ];
    
    return (
        <ul>
            {tasks.map((task) => <li key={task.id}>{task.title}</li>)}
        </ul>
    );
}
```