
# JavaScript中的iterable对象和迭代器

在JavaScript中，一个iterable对象是指一个对象，它实现了Symbol.iterator方法，该方法返回一个迭代器对象，该迭代器对象可以用于迭代该对象的每个元素。例如，数组、字符串、Set、Map等都是iterable对象。

## Q: 什么是Symbol.iterator

在JavaScript中，Symbol.iterator方法是一个内置的Symbol值，它定义了一个对象的默认迭代器。当一个对象被迭代时，它的Symbol.iterator方法会被调用，返回一个迭代器对象。该迭代器对象必须实现next()方法，该方法返回一个包含value和done属性的对象。value属性表示当前迭代的值，done属性表示迭代是否结束。

举个例子，我们可以使用Symbol.iterator方法创建一个自定义的iterable对象：

```javascript
const myIterable = {
  [Symbol.iterator]: function* () {
    yield 1;
    yield 2;
    yield 3;
  }
};

// 然后我们可以使用for...of循环遍历该对象的每个元素
for (const item of myIterable) {
  console.log(item);
}
```

输出结果为：

```
1
2
3
```

## Q: for...in 和 for...of的区别

举个例子，我们可以使用for...of循环遍历一个数组：

```javascript
const arr = [1, 2, 3, 4, 5];
for (const item of arr) {
  console.log(item);
}
```

而for...in循环用于遍历对象的属性，而不是数组的元素。举个例子，我们可以使用for...in循环遍历一个对象的属性：

```javascript
const obj = { a: 1, b: 2, c: 3 };
for (const key in obj) {
  console.log(key, obj[key]);
}
```

需要注意的是，for...of循环用于遍历iterable对象的元素，而不是对象的属性。举个例子，我们可以使用for...of循环遍历一个字符串的每个字符：

```javascript
const str = "hello";
for (const char of str) {
  console.log(char);
}
```

因此，我们可以总结出以下规律：

- for...in循环用于遍历对象的属性
- for...of循环用于遍历iterable对象的元素
