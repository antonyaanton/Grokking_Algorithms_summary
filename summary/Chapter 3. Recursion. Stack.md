# Глава 3. Рекурсия
## Рекурсия
_Псевдокод_ - высокоуровневое описание решаемой задачи. Он записывается в форме, похожей на программный код, но в большей степени напоминает естественный язык.

**Рекурсия** - вызов функцией самой себя.

Пример рекурсии:
```python
def look_for_key(box):
  for item in box:
    if item.is_a_box():
      look_for_key(item)
    elif item.is_a_key():
      print("found the key!")
```
Каждая рекурсивная функция состоит из двух частей: базового случая и рекурсивного случая.

```python
def countdown(i):
  print(i)
  if i <= 1:          #базовый случай 
    return
  else:               #рекурсивный случай 
    countdown(i - 1)
```
## Стек
**Стек** - структкура данных.

При рассмотрении списков и массивов, у нас был список задач. Задачи, т.е. элементы списка можно было добавлять и удалять в произвольных позициях списка. Стопка листов работает куда проще. Новые (вставленные) элементы добавляются в начало списка, то есть на верх стопки. Читается только верхний элемент, и он исключается из списка. Таким образом, список задач поддерживает всего два действия: _занесение_ (вставка) и _извлечение_ (выведение из списка и чтение).

## Стек вызовов

```python
def greet(name):
  print "hello, " + name + "!"
  greet2(name):
  print "getting ready to say bye..."
  bye()

def grret2(name):
  print "how are you, " + name + "?"
def bye():
  print "ok bye!"
```
Предположим, в программе используется вызов `greet("maggie")`. Сначала компьютер выделяет блок памяти для этого вызова функции. Затем эта память используется. Переменной `name` присваивается значение `"maggie"`; оно должно быть сохранено в памяти. Каждый раз, когда вы вызываете функцию, компьютер сохраняет в памяти значения всех переменных для этого вызова. Далее выводится приветствие `hello, maggie!`, после чего следует второй вызов `greet2("maggie")`. И снова компьютер выделяет блок памяти для вызова функции. Компьютер выделяет эти блоки в стек. Второй блок создается над первым. Вы выводите сообщение `how are you, maggie?`, после чего возвращаете управление из вызова функции. Когда это происходитЮ блок на вершине стека извлекается из него. Теперь веохний блок относится к функции `greet`; это означает, что вы вернулись к функции `greet`. При вызове функции `greet2` функция `greet` еще была _не завершена_. _Когда вы вызываете функцию из другой функции, вызывающая функция приостанавливается в частично завершенном состоянии._ Все значения переменных этой функции остаются в памяти. А когда выполнение функции `greet2` будет завершено, вы вернетесь к функции `greet` и продолжите ее выполнение с того места, где оно прервалось. Сначала выводится сообщение `getting ready to say bye...`, после чего вызывается функция `bye`. Блок для этой функции добавляется на вершну стека. Далее выводится сообщение `ok bye!` с выходом из вызова функции. Управление снова возвращается функции `greet`. Делать больше нечего, так что управление возвращается и из функции `greet`. Этот стек, в котором сохранялись переменные разных функций, называется _`стеком выражений`_.
## Стек вызовов с рекурсией
```python
def factorial(x):
  if x == 1:
    return
  else:
    return x * factorial(x - 1)
```
## Выводы:
* Когда функция вызывает саму себя, это называется рекурсией.
* В каждой рекурсивной функции должно быть два случая: базовый и рекурсивный
* Стек поддереживает две операции: занесение и извлечение элементов.
* Все вызовы функций сохраняются в стеке вызовов.
* Если стек вызовов станет очень большим, он займет слишком много памяти.
