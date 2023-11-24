## Наследование в JS

В плане наследования JavaScript работает лишь с одной сущностью: объектами. Каждый объект имеет внутреннюю ссылку на другой объект, называемый его прототипом. У объекта-прототипа также есть свой собственный прототип и так далее до тех пор, пока цепочка не завершится объектом, у которого свойство `prototype` равно `null`. По определению, `null` не имеет прототипа и является завершающим звеном в **цепочке прототипов**.

Объекты в JavaScript — динамические "контейнеры", наполненные свойствами (называемыми **собственными свойствами**). Каждый объект содержит ссылку на свой объект-прототип. При попытке получить доступ к какому-либо свойству объекта, свойство вначале ищется в самом объекте, затем в прототипе объекта, после чего в прототипе прототипа, и так далее. Поиск ведётся до тех пор, пока не найдено свойство с совпадающим именем или не достигнут конец цепочки прототипов.

**property shadowing** — затенение свойств объекта. Механизм, при котором объект, у которого есть собственное свойство с тем же именем, как и у его объекта-прототипа, при обращении к этому свойству возвращает собственное свойство, а не свойство объекта-прототипа. 
Тот же механизм для унаследованных функций называется **method overriding**.

При добавлении к объекту нового свойства, создаётся новое собственное свойство (own property). Единственным исключением из этого правила являются наследуемые свойства, имеющие getter или setter.

## Проверка собственного свойства

`Object.prototype.hasOwnProperty()` — единственная существующая в JavaScript возможность работать со свойствами, не затрагивая цепочку прототипов.

## Способы создания объектов

### С помощью литералов
`let obj = { a: 1 }`
Созданный объект `o` имеет `Object.prototype` в качестве своего `[[Prototype]]`
у `o` нет собственного свойства `hasOwnProperty`
`hasOwnProperty` — это собственное свойство `Object.prototype`.
Таким образом `o` наследует `hasOwnProperty` от `Object.prototype`
`Object.prototype` в качестве прототипа имеет `null`.
`o ---> Object.prototype ---> null`

`let arr = [1, 2, 3]`
Массивы наследуются от `Array.prototype`
(у которого есть такие методы, как `indexOf`, `forEach` и т.п.).
Цепочка прототипов при этом выглядит так:
`a ---> Array.prototype ---> Object.prototype ---> null`

```
function f() {
  return 2;
}
// Функции наследуются от Function.prototype
// (у которого есть такие методы, как call, bind и т.п.):
// f ---> Function.prototype ---> Object.prototype ---> null
```

### С помощью конструктора
'''
function Car(model, power) {
  this.model = model
  this.power = power
};

Car.prototype.start = function() {
  console.log(`${this.model} is started`)
};

const ford = new Car('Ford', 150);
'''

### С помощью класса
```
class Car {
  constructor(model, power) {
    this.model = model
    this.power = power
  }
  start() {
    console.log(`${this.model} is started`)
  }
}

const ford = new Car('Ford', 150);
```

### С помощью Object.create
```
var a = { a: 1 };
// a ---> Object.prototype ---> null

var b = Object.create(a);
// b ---> a ---> Object.prototype ---> null
console.log(b.a); // 1 (унаследовано)

var c = Object.create(b);
// c ---> b ---> a ---> Object.prototype ---> null

var d = Object.create(null);
// d ---> null
console.log(d.hasOwnProperty);
// undefined, т.к. 'd' не наследуется от Object.prototype
```

### С помощью Object.assign

### С помощью new Object()

### С помощью Object.fromEntries()
```
const entries = new Map([
  ['foo', 'bar'],
  ['baz', 42],
]);

const obj = Object.fromEntries(entries);

console.log(obj);
// Expected output: Object { foo: "bar", baz: 42 }
```


### `Object.prototype` vs `__proto__`

`__proto__` — это свойство любого объекта в JS, которое является ссылкой на свойство `prototype` функции-конструктора. 
Свойство `__proto__` — исторически обусловленный геттер/сеттер для `[[Prototype]]`
Свойство `__proto__` немного устарело, оно существует по историческим причинам. Современный JavaScript предполагает, что мы должны использовать функции `Object.getPrototypeOf/Object.setPrototypeOf` вместо того, чтобы получать/устанавливать прототип. Мы также рассмотрим эти функции позже.

`prototype` — это свойство функции-конструктора, которое хранит поведение наследуемое потомками (которое хранит в себе интерфейс предка, к которому через ссылку` __proto__` будет обращаться потомок). По факту специализированное хранилище для поведения всех экземпляров, созданных функцией-конструктором

У каждой функции в JS есть свойство `prototype`, но только у функций! Класс в JS — это синтаксический сахар вокруг функции-конструктора, следовательно, у классов тоже есть свойство prototype.

Потомок связан с родителем свойством `__proto__`, которое указывает на свойство prototype родителя, в котором в свою очередь хранится своя ссылка `__proto__`, указывающая на его родителя. Такая связь называется цепочка прототипов, а сам механизм такого наследования называется прототипное наследование


### До появления классов
```
function User(login, email) {
  this.login = login;
  this.email = email;
}

User.prototype.changeEmail = function (newEmail) {
  this.email = newEmail;
};

function Admin(login, email, team) {
  User.call(this, login, email);
  this.team = team;
}

Admin.prototype = Object.create(User.prototype);
Admin.prototype.constructor = Admin;

Admin.prototype.changeTeam = function (newTeam) {
  this.team = newTeam;
};
```

## Дескрипторы
У каждого из свойств объекта, кроме значения, есть ещё три флага конфигурации, которые могут принимать значения `true` или `false`. Эти флаги называются дескрипторами:

`writable` — доступно ли свойство для записи;
`enumerable` — является ли свойство видимым при перечислениях (например, в цикле `for..in`);
`configurable` — доступно ли свойство для переконфигурирования.
Когда мы создаём свойство объекта «обычным способом», эти три флага устанавливаются в значение `true`.

Для изменения значений дескрипторов применяется статический метод `Object.defineProperty()`, а для чтения значений — `Object.getOwnPropertyDescriptors()`.

Другими словами, дескрипторы — это пары ключ-значение, которые описывают поведение свойства объекта при выполнении операций над ним (например, чтения или записи).

### Пример 
```
const laptop = {}

Object.defineProperty(laptop, 'os', {
  value: 'MacOS',
  writable: false,
  enumerable: true,
  configurable: true
})
```