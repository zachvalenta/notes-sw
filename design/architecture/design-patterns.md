# ⛩️

## 参考

📚
* Conery ch. 11/12
* Gamma design patterns
* Nystrom http://gameprogrammingpatterns.com/contents.html

## 进步

* https://neetcode.io/courses/lessons/8-design-patterns
* in Elixir https://youtube.com/watch?v=agkXUp0hCW8
* https://www.youtube.com/watch?v=tAuRQs_d9F8

* _25_: factory
* _24_: builder for EDI at Capp
* _23_: 📙 Evans domain-driven

> A key insight is that many patterns solve similar problems in different contexts. For example, both Strategy and Command encapsulate behavior, but Command adds undo/logging capabilities. Similarly, both Decorator and Chain of Responsibility compose behavior, but Chain focuses on request handling while Decorator is more general.

* fanout https://www.better-simple.com/django/2023/12/06/fanout-pattern-explained/ https://news.ycombinator.com/item?id=43105028
* the big ball of mud https://news.ycombinator.com/item?id=35481309
* _strangler fig_: you run the old code and new code live, in production, side-by-side, checking that the new code behaves exactly the same as the old code. Once you are confident it does, you retire the old code https://www.kosli.com/blog/how-to-strangle-old-code-using-python-decorators/ https://news.ycombinator.com/item?id=41423421

> Some practices are the best when applied to a rewrite, but the worst when you’re still exploring. https://thorstenball.com/blog/2022/05/17/professional-programming-the-first-10-years/

https://developers.soundcloud.com/blog/end-of-the-strangler

* _strangler fig_: https://developers.soundcloud.com/blog/end-of-the-strangler
* _proxy_ https://rednafi.github.io/digressions/python/2020/06/16/python-proxy-pattern.html

as red flag https://news.ycombinator.com/item?id=30675182

* entity component https://akkartik.name/post/programming-2024
* _design patterns_: ❓ inherently OOP? [Conery 236]
* _bridge_: allows you to update abstraction w/breaking impl i.e. yet another layer of abstraction [Conery 250]
* _decorator_: wrapper [Conery 254]
* _facade_: wrapper [Conery 255]
* _flyweight_: storage for other obj to use, cuts down on memory usage 📙 Conery [257] Evans [100]
* can use when shared obj is immutable, shared memory, when you really need to save space 📙 Evans [101]
* _mediator_: obj passing msg btw two other obj [Conery 261]
* _observer_: obj that listens to events from another obj
* _strategy_: pass algo at runtime i.e. `charge(normal_price)` or `charge(half_off)`
* _template method_: https://startcodingnow.com/template-method-design-pattern
> Defines algorithm skeleton in base class. Lets subclasses override specific steps without changing algorithm structure
* _visitor_: https://martinheinz.dev/blog/90

* _sink_: https://github.com/kamranahmedse/design-patterns-for-humans https://www.youtube.com/playlist?list=PLVmRRBrc2pRAEgzxUIJc_7LLABdg_58hJ https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001745
* in python https://python-patterns.guide/ https://hynek.me/articles/python-subclassing-redux/

# 🏭 CREATIONAL

https://realpython.com/python-multiple-constructors/#defining-multiple-class-constructors

ABSTRACT FACTORY
* families of related objects
* Provides an interface for creating families of related or dependent objects without specifying their concrete classes
* Example: UI toolkit that can create buttons, checkboxes, etc., for different platforms

PROTOTYPE
* cloning existing objects
* Creates new objects by copying an existing object (cloning)
* Example: Creating new documents by duplicating a template document

## ✅ factory

💻 https://github.com/zachvalenta/capp-edi

TYPES
* _factory_: don't have to know product impl 📙 Evans domain-driven [139] Gamma [107]
```python
DocBuilder().add_products('new item')
class ProductFactory:
    def create_segments(self, scenario_type, product_index=0):
        scenarios = {
            'new item': self._new_item,
            'pricing': self._pricing,
            'lead time': self._lead_time
        }
        return scenarios.get(scenario_type)
    def _new_item(self, index):
        return [
            f"LIN*{index}*VP*{product['id']}~",
            f"G53*003~",
        ] 
    def _pricing(self, index):
        return [
            f"LIN*{index}*VP*{product['id']}~",
            f"G53*001~",
        ]
```
```python
@dataclass
class Burger:
    bun: str | None = None
    protein: str | None = None
    cheese: str | None = None
    toppings: list[str] | None = None
    sauce: str | None = None
class BurgerFactory:
    @staticmethod
    def custom(**kwargs):
        return Burger(**kwargs)
    @staticmethod
    def kahuna():
        return Burger(
            bun = 'Hawaiian',
            protein = 'beef',
            cheese = 'cheddar',
            toppings = ['onions', 'pineapple'],
            sauce = 'teriyaki',
        )
```

SEMANTICS
* _factory_: creator 📙 Gamma [108]
* _product_: thing being created

---

TYPES
* _constructor_: 📙 Evans domain-driven [141]
* _abstract factory_: dedicated class to construct `CustomerFactory().default()` [Conery 243]

## ✅ builder

💻 https://github.com/zachvalenta/capp-edi
🗄️ `data/orm.md` query builders

```python
class DocBuilder:
    def __init__(self):
        self.segments = []
        self.control_number = 'VG9M'

def add_isa_gs_st(self):
    self.segments.extend([f"ST*832*{self.control_number}~"])
    return self

def add_ctt_to_iea(self):
    self.segments.extend(["GE*1*1~", "IEA*1*000000001~"])
    return self

DocBuilder().add_isa_gs_st().add_ctt_to_iea()
```

## singleton

---

> dependency injection generally better?

* single instance
* class that only allows single instance of itself
* naive impl can go haywire in multithreaded env [Conery 248]

Singleton: Ensures a class has only one instance and provides a global point of access to it.
Example: A configuration manager that should have a single instance.

Problem it solves: Ensures only one instance of a class is created and provides a global point of access to it.
Use cases:
Managing database connections.
Configuration objects or environment settings.
Logging systems where multiple instances are redundant.
Caution: Can introduce global state and tight coupling, so use it sparingly.

# 🦠 STRUCTURAL

FACADE (simplified interface)
* Provides a simplified interface to a larger body of code or subsystem.
* Example: A home theater facade that controls various subsystems (TV, speakers, streaming service).

BRIDGE
* Bridge (separate abstraction from implementation)
* Bridge: Decouples an abstraction from its implementation so that the two can vary independently.
* Example: A device abstraction (TV/Radio) with a concrete implementation of different remote controls.

COMPOSITE
* Composite (tree structures of objects)
* Composite: Composes objects into tree structures to represent part-whole hierarchies.
* Example: File system directories and files where directories can hold files and other directories.

FLYWEIGHT
Flyweight (sharing for efficiency)
Flyweight: Reduces memory usage by sharing data between similar objects.
Example: Sharing font objects to avoid creating multiple identical instances.

PROXY
Proxy (controlled access)
Proxy: Provides a surrogate or placeholder to control access to another object.
Example: Proxy server for security, logging, or caching.

## adapter (interface)

---

* _adapter_: wrapper e.g. ORM class for Postgres, MySQL, et al. [Conery 249] https://bitfieldconsulting.com/golang/adapter

Adapter (interface compatibility)

Adapter: Converts the interface of a class into another interface that clients expect.
Example: Adapter to make a legacy API compatible with new code.

## 📍 decorator

---

> pull in your timing function

Decorator (dynamic additional responsibilities)
Decorator: Dynamically adds behavior to an object without altering its structure.
Example: Adding features to a base coffee object (milk, sugar, caramel).

Problem it solves: Adds behavior to individual objects dynamically without changing the underlying class.
Use cases:
Adding logging, caching, or validation logic to functions or objects.
Extending UI elements with additional features (e.g., tooltips, borders).
Implementing middleware in HTTP frameworks (like Express or Flask).

# 🔍 BEHAVIORAL

Chain of Responsibility (request handling pipeline)
Mediator (loose coupling via coordinator)
Memento (capture/restore state)
State (behavior tied to state)
Template Method (skeleton algorithm)
Visitor (operations on elements)

## command

Command (requests as objects)

```python
from decimal import Decimal
from dataclasses import dataclass
from typing import Callable, List  # Only for clarity

class BankAccount:
    def __init__(self, account_id: str, balance: Decimal = Decimal('0')):
        self.account_id = account_id
        self.balance = balance
        
    def deposit(self, amount: Decimal) -> None:
        self.balance += amount
        
    def withdraw(self, amount: Decimal) -> None:
        if self.balance >= amount:
            self.balance -= amount
        else:
            raise ValueError("Insufficient funds")
            
    def __str__(self) -> str:
        return f"Account {self.account_id} - Balance: ${self.balance}"

@dataclass
class Command:
    execute_fn: Callable[[], None]
    undo_fn: Callable[[], None]

class TransactionManager:
    """
    Invoker class that handles transaction execution and history
    
    >>> account = BankAccount("123", Decimal('100'))
    >>> manager = TransactionManager()
    >>> deposit = Command(
    ...     lambda: account.deposit(Decimal('50')),
    ...     lambda: account.withdraw(Decimal('50'))
    ... )
    >>> manager.execute_transaction(deposit)
    >>> print(account)
    Account 123 - Balance: $150
    >>> manager.undo_last_transaction()
    >>> print(account)
    Account 123 - Balance: $100
    """
    def __init__(self):
        self.history: List[Command] = []
        
    def execute_transaction(self, command: Command) -> None:
        try:
            command.execute_fn()
            self.history.append(command)
        except ValueError as e:
            print(f"Transaction failed: {e}")
            
    def undo_last_transaction(self) -> None:
        if self.history:
            command = self.history.pop()
            command.undo_fn()

# Usage
if __name__ == "__main__":
    account = BankAccount("12345", Decimal('1000'))
    manager = TransactionManager()
    
    # Create and execute deposit command
    deposit = Command(
        execute_fn=lambda: account.deposit(Decimal('500')),
        undo_fn=lambda: account.withdraw(Decimal('500'))
    )
    
    manager.execute_transaction(deposit)
    print(account)  # Balance: $1500
    
    # Undo it
    manager.undo_last_transaction()
    print(account)  # Balance: $1000
```

## observer

Observer (one-to-many dependencies)
* _observer_: pub sub https://layerci.com/blog/postgres-is-the-answer http://blog.joncairns.com/2013/04/fat-model-skinny-controller-is-a-load-of-rubbish/
Defines one-to-many dependency between objects. When one object changes state, dependents get notified automatically.

> Reactive Programming: Handles event-driven programming, which may replace Observer patterns in modern reactive frameworks.

Problem it solves: Establishes a one-to-many relationship, allowing multiple objects (observers) to react to changes in a subject.
Use cases:
Event listeners (like user interface updates in real-time).
Publish-subscribe models (e.g., React components or webhooks).
Data synchronization between models and views in the MVC architecture.

HOOKS
* _hook_: response to event e.g. db trigger
* aka event handler, callback 📙 Chacon [402] https://stackoverflow.com/a/11087727
* _webhook_: res/ack (vs. req/res); 3rd streams > 1st polls https://sendgrid.com/blog/whats-webhook
* route known as "receiver" https://adamj.eu/tech/2021/05/09/how-to-build-a-webhook-receiver-in-django/
* further considerations https://brandur.org/webhooks https://www.svix.com/blog/webhooks-are-harder-than-they-seem/

## iterator

Iterator (sequential access)

## 📍 strategy

🗄️ `business.md` pricing
💻 https://github.com/zachvalenta/capp-brand-enablement

       Strategy Pattern
      ┌────────────────────┐
      │ PaymentStrategy    │
      ├────────────────────┤
      │ processPayment()   │
      │                    │
      │                    │
      └────────────────────┘
                ▲
                │
    ┌──────────┼──────────┐
    │          │          │
StripePayment  │  PayPalPayment
               │
               │
               │
               ▼
      Payment Provider APIs

Encapsulates interchangeable algorithms in separate classes. Client selects appropriate strategy at runtime.

```txt
This is metaprogramming using Python's attribute lookup system. The repository pattern would abstract data access behind a consistent interface. This code dynamically selects IO methods based on the format parameter, which is closer to the Strategy pattern, but implemented through Python's reflection capabilities.

Core mechanics:
getattr() returns bound methods for different formats
String interpolation creates method names
Uniform method naming convention in polars enables this
```

Strategy (interchangeable algorithms)

Problem it solves: Enables swapping algorithms or behaviors dynamically at runtime.
Use cases:
Different sorting algorithms based on data size (e.g., quicksort vs. mergesort).
Multiple authentication strategies (e.g., OAuth, API key, password-based).
Managing discounts or pricing rules dynamically in an e-commerce system.
