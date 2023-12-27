## Unit-tests, testing pyramid, integration tests
### Basic concepts: Test Plan, Test Suite, Test Case
**Тест план (Test Plan)** - это документ, описывающий весь объем работ по тестированию, начиная с описания объекта, стратегии, расписания, критериев начала и окончания тестирования, до необходимого в процессе работы оборудования, специальных знаний, а также оценки рисков с вариантами их разрешения.

*Что надо тестировать?*
описание объекта тестирования: системы, приложения, оборудования
*Что будете тестировать?*
список функций и описание тестируемой системы и её компонент в отдельности
*Как будете тестировать?*
стратегия тестирования, а именно: виды тестирования и их применение по отношению к объекту тестирования
*Когда будете тестировать?*
последовательность проведения работ: подготовка (Test Preparation), тестирование (Testing), анализ результатов (Test Result Analisys) в разрезе запланированных фаз разработки
*Критерии начала тестирования:*
готовность тестовой платформы (тестового стенда)
законченность разработки требуемого функционала
наличие всей необходимой документации
*Критерии окончания тестирования:*
результаты тестирования удовлетворяют критериям качества продукта:
требования к количеству открытых багов выполнены
выдержка определенного периода без изменения исходного кода приложения Code Freeze (CF)
выдержка определенного периода без открытия новых багов Zero Bug Bounce (ZBB)

**Тест Сьют** это набор тест кейсов, которые объединены тем что относятся к одному тестируемому модулю, функциональности, приоритету или одному типу тестирования. Каждый тест сьют состоит из более чем одного тест кейса и зачастую выполняется всей «пачкой» в процессе тестирования.

**Тест-кейс** — это форма записи проверки, которую проводит тестировщик. По сути, это алгоритм действий, по которому предполагается тестировать уже написанную программу. В нём подробно прописаны шаги, которые нужно сделать для подготовки к тесту, сама проверка и ожидаемый результат.
Тестировщик выполняет тест-кейс последовательно, шаг за шагом. Если фактический результат соответствует ожидаемому — всё хорошо. Если нет, тестировщик анализирует, что произошло. Это может быть ошибка в программе, в тест-кейсе из-за его неактуальности или в тестовом стенде. Если дело в программе, инженер составляет отчёт об ошибке и отправляет его разработчикам. Если в тест-кейсе — исправляет сам. Если в стенде — обращается к техническим специалистам.

Как правило, один тест-кейс описывает небольшую последовательность действий с одним конкретным результатом. Например, успешную авторизацию на сайте для конкретного пользователя или добавление одного конкретного товара в корзину.

Благодаря тест-кейсам специалисты всегда знают, как и что протестировать оптимальным количеством проверок, и не забывают о нюансах, так как записан каждый шаг. И им не приходится каждый раз заглядывать в документацию продукта или спрашивать команду, что и как должно работать.

**Тест-кейс** — достаточно подробная инструкция. Обычно форма тест-кейса чёткая и строгая, с конкретной структурой, и в нём обязательно прописаны тестовые данные для проверки, шаги, предварительные условия и ожидаемый результат.

## Testing Pyramid

**Пирамида тестирования** - это концепция, которая описывает порядок или приоритет различных типов тестирования в процессе разработки программного обеспечения. Она включает четыре основных уровня:

1. *Unit-тестирование*: Это самый базовый уровень, который предполагает проверку отдельных компонентов или модулей программы. Основная цель юнит-тестирования - проверить, работает ли каждый компонент должным образом.
2. *Интеграционное тестирование*: На этом уровне тестируются взаимодействия между отдельными компонентами или модулями программы. Здесь проверяются интерфейсы и границы между различными компонентами.
3. *Системное тестирование*: Этот уровень предполагает тестирование всей системы в целом. На данном этапе проверяется, как система работает в контексте реальных бизнес-процессов или требований пользователя.
4. *Приемочное тестирование* (или альфа/бета-тестирование): Это финальный уровень пирамиды. Здесь тестировщики проверяют, соответствует ли система требованиям заказчика и готова ли она к использованию.
Пирамида тестирования помогает упорядочить и распределить ресурсы на различные виды тестирования, учитывая их сложность, стоимость и важность для качества продукта. Обычно, пирамида тестирования предполагает, что юнит-тестирование должно быть выполнено в первую очередь, затем следует интеграционное тестирование и так далее по пирамиде.

### Different test types concepts: Unit/Integration/Functional ...
*Функциональное тестирование* - это тип тестирования программного обеспечения, который проверяет, выполняет ли программа заявленные функции в соответствии с требованиями и спецификациями. Функциональное тестирование обычно включает в себя тестирование каждого отдельного модуля или функции программы, а также тестирование взаимодействия между различными модулями. Цель функционального тестирования - убедиться, что программа работает корректно и соответствует всем функциональным требованиям.

### Properties of a good unit test;

- Good unit test properties:
- It should be automated and repeatable.
- It should be easy to implement.
- Once it's written, it should remain for future use.
- Anyone should be able to run it.
- It should run at the push of a button.
- It should run quickly.

### F.I.R.S.T;

*Быстрота (Fast)*. Тесты должны выполняться быстро. Все мы знаем, что разработчики люди, а люди ленивы, поскольку эти выражения являются “транзитивными”, то можно сделать вывод, что люди тоже ленивы. А ленивый человек не захочет запускать тесты при каждом изменении кода, если они будут долго выполняться.

*Независимость (Independent)*. Результаты выполнения одного теста не должны быть входными данными для другого. Все тесты должны выполняться в произвольном порядке, поскольку в противном случае при сбое одного теста каскадно “накроется” выполнение целой группы тестов.

*Повторяемость (Repeatable)*. Тесты должны давать одинаковые результаты не зависимо от среды выполнения. Результаты не должны зависеть от того, выполняются ли они на вашем локальном компьютере, на компьютере соседа или же на билд-сервере. В противном случае найти концы с концами будет весьма не просто.

*Очевидность (Self-Validating)*. Результатом выполнения теста должно быть булево значение. Тест либо прошел, либо не прошел и это должно быть легко понятно любому разработчику.  Не нужно заставлять людей читать логи только для того, чтобы определить прошел тест успешно или нет.

*Своевременность (Timely)*. Тесты должны создаваться своевременно. Несвоевременность написания тестов является главной причиной того, что они откладываются на потом, а это “потом” так никогда и не наступает. Даже если вы и не будете писать тесты перед кодом (хотя этот вариант уже доказал свою жизнеспособность) их нужно писать как минимум параллельно с кодом.

### JS Unit basics;

В JavaScript для написания юнит-тестов можно использовать различные библиотеки и фреймворки, такие как Jest, Mocha, Chai и другие. Вот пример юнит-теста, написанного с использованием библиотеки Jest:

```js
import { add } from './math.js';

describe('Math', () => {
  it('adds two numbers', () => {
    const result = add(2, 3);
    expect(result).toBe(5);
  });
});
```
В этом примере мы тестируем функцию add из файла math.js. Мы используем библиотеку Jest для создания юнит-теста и проверяем, что результат сложения двух чисел (2 и 3) равен 5. Если тест пройден, это означает, что функция add работает правильно.

### Test first development techniques (TDD and BDD)

## SyntheticEvent
- What is SyntheticEvent and what is it for
SyntheticEvent — это оболочка, основанная на собственных событиях браузера. Он предоставляет унифицированный API, предотвращает несогласованность браузера и гарантирует, что событие работает на нескольких платформах.

- Supported events
- What is the difference between event handling in 17 and previous versions of React?

## Bubbling event in react
### Working with bubbling in components
Bubbling (всплытие) в React компонентах работает по тому же принципу, что и в нативных событиях браузера. 

Когда происходит событие внутри компонента, оно сначала обрабатывается самим компонентом. Затем, если у компонента есть родительские компоненты, событие "всплывает" вверх по иерархии компонентов и обрабатывается родительским компонентом. Этот процесс продолжается до тех пор, пока событие не будет полностью обработано или не достигнет корневого компонента.

Пример:

```jsx
class ParentComponent extends React.Component {
  handleEvent = () => {
    console.log('Parent component event handler');
  }
  
  render() {
    return (
      <div onClick={this.handleEvent}>
        <ChildComponent />
      </div>
    );
  }
}

class ChildComponent extends React.Component {
  handleEvent = () => {
    console.log('Child component event handler');
  }
  
  render() {
    return (
      <div onClick={this.handleEvent}>
        Click me!
      </div>
    );
  }
}
```

В этом примере, если пользователь кликает на дочерний компонент `ChildComponent`, сначала вызывается обработчик события в `ChildComponent`, а затем событие "всплывает" и передается обработчику события в родительском компоненте `ParentComponent`. В результате в консоли будет выведено:

```
Child component event handler
Parent component event handler
```

Bubbling позволяет упростить обработку событий вложенных компонентов и делает код более модульным и гибким.

### Understanding How Portal Bubbling Works (Basic understanding)
Всплеск событий: по умолчанию события, исходящие из компонента портала, будут распространяться вверх по дереву React и запускать обработчики событий в компонентах-предках. Такое поведение не всегда может быть желательным. StopPropagation() или другие методы обработки событий могут предотвратить всплытие событий и гарантировать, что события обрабатываются только внутри компонента портала.
### Bubbling through portals (good understanding)

## Basic react optimization
### Confident knowledge of what keys are used for in react
Keys в React используются для оптимизации процесса рендеринга компонентов при изменении их порядка или количества. 

Ключи представляют собой уникальные идентификаторы, которые присваиваются каждому элементу списка (например, при использовании метода map) или компоненту внутри цикла. Ключи помогают React определить, какие элементы были добавлены, удалены или перемещены, и обновить только те компоненты, которые были изменены, вместо полного перерисования всего списка.

Без использования ключей React будет выполнять полный перерендеринг всех элементов списка при каждом изменении, что может привести к потере состояния компонентов и снижению производительности. 

Также, ключи используются для поддержки сохранения состояния компонентов при использовании списков или циклов внутри компонентов.

### Understanding how the shouldComponentUpdate lifecycle method works
### Strong knowledge, understanding when to use Component / PureComponent.
PureComponent похож на Component, но он пропускает повторные рендеринги для тех же пропсов и состояний.
Если компонент содержит сложную логику с обновлением состояния или пропсов, то может быть лучше использовать Component и явно реализовать метод shouldComponentUpdate для оптимизации процесса обновления.
### How to work with props to avoid unnecessary redrawing.
- Ability to profile bottlenecks in the code

## Reselect&Recompose
- Understanding what Reselect and Recompose are used for
- Ability to describe in your own words
- Good understanding of the two libraries. Note: It is assumed that the person has already worked with them for a short time"
- Deep understanding of the API

Reselect и Recompose - это библиотеки, которые используются в разработке приложений на React. Они помогают улучшить производительность и управление состоянием компонентов.

Reselect является селектором, который позволяет выбирать и комбинировать данные из Redux-хранилища. Он предоставляет мемоизацию, что означает, что результаты вызовов селекторов кэшируются и возвращаются только в случае изменения входных данных. Это позволяет избежать ненужных пересчетов и повысить производительность при работе с большими объемами данных. Reselect также упрощает кодирование сложных запросов к данным и делает его более читаемым и поддерживаемым.

Recompose - это набор функций высшего порядка (HOC), которые позволяют легко создавать и компоновать компоненты React. Он предлагает множество утилитарных функций, таких как withProps, withState, withHandlers и другие, которые помогают управлять состоянием компонента и передавать ему необходимые данные и функции. Recompose также обеспечивает оптимизацию рендеринга компонентов, путем использования shouldComponentUpdate, чтобы избежать ненужных перерисовок.

Использование Reselect и Recompose может быть полезно во множестве сценариев. Например, при работе с большими объемами данных в Redux-хранилище, Reselect позволяет эффективно выбирать и комбинировать данные для отображения на UI. Это особенно полезно при использовании сложных фильтров или сортировок. Recompose, с другой стороны, может быть полезен при создании компонентов с различными состояниями, обработчиками событий и передачей данных через пропсы.

В целом, Reselect и Recompose являются мощными инструментами, которые помогают улучшить производительность и управление состоянием в приложениях на React. Они предоставляют удобные функции и паттерны, которые делают кодирование более эффективным и поддерживаемым.

## Virtualization
- What is virtualization
- Understanding what virtualization is for
- Working with libraries for data virtualization
- Understanding and using virtualization
- Rendering Optimization

## useMemo, useCallback
- Differences between useMemo and useCallback
useMemo и useCallback - это два хука в React, которые используются для оптимизации производительности компонентов.

useMemo используется для мемоизации результатов вычислений. Он принимает два аргумента: функцию и массив зависимостей. Функция будет вызвана при каждом рендере компонента, но результат ее выполнения будет кэширован и возвращен только в случае изменения зависимостей. Это позволяет избежать повторных вычислений и улучшить производительность компонента.

Пример использования useMemo:

```jsx
const memoizedValue = useMemo(() => {
  // some expensive calculation
  return result;
}, [dependencies]);
```

useCallback используется для мемоизации колбэк-функций. Он принимает два аргумента: колбэк-функцию и массив зависимостей. Колбэк-функция будет мемоизирована и возвращена только в случае изменения зависимостей. Это полезно, когда передается колбэк-функция в дочерние компоненты, чтобы избежать их лишнего перерендера.

Пример использования useCallback:

```jsx
const memoizedCallback = useCallback(() => {
  // do something
}, [dependencies]);
```

В целом, использование useMemo и useCallback позволяет избежать ненужных вычислений и повторных рендеров компонентов, что способствует улучшению производительности приложения.

- Understanding what and when to use
useMemo и useCallback следует использовать в следующих случаях:

- Когда у вас есть вычисления, которые занимают много времени, и результаты этих вычислений не изменяются при каждом рендере компонента. В этом случае вы можете использовать useMemo для кэширования результатов вычислений и избежать их повторного выполнения при каждом рендере.

- Когда у вас есть колбэк-функции, которые передаются в дочерние компоненты и зависят от определенных значений или состояний. В этом случае вы можете использовать useCallback для мемоизации колбэк-функций и избежать их перерендера при изменении зависимостей.

- Когда у вас есть сложные вычисления или операции с большими объемами данных, которые происходят при каждом рендере компонента. В этом случае вы можете использовать useMemo или useCallback для оптимизации производительности и улучшения отзывчивости приложения.

В целом, использование useMemo и useCallback рекомендуется там, где есть потенциал для оптимизации производительности и улучшения отзывчивости компонентов. Однако не стоит злоупотреблять этими хуками, так как неправильное использование может привести к избыточной сложности кода и усложнению отладки.

- Optimizing the work of these hooks

Оптимизация работы хуков useMemo и useCallback может быть достигнута путем правильного выбора зависимостей.

- Для useMemo: Убедитесь, что вы указали все необходимые зависимости в массиве зависимостей. Если вы забыли указать зависимость, то useMemo не будет обновляться при изменении этой зависимости, что может привести к неправильным результатам. Однако, также не стоит указывать слишком много зависимостей, так как это может уменьшить эффективность кэширования.

- Для useCallback: Убедитесь, что вы указали все необходимые зависимости в массиве зависимостей. Если вы забыли указать зависимость, то useCallback не будет пересоздаваться при изменении этой зависимости, что может привести к неправильному поведению. Также, если у вас есть колбэк-функции, которые используются внутри других колбэк-функций, убедитесь, что вы правильно указали зависимости для каждого уровня вложенности.

Кроме того, вы можете использовать мемоизацию на более высоком уровне компонентов, чтобы избежать повторных рассчетов или перерендеров. Например, вы можете использовать useMemo или useCallback в родительском компоненте, чтобы кэшировать результаты вычислений или колбэк-функции и передавать их в дочерние компоненты.

- How to avoid excessive memoization
Чрезмерная мемоизация может быть проблемой, если не управлять ею правильно. Вот несколько способов избежать чрезмерной мемоизации:

1. Оцените, насколько часто вызывается функция: Если функция вызывается очень редко, то мемоизация может быть излишней. В таком случае, можно просто не использовать мемоизацию для этой функции.

2. Оцените потребление памяти: Если функция использует большое количество памяти для хранения кэшированных результатов, то может быть лучше ограничить мемоизацию или использовать другой подход для оптимизации.

3. Используйте дополнительные параметры: Если функция имеет дополнительные параметры, которые влияют на результат, то мемоизация может быть неэффективной. В таких случаях, можно добавить эти параметры в ключ кэша или использовать другой подход к оптимизации.

4. Используйте адекватный размер кэша: Если кэш слишком большой, то он может занимать слишком много памяти, а если слишком маленький, то мемоизация может быть неэффективной. Подберите размер кэша, который соответствует потребностям вашей функции.

5. Оцените сложность функции: Если функция имеет очень высокую сложность, то мемоизация может быть полезной. Однако, если функция имеет низкую сложность или выполняется очень быстро, то мемоизация может быть излишней.

В целом, важно оценивать потребности вашей функции и применять мемоизацию только там, где это действительно необходимо для оптимизации производительности.

# Lazy imports, dynamic imports
- Understanding the concept at a basic level
- What is lazy loading of components for?
- Explain how lazy loading works
- Ability to apply in practice

# Concurrent Mode and Suspense
### Understanding Concurrent Mode
Concurrent Mode - это новая функциональность, представленная в React 18, которая позволяет приложению более гибко и эффективно работать с асинхронными операциями и обеспечивает более отзывчивый пользовательский интерфейс.

Основная идея Concurrent Mode заключается в том, что React может приостанавливать и возобновлять работу рендеринга компонентов в зависимости от приоритетов и доступных ресурсов. Это позволяет React более эффективно распределить вычислительные ресурсы между различными частями приложения и предотвратить блокировку пользовательского интерфейса.

В Concurrent Mode была введена новая концепция - "suspense" (ожидание). Suspense позволяет компонентам ожидать асинхронных данных или других ресурсов без блокировки пользовательского интерфейса. Когда компонент ожидает данных, React может продолжать рендерить другие части приложения, которые не зависят от этих данных. Когда данные становятся доступными, React возобновляет работу рендеринга компонента и обновляет пользовательский интерфейс.

Concurrent Mode также предоставляет другие возможности, такие как "batching" (группировка) обновлений состояния и рендеринга компонентов, чтобы уменьшить количество операций обновления DOM и повысить производительность.
### Ability to explain  Concurrent Mode in your own words
### Good understanding of Concurrent
### Application of UI patterns Concurrent
Concurrent Mode позволяет применять различные UI-паттерны в приложении. Вот несколько примеров:

1. Lazy Loading (ленивая загрузка): Concurrent Mode позволяет откладывать загрузку компонентов, которые не отображаются на экране сразу. Это позволяет ускорить начальную загрузку приложения и уменьшить объем передаваемых данных.

2. Infinite Scrolling (бесконечная прокрутка): С помощью Suspense и Concurrent Mode можно реализовать бесконечную прокрутку, когда новые данные подгружаются автоматически по мере прокрутки страницы. Это позволяет создавать более плавный и отзывчивый пользовательский интерфейс.

3. Data Fetching (загрузка данных): С Suspense и Concurrent Mode можно организовать загрузку данных асинхронно и параллельно с рендерингом компонентов. Это позволяет улучшить производительность и отзывчивость приложения при работе с большими объемами данных.

4. Error Handling (обработка ошибок): Suspense вместе с Concurrent Mode предоставляет удобный способ обрабатывать ошибки загрузки данных или других асинхронных операций. Можно применять паттерны, такие как fallback UI (запасной интерфейс) или retry (повторная попытка), чтобы обеспечить более гладкую работу приложения в случае возникновения ошибок.

### Good understanding of the Concurrent API
Вот несколько примеров API, связанных с Concurrent Mode:

1. `Suspense`: Это компонент-обертка, который позволяет отложить загрузку компонента и отобразить запасное содержимое (fallback UI) во время ожидания. Пример использования:

```jsx
<Suspense fallback={<Spinner />}>
  <LazyComponent />
</Suspense>
```

2. `useTransition`: Этот хук позволяет добавить анимацию перехода между состояниями при загрузке или обновлении компонента. Пример использования:

```jsx
const [startTransition, isPending] = useTransition();

const handleClick = () => {
  startTransition(() => {
    // Асинхронная операция
  });
}

<button onClick={handleClick} disabled={isPending}>
  {isPending ? 'Loading...' : 'Load Data'}
</button>
```

3. `useDeferredValue`: Этот хук позволяет откладывать обновление значения состояния до следующего рендеринга, что может помочь избежать лишних перерисовок компонента. Пример использования:

```jsx
const deferredValue = useDeferredValue(value, {
  timeoutMs: 3000,
});

return <div>{deferredValue}</div>;
```

4. `startTransition`: Это функция, которая позволяет запустить асинхронную операцию с использованием Concurrent Mode и отложить обновление состояния до ее завершения. Пример использования:

```jsx
const [data, setData] = useState(null);

const handleClick = () => {
  startTransition(() => {
    fetchData().then((result) => {
      setData(result);
    });
  });
}

<button onClick={handleClick}>Load Data</button>
```

## Bundle optimization
### Lazy-loading
### Tree shaking
### Import cost
### Webpack optimization
### Chunks
### Caching;
### Webpack;
### Internal react tools
Оптимизация бандла JS и React - это процесс улучшения производительности и эффективности загрузки и работы JavaScript-кода веб-приложения, основанного на React.

Lazy-loading (ленивая загрузка) - это техника, которая позволяет загружать только те части кода, которые необходимы в данный момент, откладывая загрузку остальных частей до момента их фактического использования. Это позволяет ускорить начальную загрузку приложения и уменьшить объем передаваемых данных.

Tree shaking - это процесс удаления неиспользуемого кода (дерева) из бандла JavaScript. Это достигается путем статического анализа кода и определения, какие модули не используются, и затем исключения их из финального бандла. Это помогает сократить размер бандла и улучшить производительность приложения.

Import cost - это функциональность, предоставляемая некоторыми инструментами разработки, такими как VS Code, которая позволяет видеть стоимость импорта конкретного модуля в проекте. Она показывает информацию о размере модуля (в байтах) и время, необходимое для его загрузки. Это помогает разработчикам принимать решения об оптимизации импорта и улучшении производительности приложения.

Webpack optimization (оптимизация Webpack) - это процесс настройки и использования различных плагинов и настроек веб-пакета, чтобы улучшить производительность сборки и загрузки JavaScript-кода. Это может включать в себя минификацию кода, объединение модулей в более крупные части (chunks), кэширование данных и другие техники, которые помогают уменьшить размер бандла и ускорить его загрузку.

Chunks (части) - это фрагменты кода, на которые разделяется исходный код приложения веб-пакетом. Часто используется для ленивой загрузки, когда каждая часть кода загружается отдельно по мере необходимости. Оптимизация частей может включать в себя выделение общих зависимостей в общие части, чтобы уменьшить размер бандла и улучшить его загрузку.

Caching (кэширование) - это процесс сохранения данных или файлов в памяти или на диске для повторного использования в будущем. В контексте оптимизации бандла JS и React, кэширование может использоваться для хранения бандлов и других ресурсов на стороне клиента, чтобы ускорить загрузку приложения при повторном посещении.

Webpack - это инструмент сборки JavaScript, который позволяет объединять и оптимизировать код приложения в бандлы. Он также имеет множество плагинов и настроек, которые помогают улучшить производительность и оптимизацию загрузки.

Internal react tools (внутренние инструменты React) - это инструменты, предоставляемые командой разработчиков React, которые помогают оптимизировать и улучшить производительность React-приложений. Это может включать в себя инструменты для анализа производительности, поиска и исправления узких мест, а также рекомендации по оптимизации и лучшие практики использования React.

## useState/useReducer/useContext
### Explain in your own words how useState and useReducer work;
Хуки useState, useReducer и useContext являются основными хуками в React, которые позволяют управлять состоянием компонентов и передавать данные между компонентами.

1. useState:
- Применяется для управления состоянием функциональных компонентов.
- Принимает начальное значение состояния и возвращает массив с двумя элементами: текущим значением состояния и функцией для его обновления.
- Может использоваться несколько раз внутри одного компонента для создания и управления несколькими состояниями.

Пример использования useState:

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```

2. useReducer:
- Применяется для управления состоянием компонентов, особенно когда состояние имеет сложную структуру или нужно выполнить более сложные операции при обновлении состояния.
- Принимает редюсер (функцию, которая принимает текущее состояние и действие, и возвращает новое состояние) и начальное значение состояния.
- Возвращает текущее состояние и диспетчер (функцию, которая позволяет изменять состояние).

Пример использования useReducer:

```jsx
import React, { useReducer } from 'react';

const initialState = {
  count: 0,
};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  const increment = () => {
    dispatch({ type: 'increment' });
  };

  const decrement = () => {
    dispatch({ type: 'decrement' });
  };

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}
```

3. useContext:
- Применяется для передачи данных через иерархию компонентов без явной передачи пропсов.
- Принимает контекст (объект, созданный с помощью createContext) и возвращает текущее значение контекста.
- Компоненты, которым необходим доступ к значению контекста, должны быть обернуты в соответствующий провайдер (компонент, созданный с помощью Context.Provider).

Пример использования useContext:

```jsx
import React, { useContext } from 'react';

const MyContext = React.createContext();

function ParentComponent() {
  return (
    <MyContext.Provider value="Hello, world!">
      <ChildComponent />
    </MyContext.Provider>
  );
}

function ChildComponent() {
  const value = useContext(MyContext);

  return <p>{value}</p>;
}
```
### What parameters are accepted
### Ability to work with basic hooks
### Good knowledge of the topic
### Understand when to use this or that hook

## useEffect, useLayoutEffect vs useEffect
### What is useEffect, useLayoutEffect;
### How to unsubscribe from changes;
### Understand what lifecycle methods this hook can replace.
Хуки useEffect и useLayoutEffect в React предоставляют возможность выполнять побочные эффекты в функциональных компонентах. Они позволяют выполнять определенный код при каждом рендеринге компонента или при изменении определенных зависимостей.

Отличие между useEffect и useLayoutEffect заключается во времени, когда они вызываются во время жизненного цикла компонента. useEffect вызывается после того, как браузер отрисовал изменения на экране. Таким образом, он не блокирует процесс отрисовки пользовательского интерфейса и рекомендуется использовать его по умолчанию. С другой стороны, useLayoutEffect вызывается сразу после того, как React выполнит все изменения в виртуальном DOM и перед отрисовкой настоящего DOM. Поэтому, если код в useLayoutEffect блокирует отрисовку, пользователь может заметить задержку или "мерцание" интерфейса.

Как для useEffect, так и для useLayoutEffect существуют методы жизненного цикла классовых компонентов, которые они заменяют. useEffect заменяет методы componentDidMount, componentDidUpdate и componentWillUnmount. useLayoutEffect заменяет методы componentDidMount и componentDidUpdate, но вызывается синхронно после каждого изменения виртуального DOM.

Для отписки от изменений, которые выполняются в useEffect или useLayoutEffect, необходимо вернуть функцию из этих хуков. Эта функция будет вызвана перед следующим вызовом эффекта или перед удалением компонента. Возвращаемая функция может содержать код для отмены или очистки ресурсов, например, отписки от событий или отмены запросов к серверу.

Хук useEffect в React может заменить следующие методы жизненного цикла:

- componentDidMount: вызывается после монтирования компонента в DOM. В хуке useEffect можно выполнять действия, которые раньше выполнялись в componentDidMount.

- componentDidUpdate: вызывается после обновления компонента. В хуке useEffect можно проверять изменение пропсов или состояния и выполнять соответствующие действия.

- componentWillUnmount: вызывается перед размонтированием компонента. В хуке useEffect можно выполнять очистку ресурсов или отписываться от событий.

Также, хук useEffect можно использовать для эмуляции других методов жизненного цикла, таких как shouldComponentUpdate или componentDidCatch.

 Хук useLayoutEffect заменяет методы жизненного цикла componentDidMount и componentDidUpdate. 

Он вызывается сразу после того, как браузер отрисовал изменения на странице, но перед тем, как эти изменения станут видимыми для пользователя. Это позволяет использовать хук useLayoutEffect для выполнения действий, которые требуют информации о размерах или позиции элементов на странице.

В отличие от хука useEffect, который выполняется асинхронно, хук useLayoutEffect блокирует браузер до тех пор, пока не завершатся все его эффекты. Поэтому, если вам необходимо внести изменения в DOM, которые должны быть видны пользователю сразу же после обновления компонента, то лучше использовать хук useLayoutEffect.

## Custom hooks
### Understanding the concept of custom hooks
### Ability to write simple custom hooks
### Writing complex hooks

```jsx
import { useState } from 'react';

function useCounter(initialValue) {
  const [count, setCount] = useState(initialValue);

  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return {
    count,
    increment,
    decrement
  };
}

function Counter() {
  const { count, increment, decrement } = useCounter(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}
```


```javascript
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    async function fetchData() {
      try {
        const response = await fetch(url);
        const json = await response.json();
        setData(json);
        setLoading(false);
      } catch (error) {
        setError(error);
        setLoading(false);
      }
    }

    fetchData();
  }, [url]);

  return { data, loading, error };
}

function UserList() {
  const { data, loading, error } = useFetch('https://api.example.com/users');

  if (loading) {
    return <p>Loading...</p>;
  }

  if (error) {
    return <p>Error: {error.message}</p>;
  }

  return (
    <ul>
      {data.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

## Understanding what useRef is for
### useImperativeHandle
### useLayoutEffect 
### useDebugValue
### Work with thirdparty libraries Note: e.g. reactuse

1. Пример использования хука useRef:

```javascript
import React, { useRef } from 'react';

const ExampleComponent = () => {
  const inputRef = useRef(null);

  const handleButtonClick = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleButtonClick}>Focus Input</button>
    </div>
  );
};
```

В этом примере мы используем useRef для создания ref-ссылки на input элемент. Затем мы передаем эту ссылку в атрибут ref элемента и можем получить доступ к нему через свойство current объекта, возвращаемого useRef. В функции handleButtonClick мы вызываем метод focus() для установки фокуса на ввод.

2. Пример использования хука useImperativeHandle:

```javascript
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const ChildComponent = forwardRef((props, ref) => {
  const childRef = useRef();

  useImperativeHandle(ref, () => ({
    showMessage: () => {
      console.log('Hello from ChildComponent');
    }
  }));

  return <div>Child Component</div>;
});

const ParentComponent = () => {
  const childRef = useRef();

  const handleClick = () => {
    childRef.current.showMessage();
  };

  return (
    <div>
      <ChildComponent ref={childRef} />
      <button onClick={handleClick}>Show Message</button>
    </div>
  );
};
```

В этом примере у нас есть дочерний компонент ChildComponent, который принимает реф через forwardRef. Внутри ChildComponent мы используем useRef для создания локальной переменной childRef. Затем мы используем useImperativeHandle, чтобы определить, что должно быть доступно через переданный реф. В данном случае мы определяем метод showMessage, который выводит сообщение в консоль.

В родительском компоненте ParentComponent мы создаем реф childRef с помощью useRef и передаем его в ChildComponent. Затем мы обрабатываем клик по кнопке и вызываем метод showMessage через childRef.

3. Пример использования хука useDebugValue:

```javascript
import React, { useState, useDebugValue } from 'react';

const Counter = () => {
  const [count, setCount] = useState(0);

  useDebugValue(count > 5 ? 'High Count' : 'Low Count');

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};
```

В этом примере у нас есть компонент Counter, который использует хук useState для создания состояния count и функции setCount для его обновления. Мы также используем хук useDebugValue для отображения пользовательской метаинформации о значении count в инструментах разработчика. В данном случае, если count больше 5, будет отображаться "High Count", иначе - "Low Count".