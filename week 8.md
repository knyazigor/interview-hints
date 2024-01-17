## React devtools, redux devtools
- React/redux devtools usage	
- Ability to work with React devtools, Redux devtools at a good level, saving variables
- Ability to profile components
- Optimize component performance

## Jest, Enzyme and other tools
- What are jest and enzyme for
1. Jest:
   - Jest - это фреймворк для тестирования JavaScript, который предоставляет широкий набор функций и утилит для тестирования кода.
   - Он широко используется для тестирования компонентов React, но также может быть использован для тестирования других типов JavaScript-кода.
   - Jest обеспечивает функции для запуска тестов, создания тестовых случаев, создания утверждений (assertions), имитации (mocking) и многое другое.
   - Он также обладает встроенной поддержкой для снимков (snapshots), что позволяет легко проверять, не изменилось ли отображение компонента.

2. Enzyme:
   - Enzyme - это библиотека, разработанная Airbnb, которая предоставляет удобные функции для тестирования компонентов React.
   - Она призвана упростить манипуляцию с компонентами React, что делает тестирование более простым и эффективным.
   - Enzyme предлагает широкий спектр функций, таких как поиск, манипуляция и симуляция событий в компонентах.
   - Она также обеспечивает удобные методы для проверки состояния и свойств компонентов, а также для сравнения отрисовки компонентов с ожидаемыми результатами.
- Basic understanding of writing tests
Для базового тестирования компонентов React с использованием Jest и Enzyme, следуйте этим шагам:

1. Установите необходимые зависимости:
   - Установите Jest и Enzyme, выполнив команду npm install --save-dev jest enzyme enzyme-adapter-react-16.

2. Настройте Enzyme:
   - Создайте файл setupTests.js в корневой папке вашего проекта.
   - В файле setupTests.js добавьте следующий код:
```js
import Enzyme from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';

Enzyme.configure({ adapter: new Adapter() });
```

3. Напишите тестовый случай:
   - Создайте файл с расширением .test.js или .spec.js, например MyComponent.test.js.
   - В файле теста добавьте код для импорта необходимых зависимостей и компонента, который вы хотите протестировать.
   - Определите тестовый случай с помощью функции test или it из Jest.
   - В тестовом случае используйте Enzyme для манипуляции с компонентом и проверки ожидаемых результатов.
   - Пример базового тестового случая:
```js
import React from 'react';
import { shallow } from 'enzyme';
import MyComponent from './MyComponent';

test('renders MyComponent correctly', () => {
  const wrapper = shallow(<MyComponent />);
  expect(wrapper.find('h1').text()).toEqual('Hello, World!');
});
```

- Good understanding of how to test various entities: components, utilities, HOCs, modals;
- Basic application of test patterns 
- Application of test patterns
- Testing pyramid
- Working with TTD approach is possible"

## Snapshot testing, components testing	
### Basic understanding of shapshot testing, why it can be used
Snapshot тестирование в React - это метод тестирования, который позволяет создавать и сравнивать "снимки" (snapshots) компонентов React. Снимок представляет собой сериализованное представление компонента в виде HTML или JSON.

Пример использования snapshot тестирования в React:

1. Установите необходимые зависимости:
```bash
npm install --save-dev react-test-renderer
```

2. Создайте тестовый файл для компонента (например, `Button.test.js`):
```javascript
import React from 'react';
import renderer from 'react-test-renderer';
import Button from './Button';

test('Button component renders correctly', () => {
  const component = renderer.create(<Button label="Click me" />);
  const tree = component.toJSON();
  expect(tree).toMatchSnapshot();
});
```

3. Запустите тесты:
```bash
npm test
```

4. Первый запуск теста создаст снимок компонента. Все последующие запуски будут сравнивать новый снимок с сохраненным. Если снимки не совпадают, тест будет считаться проваленным.

Snapshot тестирование особенно полезно для проверки изменений визуального представления компонентов при изменении кода или зависимостей.

- Working experience with snapshot testing

## e2e
### Understanding what e2e tests are for
### Difference from unit, integration tests
Unit-тесты:
- Написаны для тестирования отдельных функций, модулей или компонентов программы.
- Целью unit-тестов является проверка правильности работы отдельных частей программы независимо от остального кода.
- Unit-тесты обычно выполняются быстро и изолированно, без взаимодействия с внешними зависимостями.
- Используются моки и заглушки для замены зависимостей и эмуляции окружения.

Интеграционные тесты:
- Написаны для проверки взаимодействия и корректной работы между различными компонентами, модулями или сервисами программы.
- Целью интеграционных тестов является обнаружение возможных проблем взаимодействия и соответствия между компонентами.
- Интеграционные тесты могут включать в себя реальные внешние зависимости и внешние сервисы.
- Обычно требуют больше времени на выполнение, чем unit-тесты.

E2E-тесты (End-to-End):
- Написаны для проверки полной функциональности программы с точки зрения пользователя.
- Целью e2e-тестов является моделирование и проверка реальных сценариев использования программы.
- E2E-тесты выполняются на реальном окружении и взаимодействуют с программой так же, как это делал бы пользователь.
- E2E-тесты требуют настройки и запуска реального приложения или симулятора, и обычно выполняются медленнее, чем другие типы тестов.
### Used one of the libraries / frameworks for writing e2e tests Note: e.g. Cypress
### Write e2e tests on a regular basis in projects

## Custom hooks
### Understanding the concept of custom hooks
Custom hooks в React используются для повторного использования логики состояния и поведения между компонентами. Они позволяют абстрагировать и изолировать определенную функциональность, чтобы ее можно было легко использовать в разных компонентах.

Вот несколько случаев, когда полезно использовать custom hooks:

1. Логика состояния: Если у вас есть определенная логика состояния, которую вы хотите использовать в нескольких компонентах, вы можете вынести ее в custom hook. Например, вы можете создать custom hook для управления формой или для работы с API.

2. Совместное использование поведения: Если у вас есть поведение, которое используется в нескольких компонентах, вы можете создать custom hook для его обработки. Например, вы можете создать custom hook для обработки клика вне элемента или для выполнения анимации.

3. Абстрагирование сложной логики: Если у вас есть сложная логика, которую вы хотите скрыть или упростить внутри компонента, вы можете создать custom hook для абстрагирования этой логики и предоставления более простого интерфейса для использования.

Преимущества использования custom hooks включают повышение переиспользуемости кода, улучшение читаемости и поддерживаемости компонентов, а также возможность тестирования логики в изоляции.

Важно помнить, что custom hooks должны начинаться с префикса "use" (например, useCustomHook), чтобы следовать правилам хуков React и обеспечить их корректное использование.
### Ability to write simple custom hooks	
### Writing complex hooks

## Other hooks
### Understanding what useRef is for
useRef - это хук, предоставляемый React, который позволяет сохранять и получать мутируемое значение, которое будет сохранять свое состояние между рендерами компонента. 

Основное назначение useRef в React состоит в сохранении и получении ссылки на DOM-элемент или другое значение, которое нужно сохранить внутри компонента. В отличие от состояния компонента, изменение значения useRef не вызывает повторный рендер компонента.

Вот несколько примеров использования useRef:

1. Сохранение ссылки на DOM-элемент:
```jsx
import React, { useRef } from 'react';

function ExampleComponent() {
  const inputRef = useRef();

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Фокус на поле ввода</button>
    </div>
  );
}
```

2. Сохранение значения, не вызывающего повторный рендер:
```jsx
import React, { useRef, useEffect } from 'react';

function ExampleComponent() {
  const renderCountRef = useRef(0);

  useEffect(() => {
    renderCountRef.current += 1;
  });

  return (
    <div>
      <p>Количество рендеров: {renderCountRef.current}</p>
    </div>
  );
}
```

В этом примере мы используем useRef, чтобы сохранить количество рендеров компонента, которое будет увеличиваться каждый раз при рендере. Изменение значения useRef не вызывает повторный рендер компонента, поэтому мы можем сохранять и обновлять значение без влияния на поведение компонента.
### useImperativeHandle;
Хук useImperativeHandle используется в React для определения пользовательского интерфейса, который будет предоставлен родительскому компоненту при использовании ref. Он позволяет компоненту настроить, какие значения или функции будут доступны для родительского компонента через ref.

Основные случаи использования useImperativeHandle включают:

1. Сокрытие деталей реализации: Вы можете использовать useImperativeHandle, чтобы определить, какие значения или функции компонента будут доступны через ref, скрывая некоторые внутренние детали реализации от родительского компонента. Таким образом, вы можете предоставить только те методы или данные, которые необходимы для взаимодействия с компонентом.

2. Предоставление API родительскому компоненту: Вы можете использовать useImperativeHandle, чтобы определить пользовательскую API, которая будет доступна родительскому компоненту через ref. Вместо предоставления полного доступа к внутреннему состоянию компонента, вы можете определить специфические методы или данные, которые родительский компонент может использовать для взаимодействия с дочерним компонентом.

Вот пример использования useImperativeHandle:
```jsx
import React, { forwardRef, useImperativeHandle, useRef } from 'react';

const ChildComponent = forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focusInput: () => {
      inputRef.current.focus();
    },
    getValue: () => {
      return inputRef.current.value;
    }
  }));

  return <input ref={inputRef} />;
});

// В родительском компоненте
const ParentComponent = () => {
  const childRef = useRef();

  const handleButtonClick = () => {
    childRef.current.focusInput();
    const value = childRef.current.getValue();
    console.log(value);
  };

  return (
    <div>
      <ChildComponent ref={childRef} />
      <button onClick={handleButtonClick}>Get Value</button>
    </div>
  );
};
```

В этом примере ChildComponent определяет inputRef с помощью хука useRef и использует useImperativeHandle, чтобы предоставить два метода (focusInput и getValue) родительскому компоненту через ref. В родительском компоненте ParentComponent мы используем childRef для вызова методов focusInput и getValue через кнопку.
### useLayoutEffect; 
Вызывает до отрисовки компонента
### useDebugValue;
useDebugValue - это хук, предоставляемый React, который позволяет добавлять дополнительную отладочную информацию к пользовательским хукам. 

Он обычно используется для отображения значений хуков в инструментах разработчика или в других отладочных целях. useDebugValue принимает значение и необязательную функцию форматирования и используется внутри пользовательских хуков перед возвратом значения.

Например, вы можете использовать useDebugValue для отображения названия компонента или другой полезной информации, когда вы анализируете состояние и поведение вашего приложения в инструментах разработчика React.

```jsx
import React, { useState, useDebugValue } from 'react';

function useCustomHook() {
  const [count, setCount] = useState(0);

  // Добавляем отладочное значение "Количество"
  useDebugValue(count, (count) => `Количество: ${count}`);

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return { count, increment };
}

function ExampleComponent() {
  const { count, increment } = useCustomHook();

  return (
    <div>
      <p>{count}</p>
      <button onClick={increment}>Увеличить</button>
    </div>
  );
}

export default ExampleComponent;
```
В этом примере мы создаем пользовательский хук useCustomHook, который использует useState для создания счетчика count. Мы также вызываем useDebugValue, чтобы добавить отладочную информацию о значении count.

Когда вы открываете инструменты разработчика React и просматриваете компонент ExampleComponent, вы увидите отладочную информацию "Количество: значение счетчика". Это позволяет вам легко отслеживать значение хука при отладке вашего приложения.
### Work with thirdparty libraries Note: e.g. reactuse