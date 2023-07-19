###  1.
Какой из двух фрагментов кода не сработает и почему?

Фрагмент 1:
```	
	console.log( doubleNum(10) );

	let doubleNum = (num) => {
		let result = num * 2;
		return result;
	}
```  

Фрагмент 2:
```
	console.log( doubleNum(10) );

	function doubleNum(num) {
    		let result = num * 2;
		return result;
	}
```  

#### Не работает фрагмент 1, т. к. это function expression, let doubleNum не подвергнется всплытию, вызов до объявления, ReferenceError.

### 2.
Исправьте ошибку в фрагменте коде так, чтобы после компиляции в шаблоне не было лишних тегов:
```
	<template>
        <div>
            <component-name
                v-for="i of count" 
                :key="i"
                v-if="i < 10" 
            />
        </div>
	</template>

	<script>
	export default {
		data() {
			return {
				count: 20,
			};
		},
	};
	</script>  
```  
#### Удалил ";" в 41 строке и добавил элемент-оболочку <div>, чтобы правильно заключить цикл v-for.

### 3.
Есть массив некоторых строительных материалов, каждый элемент массива - объекты с ключами id и количества материала. Напишите функцию, которая будет возвращать oбьект в формате { "id":"count" }

```
   resources = [
			{
			   id: 1,
			   count: 13,
   			},
			{
			   id: 2,
			   count: 5,
   			}, 
			{
			   id: 3,
			   count: 24,
   			},
		      {
			   id: 4,
			   count: 101,
   			}, 
			{
			   id: 5,
			   count: 72,
   			}, 
			{
			   id: 6,
			   count: 64,
   			}, 
			{
			   id: 7,
			   count: 305,
   			}, 
			{
			   id: 8,
			   count: 67,
   			}, 
			{
			   id: 9,
			   count: 95,
   			}, 
			{
			   id: 10,
			   count: 21,
   			}, 
			{
			   id: 11,
			   count: 37,
   			},
		   ];
```  

Ожидаемый результат:

```
  {
				   1: 13,
				   2: 5,
				   3: 24,
				   4: 101,
				   5: 72,
				   6: 64,
				   7: 305,
				   8: 67,
				   9: 95,
				   10: 21,
				   11: 37,
			     }
```  

```
// реализация 1
const format = (coll) => coll.reduce((acc, { id, count }) => ({ ...acc, [id]: count }), {});

// реализация 2
const format2 = (coll) => {
    const result = {};

    for ({ id, count } of coll) {
        result[id] = count;
    }

    return result;
}
```