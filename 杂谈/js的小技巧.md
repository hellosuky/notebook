#### :b:生成随机id

---

关键点：

+ 通过`toString()`将我们的数字变成36进制
+ 通过`substr`去除小数点前面的部分

```javascript
const RandomId = len => Math.random().toString(36).substr(3,len)
const id = RandomId(10)
```



#### :bookmark_tabs:格式化金钱

---

关键点：

+ 将数字转化为字符串
+ `\B`表示非单词边界，不匹配任何实际的字符串,\b则是我们单词边界
+ `$`匹配结尾
+ `(?=\d{3}$)`匹配一个先行断言，这整句话说起来就是，有三个数字和结尾的前面

```javascript
const ThousandNum = num => num.toString().replace(/\B(?=\d{3})+\b)/g, ",");
const money = ThousandNum(20190214);
// money => "20,190,214"
```



#### :orange:操作URL查询参数

---

关键点：

+ `URLSearchParams`是一个集成的URL处理方法，唯一的问题在于现在众多浏览器并不支持

```javascript
const params = new URLSearchParams(window.location.search.replace(/\?/ig, "")); 
// window.location.search = "?name=young&sex=male"
params.has("young"); // true
params.get("sex"); // "male"
```



#### :innocent:补零

---

关键点：

+ `padStart`是用来补0的函数，他将会在字符串的开头进行字符补全，那与他对应的是`padEnd`他是在字符串的后面进行补零

```javascript
const FillZero = (num, len) => num.toString().padStart(len, "0");
const num = FillZero(169, 5);
// num => "00169"
```



#### :cry:生成范围随机数

---

```javascript
const RandomNum = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
const num = RandomNum(1, 10);
```



#### :flushed:混淆数组

---

关键点：

+ `sort()`是对数组进行排序的函数，里面能够输入我们对各个元素排序的规则。

```javascript
const arr = [0, 1, 2, 3, 4, 5].sort(() => Math.random() - .5);
// arr => [3, 4, 0, 5, 1, 2]
```



#### :no_mouth:统计数组成员的个数

---

```javascript
const arr = [0, 1, 1, 2, 2, 2];
const count = arr.reduce((t, c) => {
    t[c] = t[c] ? ++ t[c] : 1;
    return t;
}, {});
// count => { 0: 1, 1: 2, 2: 3 }
```

