# 44 道 JavaScript 谜题

> 题目来自于 [JavaScript Puzzlers!](http://javascript-puzzlers.herokuapp.com/) 。下午花时间做了一遍，然后翻译成了中文并增加了一些个人解释。文章同步发布于【掘金】和微信公众号【布谷工作室】，公众号答案和解析位于下方的折叠部分，单击即可查看。



又称： 你真的了解 JavaScript 吗？

又称： 你认为 JavaScript 有多疯狂？



这是一套在浏览器环境下的基于 ES5 的测试题。在 node 或 jsc 等环境下可能会有不同的行为。



**1. 下面表达式的结果是什么？**

```js
["1", "2", "3"].map(parseInt)
```

- A `["1", "2", "3"]`

- B `[1, 2, 3]`
- C `[0, 1, 2]`
- D `other`



**答案： D**

你将会得到 `[1, NaN, NaN]` 的结果，因为 `parseInt` 函数有两个参数 `(val, radix)`，`map` 的回调函数有三个参数 `(element, index, array)`。



译者注：

由于有 `parseInt(val, index)`，

`map((element, index, array) => {}, thisArg)`，

 上述表达式的执行过程如下：

`parseInt(1, 0)` 返回值为 1，

`parseInt(2, 1)` 返回值为 NaN，

`parseInt(3, 2)` 返回值为 NaN。

最终结果为 `[1, NaN, NaN]`。





**2. 下面表达式的结果是什么？**

```js
[typeof null, null instanceof Object]
```

- A `["object", false]`

- B `[null, false]`
- C `["object", true]`
- D `other`



**答案： A**

`typeof null` 返回类型为对象。



译者注：

`null` 表示什么都没有，`typeof` 将其判断为对象，而 `instanceof`是判断对象上有无构造函数，故为 `false`。





**3. 下面表达式的结果是什么？**

```js
[ [3,2,1].reduce(Math.pow), [].reduce(Math.pow) ]
```

- A `an error`

- B `[9, 0]`
- C `[9, NaN]`
- D `[9, undefined]`



**答案： A**

特别提醒：在数组没有初始值的情况下 `reduce` 将抛出 `TypeError`。



译者注：

`reduce` 函数对数组中的每一个元素升序执行一次回调函数，并返回汇总结果。

上面表达式一将执行以下几步：

`Math.pow(3, 2)` 结果为 9，

`Math.pow(9, 1)` 结果为 9，故最终结果为 9。

对于空数组 `reduce` 将抛出错误，对于只有一项的数组将不执行回调函数直接返回该值，如 `[2].reduce((a, c) => a + c)` 返回值为 2。





**4 下面表达式的结果是什么？**

```js
var val = 'smtg';
console.log('Value is ' + (val === 'smtg') ? 'Something' : 'Nothing');
```

- A `Value is Something`

- B `Value is Nothing`
- C `NaN`
- D `other`



**答案： A**

特别提醒：在数组没有初始值的情况下 `reduce` 将抛出 `TypeError`。



译者注：

`reduce` 函数对数组中的每一个元素升序执行一次回调函数，并返回汇总结果。

上面表达式一将执行以下几步：

`Math.pow(3, 2)` 结果为 9，

`Math.pow(9, 1)` 结果为 9，故最终结果为 9。

对于空数组 `reduce` 将抛出错误，对于只有一项的数组将不执行回调函数直接返回该值，如 `[2].reduce((a, c) => a + c)` 返回值为 2。



























