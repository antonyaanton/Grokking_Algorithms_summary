# **Грокаем алгоритмы.** Адитья Бхаргава
<image src=https://img4.labirint.ru/rc/3a7e6da517de3fd690f748433aef73b4/363x561q80/books58/571060/cover.jpg?1598873204 alt=''>

## Глава 2. _Сортировка выбором_

### Массивы и списки

При сохранении отдельных значений в памяти компьютера, запрашивается место в памяти, а затем выдается адрес для сохранения значения.

Существует несколько видов хранения списка элементов: **массивы** и **связанные списки**. 

При использовании _массива_ все элементы хранятся в памяти непрерывно, поэтому при добавлении в него новых элементов, компьютер будет должен выделить адрес для такого объема памяти, в который бы уместился массив с добавленным элементом. Элементы _связанного списка_ могут размещаться в памяти где угодно. Так, в каждом элементе _списка_ хранится адрес следующего элемента списка. 
Приемуществом _массива_ перед _связанном списком_ состоит в том, что обращение к любому элементу _массива_ происходит мгновенно. В _связанном списке_ элементы не хранятся рядом друг с другом, поэтому чтобы получить адрес, например, третьего элемента, сначала нужно обратиться к первому элементу, чтобы получить адрес второго, затем ко второму для получения адреса третьего. 

Связанные списки лучше подходят для вставки элемента в середину списка задач. Такая задача решается изменением указателя в предыдущем элементе. Также они эффективно подходят для удаления. 

Использование связанных списков и массивов зависит от сценария использования. Массивы популярны из-за поддержки произвольного доступа. Всего существует два вида доступа: **произвольный** и **последовательный**. При последовательном доступе элементы чиатются по одному, начиная с первого. Его поддерживают только связанные списки. 

### Сортировка выбором

1. Создаем пустой список
2. Проходим по списку и находим элемент с самым наибоьшим/наименьшим значением
3. Добавлем элемент в этот список
4. Повторяем

```python
def findSmallest(arr): #функция поиска наименьшего элемента массива
  smallest = arr[0]   #для хранения наименьшего значения
  smallest_index = 0  #для хранения индекса наименьшего значения
  for i in range(1, len(arr)):
    if arr[i] < smallest:
      smallest = arr[i]
      smallest_index = i
    return smallest_index

def selectionSort(arr): #функция сортировки выбором
  newArr = []
  for i in range(len(arr)):
    smallest = findSmallest(arr)
    newArr.append(arr.pop(smallest))
  return newArr
```





