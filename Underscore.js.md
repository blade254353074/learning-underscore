# Underscore.js
## 集合函数(Array or Object)

**each**  _.each(list, iteratee, [context])  (iteratee: 迭代)
> 遍历list中所有元素,按顺序用遍历输出每个元素

```
_.each([0, 1, , 3, false, undefined, null], function(elem, idx, list) {
    console.log(elem); // 0 1 undefined 3 false undefined null
});
_.each({a: undefined, undefined: 1, null: false, b: null}, function(value, key, list) {
    console.log(value); // undefined 1 false null
});
```

**map**  _.map(list, iteratee, [context])
> 遍历list中所有元素, 将返回值映射到**新的数组**中

```
_.map([0, 1, , 3, false, undefined, null], function(elem, idx, list) {
    return elem * 2;
});
> [0, 2, NaN, 6, 0, NaN, 0]

_.map({a: undefined, undefined: 1, null: false, b: null}, function(value, key, list) {
    return elem * 2;
});
> [NaN, 2, 0, 0]
```

**reduce**  _.reduce(list, iteratee, [memo], [context])  (memo: 备忘)
> 把list中元素归结为一个单独的数值

```
_.reduce([0, 1, 2, 3], function(meno, val, idx, list) {
    return meno + val; // -1 + 0 + 1 + 2 + 3
}, -1);
> 5

_.reduce({a: 0, undefined: 1, null: 2, b: 3}, function(meno, val, key, list) {
    console.log(key); // undefined null b
    return meno + val;
});
> 6
```

**reduceRight**  _.reduceRight(list, iteratee, memo, [context])
> 从右侧开始组合的元素的reduce函数

```
_.reduceRight([[0, 1], [2, 3], [4, 5]], function(meno, val, idx, list) {
    return meno.concat(val);
}, [6, 7]);
> [6, 7, 4, 5, 2, 3, 0, 1]

_.reduceRight({a: 0, undefined: 1, null: 2, b: 3}, function(meno, val, key, list) {
    console.log(key); // null undefined a
    return meno + val;
});
> 6
```

**find**  _.find(list, predicate, [context])  (predicate: 断言)
> 返回**第一个**通过predicate迭代函数真值检测的元素值

```
_.find([0, 1, , 3, false, undefined, null], function(elem, idx, list) {
    return elem > 2;
});
> 3

_.find({a: 0, undefined: 1, null: 2, b: 3}, function(val, key, list) {
    return val > 2;
});
> 3
```
