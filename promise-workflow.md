function asyncFunction() {
    return new Promise(function (resolve, reject) {
        setTimeout(function () {
        resolve('Async Hello world'); }, 16);
    });
}
asyncFunction()
    .then(function (value) {
    console.log(value); // => 'Async Hello world'
}).catch(function (error) { console.log(error);
});


new Promise构造器之后，会返回一个promise对象

asyncFunction这个函数会返回promise对象，promise对象调用.then方法，来设置resolve后的回调函数， catch方法来设置发生错误时的回调函数

promise三个状态
Fulfilled: resolve时调用
Rejected:  rejected时调用（error）
unresolved:  Pending（promise对象刚被创建后的初始化状态）

//xhr-promise.js
function getURL(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest(); req.open('GET', URL, true); req.onload = function () {
            if (req.status === 200) { 
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));//Error对象
            } };
        req.onerror = function () { 
            reject(new Error(req.statusText)); //Error对象
        };
        req.send(); });
}
// 运行示例
var URL = "http://httpbin.org/get"; getURL(URL).then(function onFulfilled(value){
    console.log(value); }).catch(function onRejected(error){
    console.error(error); });

.catch() 只是 .then(undefined, onRejected)的别名  推荐.catch写法

