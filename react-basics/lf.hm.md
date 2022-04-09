# React Life Cycles HW

## Pre Request
- [Ссылки с прошлой лекии](./state.hm.md)
- [Тротлинг](https://learn.javascript.ru/task/throttle)
- [Дебаунс](https://learn.javascript.ru/task/debounce)
- [lodash debounce](https://lodash.com/docs/4.17.15#debounce)

## Environment Variables (env)
Мы хотим иметь возможность конфигурировать наше приложение перед сборкой. В т.ч. иметь возможность скрыть часть секретной информации (например, токен) из кодовой базы, т.е. не держать сам токен в кодовой базе, а подставлять его на этапе сборки. Для этих целей служат переменные окружения:
- Создать файл `.env ` в своем проекте и добавить его в `.gitignore`
- Создать в нем любые необходимые переменные (по требования create-react-app переменные должны начинаться с префикса `REACT_APP_`)
- Теперь эти переменные доступны в любой точке вашего приложения в виде `process.env.YOUR_VARIABLE`. Пример
```javascript
// .env
REACT_APP_WEATHER_TOKEN=345tgfddr43

// App.jsx
export cons App () => {
    return <div>Your token is: {process.env.REACT_APP_WEATHER_TOKEN}</div>
}
```


## Weather App
- Создать отдельный репозиторий с "чистым" create-react-app приложение в ветке main.
- Сделать отдельную ветку `feature/weather_app`.
-  Использовать классовый компонет с состоянием `state = { city: '' }`, который возвращает из рендера  управляемый html инпут (управляемый === связан со стейтом компонента, т.е. в инпут мы прокидывает value и onChange).
-  Создать метод `fetchWeather` который делает `console.log`. Используя метод жизненного цикла `componentDidUpdate` вызвать `fetchWeather` на изменение состояния. Проверить что наборе текста в инпуте у нас происходят консоль логи из `fetchWeather`
-  Используя debounce функцию из lodash создать `fetchWeatherDebounced` версию функции и вызвать ее в `componentDidUpdate` вместо оригинальной. Проверить работоспособность `fetchWeatherDebounced` - при наборе текста в инпуте.
-  Подготовить компонент для работы с сетевыми запросами: 1) добавить в стейт поля data и loadStatus `state = { city: '', data: {}, loadStatus: LOAD_STATUSES.UNKNOWN }`. 2) В рендере используя условный рендер возвращать соответствующую для loadStatus разметку, например для ошибки: `{loadstatus === LOAD_STATUSES.EROR && <p>Не удалось получить данные, попробуйте изменить запрос</p>}`. 3) Т.к. у нас теперь в стейте 3 поля, а `componentDidUpdate` срабатывает на любое изменение стейта или пропсов, то `fetchWeatherDebounced` вызывается при любом изменении стейта. Нам же нужно делать запрос на бекенд только при изменении запроса пользователя, т.е. изменении `state.city`. Добавить соответствующую проверку в `componentDidUpdate` - вызвать `fetchWeatherDebounced`, только если `prevState.city !== state.city`.
-  Связать компонент с бекендом:
    - `fetchWeather` вместо консоль лога делать `fetch` запрос по адресу `https://api.openweathermap.org/data/2.5/weather?appid=ТОКЕН&q=ГОРОД_ДЛЯ_ПОИСКА&units=ЕДИНИЦА_ИЗМЕРЕНИЯ`. Токен брать из env переменных.
    - Перед fetch запросом установить корректный лоадстатус `setState({ loadStatus: LOAD_STATUSES.LOADING })`, в случае ошибки запроса установить корректный лоадстатус `setState({ loadStatus: LOAD_STATUSES.ERROR })`, в слачае успеха установить корректный лоадстатус и положить данные в стейт `setState({ loadStatus: LOAD_STATUSES.LOADED, data: responseData })`
    - Убедится, что все работает - при изменении текста в инпуте после задержки запрос уходит на бекенд и показывается Loader, после ответа бекенда данные кладутся в стейт и мы видим их на ui.
    - Для улучшения архитектуры и переиспользования кода мы вместо того чтобы вызывать `fetch` напрямую из компонента, хотим вынести ее в отдельную функцию и вызвать ее. Создать папку `api` в ней будет лежать все функции для работы с бекендом. Создать функцию `getCurrentWeather` вынести в нее код из `fetchWeather` компонента, который делает fetch запрос. В самом компонете вызвать `getCurrentWeather`. **Примерный** итоговый вид метода `fetchWeather` нашего компонента:
    ```javascript
    fetchWeather(params) {
        this.setState({ loadStatus: LOAD_STATUSES.LOADING });
        
        getCurrentWeather(params)
            .then((data) => {
                this.setState({ loadStatus: LOAD_STATUSES.LOADED, data });
            })
            .catch(() => {
                this.setState({ loadStatus: LOAD_STATUSES.ERROR, data: {} });
            });
    }
    ```

-  Используя css modules добавить стилизацию по вкусу.
- Сделать Pull Request в main ветку и скинуть мне ссылку на него.
