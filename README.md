# Шаблоны проектирования(TypeScript)

## Одиночка (Singleton)
Обеспечивает создание единственного экземпляра класса.
- Плюсы: Гарантия уникальности.
- Минусы: Усложнение тестирования.
- Пример использования:
```
class Singleton {
    private static instance: Singleton;

    private constructor() {}

    public static getInstance(): Singleton {
        if (!Singleton.instance) {
            Singleton.instance = new Singleton();
        }
        return Singleton.instance;
    }
}
```

## Фабричный метод (Factory Method)
Определяет интерфейс для создания объектов.
- Плюсы: Гибкость в добавлении новых классов.
- Минусы: Увеличение количества классов.
- Пример использования:
```
abstract class Creator {
    abstract factoryMethod(): Product;
}

class ConcreteCreator extends Creator {
    factoryMethod(): Product {
        return new Product();
    }
}

class Product {}
```

## Строитель (Builder)
Отделяет конструирование сложного объекта.
- Плюсы: Упрощение создания объектов.
- Минусы: Сложность кода.
- Пример использования:
```
class Car {
    wheels: number;
}

class CarBuilder {
    private car: Car;

    constructor() {
        this.car = new Car();
    }

    setWheels(wheels: number) {
        this.car.wheels = wheels;
    }

    build(): Car {
        return this.car;
    }
}

```
## Прототип (Prototype)
Создает объекты на основе существующего экземпляра.
- Плюсы: Экономия ресурсов.
- Минусы: Сложность реализации.
- Пример использования:

```
class Prototype {
    clone(): Prototype {
        return Object.assign(Object.create(Object.getPrototypeOf(this)), this);
    }
}

```
## Адаптер (Adapter)
Позволяет объектам с несовместимыми интерфейсами работать вместе.
- Плюсы: Интеграция старая и новая.
- Минусы: Увеличение сложности.
- Пример использования:
```
class Target {
    request(): string {
        return "Target request.";
    }
}

class Adapter extends Target {
    specificRequest(): string {
        return "Adapter response.";
    }
}
```

## Декоратор (Decorator)
Добавляет новое поведение к объекту динамически.
- Плюсы: Гибкость.
- Минусы: Сложность отслеживания.
- Пример использования:

```
class Component {
    operation(): string {
        return "Base operation";
    }
}

class Decorator extends Component {
    operation(): string {
        return `Decorated ${super.operation()}`;
    }
}
```

## Фасад (Facade)
Предоставляет упрощенный интерфейс.
- Плюсы: Упрощение взаимодействия.
- Минусы: Скрытие функционала.
- Пример использования:
```
class Facade {
    operation(): string {
        return "Simple interface to complex system.";
    }
}
```

## Компоновщик (Composite)
Создает иерархию объектов.
- Плюсы: Упрощение кода.
- Минусы: Усложнение структуры.
- Пример использования:
```
class Composite {
    private children: Composite[] = [];

    add(child: Composite) {
        this.children.push(child);
    }
}
```

## Заместитель (Proxy)
Замещает другой объект.
- Плюсы: Контроль доступа.
- Минусы: Сложность тестирования.
- Пример использования:

```
class RealSubject {
    request(): string {
        return "Real subject.";
    }
}

class Proxy {
    private realSubject: RealSubject;

    constructor() {
        this.realSubject = new RealSubject();
    }

    request(): string {
        return this.realSubject.request();
    }
}
```

## Стратегия (Strategy)
Инкапсулирует семейство алгоритмов.
- Плюсы: Гибкость.
- Минусы: Увеличение сложности.
- Пример использования:
```
interface Strategy {
    execute(): string;
}

class ConcreteStrategyA implements Strategy {
    execute(): string {
        return "Strategy A";
    }
}
```

## Команда (Command)
Инкапсулирует запрос как объект.
- Плюсы: Упрощение управления командами.
- Минусы: Сложность кода.
- Пример использования:
```
interface Command {
    execute(): void;
}

class ConcreteCommand implements Command {
    execute(): void {
        console.log("Command executed.");
    }
}
```

## Наблюдатель (Observer)
Определяет зависимость «один ко многим».
- Плюсы: Автоматическое обновление.
- Минусы: Управление зависимостями.
- Пример использования:
```
class Subject {

    private observers: Observer[] = [];

    attach(observer: Observer) {
        this.observers.push(observer);
    }
}

interface Observer {
    update(): void;
}
```

## Состояние (State)
Изменяет поведение в зависимости от состояния.
- Плюсы: Упрощение кода.
- Минусы: Управление состояниями.
- Пример использования:
```
interface State {
    handle(): string;
}

class ConcreteStateA implements State {
    handle(): string {
        return "Handling state A.";
    }
}
```

## Шаблонный метод (Template Method)
Определяет скелет алгоритма.
- Плюсы: Общая структура.
- Минусы: Жесткость структуры.
- Пример использования:

```
abstract class AbstractClass {
    templateMethod(): void {
        this.step1();
        this.step2();
    }

    abstract step1(): void;
    abstract step2(): void;
}
```

## Итератор (Iterator)
Позволяет перебрать составной объект.
- Плюсы: Упрощение работы с коллекциями.
- Минусы: Увеличение классов.
- Пример использования:
```
class Iterator {
    private items: any[];
    private index: number = 0;

    constructor(items: any[]) {
        this.items = items;
    }

    next(): any {
        return this.index < this.items.length 
            ? this.items[this.index++] 
            : null;
    }

    hasNext(): boolean {
        return this.index < this.items.length;
    }
}
```
