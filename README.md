# 构造函数...继承实例化的空对象的原型赋值
<!--创建Duck对象 构造函数-->
 ```javascript
 function Duck(name,color){
 this.name = name || '某某';
 this.color = color || '黄';
}
Duck.prototype ={
eat:function(){ console.log(this.color+'颜色的鸭子'+this.name+'在吃虫子..')},
walk:function(){ console.log(this.color+'颜色的鸭子'+this.name+'走起来..')},

toString:function(){ console.log(this.color+'颜色的鸭子'+this.name+'在吃虫子..')}
}

var jack = new Duck('jack','黄');
jack.walk();
jack.toString():

/****
定义一个FarDuck对象
继承了Duck中的一些属性和方法**/
function  FatDuck(weight){
this.weight =weight ||5;
//通过apply的方法把Duck对象的属性引入 
/***
参数1 this  代表当前的FatDuck
参数2 使用apply方法时 []数组,包含里Duck 对象所需要的参数
      使用call方法时,后面跟上所有的参数用','分割**/
      //Duck.apply(this,['jarry','蓝色']) 效果跟call一样 
      Duck.call(this.'jarry','蓝色');
      
      //在此处重新定义一个show WeightFun方法  用此方法定义的showWeightFun在Duck原型上不会出现
      this.showWeightFun = function(){ console.log('这是肥鸭的体重为'+this.weight+'斤');}
      }
      //把Duck.prototype赋值给FatDuck.prototype 属于引用赋值
      FatDuck.prototype = Duck.prototype;
      /**此处我系应该了FatDuck原型上的方法 
      同事Duck原型上的方法也被我改变了 使用此方法 容易形成猴子补丁...
      (猴子补丁详情参见http://www.tuicool.com/articles/2aIZZb)**/
      FatDuck.prototype.showWeight =function(){
      console.log('这是肥鸭的体重为'+'this.weight'+'斤')}
      var littleFatDuck = new FatDuck();
      
      <!--新创建的测试属性鸭子-->
      function  ThinDuck(){ Duck.apply(this,['lily','蓝色']);}
      
      <!---->
      
 ```
 
