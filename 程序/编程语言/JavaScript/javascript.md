- JavaScript
    他是一种脚本语言，可以用来更改页面内容，控制多媒体制作图像，动画等等
```
<script>
js代码
</script>
引入js脚本
<script src="脚本路径"></script>
```
* 变量与数据类型
    声明变量有三种方式
    let
    `let 变量名 = 值`
    `console.log(a)`在控制台打印出变量
    let声明的变量可以被多次赋值
    const
    `const 常量名 = 值`
    const 修饰的叫常量，只能赋值一次
    var
    var也可以多次被赋值，但是能用let就少用var
* 基本数据类型
    undefined和null
    执行表达式或函数，没有返回结果，出现undefined
    访问数组不存在的元素，访问对象不存在的属性，出现undefined
    定义变量没有初始化，出现undefined
    两者的共同点
       都没有属性，方法
    两者的区别
      undefined由js产生
      null是由程序员提供  
* Sting
    在JavaScript中字符串有三种表示方式'' | "" | ‘’
- number和bigint
    number类型表示的是双精度浮点小数如
    `10/3 = 3.33333333`
    既然是浮点小数，那么可以除以零
    `10/0 = 结果是Infinity正无穷大`
    `-10/0 = 结果是-Infinity负无穷大`
    浮点小数都有运算精度问题，例如
    `2.0-1.1;结果是0.8999999999999999999`
    如果不想是小数可以在后面加给n表示bigint
    3n就表示的整数而不是浮点数
- 字符串转数字
    parseInt("10")；结果是数字10
       parseInt("10.5")；结果是10，去除了小数点部分但是结果仍是浮点数
       如果不属于数字则会显示nan转换失败
       也可以直接用"10"- 1；JavaScript在检测到运算时会自动转化类型
- Boolean
    有两个值truthy和falsy，就是true和false
    falsy类
        false表示false
        Nullish（null，undefined）都表示false
        0也表示false
        “”，'',‘’|这三种空字符串也表示false
    在JavaScript中并不是Boolean才能用于条件-判断，可以在if语句中使用数字0或1表示条件判断
- function
    定义函数
    `function 函数名(参数){函数体，return返回结果//不是必须返回}`
    JavaScript参数类型没有限制，参数个数也没有限制
    要实现默认值
    `function p(a = 1,b = 2)`当调用函数没传参数的时候默认使用1，和2
    匿名函数
         `(function(参数){函数体,return 结果}(参数))`,JavaScript匿名函数就是立即调用并且只执行一次
         `(function(a,b){return a+b }(1,2))`结果为3
        也可以这样
        let d =  document.getElementById("a").onclick = (function(){
              console.log("aa");
        });
     箭头函数
        箭头函数类似简化版的匿名函数
         document.getElementById("a").onclick = () => console.log("aaaaaaaa");
- 数组
    push：向数组后面添加元素
    splice：输入下标删除下标对应的数组元素
    join：把数组连接成字符串括号内可以指定拼接符号
    map：替换数组内的元素 let arr =[1,2,3];function a(i){return i x 10} arr.map(a)
     [10, 20, 30]，函数指定乘以几
    filter：返回一个布尔值，可以去除数组中不符合的数let d = [1,2,3,4,5,6];d.filter((i)=>{return i % 2 == 1})
      [1, 3, 5]
    forEach：遍历数组里的内容：let e = [1,2,3,4]; e.forEach((i) => console.log(i))
* object
    let s{
    nm: "姓名"
    age:18
    s: function(){
    console.log(nm+age)
    }
    }
    调用s.nm
    私有属性类似于Java的私有成员变量
      let s = {

        a: null,

        get nm(){

        return this.a;

        },

        set nm(n){

        this.a = n;

        }

        }
  js中的对象，不需要什么模板，它的属性可以随时加减
      let s = {nm: "张三"}
     undefined
     s.ag = 18//添加一个对象属性
     18
     console.log(s)
    VM235:1 {nm: '张三', ag: 18}
    想要删除就要用到
    delete s.ag
JavaScript继承
    let f = {
    fi: "父级属性"
    mi(){
    console.log("父方法")
    }
    }
    创建一个继承父级的子类
    let s = Object.create(f);
- json
    json对象本质上是一个字符串，它的职责是作为客户端和服务端之间传递数据，他的属性是个样子
    json中只能有null，true，false，数字，字符串(只有双引号)。对象数组
    json中不能有除以上的其他js对象特性，如方法灯
    json中的属性必须用双引号括起来
    json字符串与js的转换
    json.parse(json字符串 )//返回js对象
    json.stringify(jsd对象)//返回json字符串
- 控制语句
    遍历对象for in
     let f = {q:"张三",b:1}; for(const n in f){console.log(n)}
     获取属性和值
     for(const n in f){console.log(n,f[n])}
     for of 遍历数组
     使用方法跟上面一样