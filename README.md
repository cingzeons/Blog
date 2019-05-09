## Welcome to GitHub Pages


#### Electron 等开箱即用的模版
```jsx
// electron深入浅出 `https://blog.csdn.net/sinat_36422236/article/details/84988291` 
// 官网 https://electronforge.io/cli/start
electron-forge
electron-forge包含vue、react、Angular等开箱即用的模版。

npm i -g electron-forge
electron-forge init my-app template=react
cd my-app
npm run start 
目录结构如下

```

You can use the [editor on GitHub](https://github.com/cingzeons/Blog/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/cingzeons/Blog/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.



## Blog
This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br>
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br>
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (Webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify

## 《三分钟阅读》7个有用的JavaScript技巧
#### 数组去重
```js
var j = [...new Set([1, 2, 3, 3])];
>> [1,2,3]

//这个去重方法简单的令人陶醉
```



#### 过滤空值
```js
// 空值指的是没有具体意义的一些值，比如0，undefined，null，false，空字符串等
let res = [1,2,0,undefined,null,false,''].filter(Boolean);
>> 1,2
```




#### 创建空对象
```js
/*创建一个空对象，我们可能大多数时候会使用对面字面量为{}的方式，然而这种方式创建的对象并不是纯粹的，它任然有__proto__属性以及继承自Object原型的一些方法，这种方式创建的对象容易被修改，比如：*/

let o = {};
let p = Object.create(null);
Object.prototype.say = function(){
    console.log('hello')
}
console.log(o.say)
console.log(p.say)

>> f(){}
>> undefined

/*可以看到通过{}创建的对象，很容易就被修改了，而通过Object.create(null)这种方式创建的对象就很纯粹，没有任何属性和对象，非常干净。*/

```




#### 合并对象
```js
/*通过...延展操作符可以很容易的合并对象*/
const person = { a:1 };
const tools = { b:2 };
const attributes = { c:3 };

const summary = {...person, ...tools, ...attributes};

>> {a:1,b:2,c:3}
/*不得不说...延展操作符真是好东西啊！*/
```


#### 参数非空检测
```js
/*这个方法特别适用于封装函数时使用，也许我们知道可以在函数参数中直接指定一个默认值，像下面这样：*/

function test(parma = 'default'){}

/*然而，我们也可以直接赋值一个函数，如果没有传参，我们就直接抛出错误提醒，如果一个组件里面有很多方法，我们就可以直接复用，而不用每个方法里面都去做非空判断处理。*/

const isRequired = () => { throw new Error('param is required'); };

const hello = (name = isRequired()) => { console.log(`hello ${name}`) };
// 抛出一个错误，因为参数没有传
hello()；
// 没有问题
hello('hello')

```



#### 解构添加别名
```js
/*在导入多个模块的时候，为防止引用的组件重名，我们可以在引入时直接赋值一个别名*/
const obj = { x: 1 };

const { x: otherName } = require('module');

/*使用的时候就可以直接使用otherName*/
```



#### 获取查询字符串参数
```js
/*
url: https://developer.mozilla.org/zh-CN/docs/Web/API/URLSearchParams
获取url里面的参数值或者追加查询字符串，在这之前，我们一般通过正则匹配处理，然而现在有一个新的api，具体详情可以查看这里，可以让我们以很简单的方式去处理url。
假如我们有这样一个url，"?post=1234&action=edit"，我们可以这样处理这个url*/

var urlParams = new URLSearchParams('?post=1234&action=edit');

console.log(urlParams.has('post')); 
console.log(urlParams.get('action')); // "edit"
console.log(urlParams.getAll('action')); // ["edit"]
console.log(urlParams.toString()); // "?post=1234&action=edit"
console.log(urlParams.append('active', '1')); // "?post=1234&action=edit&active=1"

/*是不是很方便？那浏览器支持程度如何呢？通过这个地址查看，可以发现大部分浏览器都支持哦！，如果碰到不支持的情况，这里还有个polyfill。*/

```


#### URLSearchParams 接口定义了一些实用的方法来处理 URL 的查询字符串。
```js
// 一个实现了 URLSearchParams 的对象可以直接用在 for...of 结构中，例如下面两行是相等的。
for (var p of mySearchParams);
for (var p of mySearchParams.entries());
/*Note: 此特性在 Web Worker 中可用。*/

//构造函数节
URLSearchParams()
/*返回一个 URLSearchParams 对象。*


// 属性节
/*该接口不继承任何属性。*/

URLSearchParams.append()    // 插入一个指定的键/值对作为新的搜索参数。 

URLSearchParams.delete()    // 从搜索参数列表里删除指定的搜索参数及其对应的值。 

URLSearchParams.entries()   // 返回一个iterator可以遍历所有键/值对的对象。 

URLSearchParams.get()       // 获取指定搜索参数的第一个值。 

URLSearchParams.getAll()    // 获取指定搜索参数的所有值，返回是一个数组。

URLSearchParams.has()       // 返回 Boolean 判断是否存在此搜索参数。 

URLSearchParams.keys()      // 返回iterator 此对象包含了键/值对的所有键名。

URLSearchParams.set()       // 设置一个搜索参数的新值，假如原来有多个值将删除其他所有的值。

URLSearchParams.sort()      // 按键名排序。 

URLSearchParams.toString()  // 返回搜索参数组成的字符串，可直接使用在URL上。

URLSearchParams.values()    // 返回iterator 此对象包含了键/值对的所有值。
 



// 示例
var paramsString = "q=URLUtils.searchParams&topic=api"
var searchParams = new URLSearchParams(paramsString);

for (let p of searchParams) {
  console.log(p);
}

searchParams.has("topic") === true; // true
searchParams.get("topic") === "api"; // true
searchParams.getAll("topic"); // ["api"]
searchParams.get("foo") === ""; // true
searchParams.append("topic", "webdev");
searchParams.toString(); // "q=URLUtils.searchParams&topic=api&topic=webdev"
searchParams.set("topic", "More webdev");
searchParams.toString(); // "q=URLUtils.searchParams&topic=More+webdev"
searchParams.delete("topic");
searchParams.toString(); // "q=URLUtils.searchParams"
```
