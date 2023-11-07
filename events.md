## Events

*Событие* сигнал от бразуера о том что что-то произошло. Все DOM-узлы подают такие сигналы.
Примеры: 
- события мыши: `click`, `mouseover` \ `mouseout`, `mousedown`, `mouseup`
- события формы: `submit`, `focus`
- события клавиатуры: `keydown`, `keyup`
- события документа: `DOMContentLoaded`
- события CSS: `transitionend`

### Обработчики события
- атрибут HTML-элемента
  `<input value="Нажми меня" onclick="alert('Клик!')" type="button">`
- свойство DOM-объекта
  ``` 
  elem.onclick = function() {
      alert('Спасибо');
    };
  ```
- `addEventListener()`
  можно назначить несколько обработчиков на одно событие
  `element.addEventListener(event, handler, [options]);`
  `options`:
    -- `once`: если `true`, тогда обработчик будет автоматически удалён после выполнения
    -- `capture`: фаза, на которой должен сработать обработчик. Так исторически сложилось, что `options` может быть `false/true`, это то же самое, что `{capture: false/true}`
    -- `passive`: если `true`, то указывает, что обработчик никогда не вызовет `preventDefault()`

`removeEventListener()` для удаления обработчика, нужно передать ссылку на функцию.

### Погружение и всплытие

Три фазы:
1. Фаза погружения (capturing phase) – событие сначала идёт сверху вниз
2. Фаза цели (target phase) – событие достигло целевого(исходного) элемента
3. Фаза всплытия (bubbling stage) – событие начинает всплывать

При наступлении события – самый глубоко вложенный элемент, на котором оно произошло, помечается как «*целевой*» (`event.target`).

Затем событие сначала двигается вниз от корня документа к `event.target`, по пути вызывая обработчики, поставленные через `addEventListener(...., true)`.
Далее обработчики вызываются на *целевом элементе*.
Далее событие двигается от `event.target` вверх к корню документа, по пути вызывая обработчики, поставленные через `on<event>` и `addEventListener` без третьего аргумента или с третьим аргументом равным `false`.
Каждый обработчик имеет доступ к свойствам события `event`:

`event.target` – самый глубокий элемент, на котором произошло событие.
`event.currentTarget` (=`this`) – элемент, на котором в данный момент сработал обработчик (тот, на котором «висит» конкретный обработчик)
`event.eventPhase` – на какой фазе он сработал (погружение=1, фаза цели=2, всплытие=3).
Любой обработчик может остановить событие вызовом `event.stopPropagation()`



