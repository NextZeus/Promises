Promise.resolve(4).then(function(value){
    console.log( value );
});

Promise.resolve 是new Promise()的快捷方式， 在进行promise对象的初始化或者编写测试代码的时候特别方便

Thenable
  指的是一个具有 .then 方法的对象。
  Jquery.ajax() 就是个thenable对象，这个对象具有then方法
  可以转换成为一个promise对象
  
  var promise = Promise.resolve( $.ajax() );
  
  promise.then(function(value){
    console.log(value);
  });
