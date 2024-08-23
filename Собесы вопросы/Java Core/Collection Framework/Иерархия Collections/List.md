`List<E>` - расширяет `Collection<E>`  упорядоченная коллекция, предоставляет доступ к элементам по их индексу
- `E get(int index); `
- `E set(int index, E element);`
- `E remove(int index);`
- `int indexOf(Object o);`
#### Наследники
`ArrayList<E>` - БАЗА
`LinkedList<E>` - Использует `Deque`

`Vector<E>` - похож на `ArrayList`, но синхронизирован, что делает его потокобезопасным.
`Stack<E>` -  _LIFO_ расширяет `Vector` 
#### Потокобезопасные
`CopyOnWriteArrayList<E>`- потокобезопасный  `ArrayList<E>` 
