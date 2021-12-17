- [总结webAPI的常用请求方法与后台参数的获取：](#总结webapi的常用请求方法与后台参数的获取)
  - [一：get请求：（会将所有参数拼接到URL里面）](#一get请求会将所有参数拼接到url里面)
    - [1：基础类型：](#1基础类型)
    - [2：实体类型：](#2实体类型)
      - [(1)使用 `[FromUri]` 关键字：前端写到ajax里面的data属性里面提交，如](#1使用-fromuri-关键字前端写到ajax里面的data属性里面提交如)
      - [(2)不使用 `[FromUri]` 关键字](#2不使用-fromuri-关键字)
      - [(3)：若web API的接口方法名称以get开头的时候，可以省略[HttpGet]过滤](#3若web-api的接口方法名称以get开头的时候可以省略httpget过滤)
  - [二：post请求](#二post请求)
    - [1：基础类型：](#1基础类型-1)
    - [2：多个基础类型数据参数](#2多个基础类型数据参数)
    - [3：单个实体类型：](#3单个实体类型)
    - [4：单个实体类型：](#4单个实体类型)
    - [5：基础类型+实体：](#5基础类型实体)
    - [6：数组为参数：](#6数组为参数)
    - [7:实体集合：](#7实体集合)
  - [三：put请求机制和post一样](#三put请求机制和post一样)
  - [四：delete请求机制和post一样](#四delete请求机制和post一样)
- [WebAPI之[FromBody]和[FromUri]的参数绑定规则](#webapi之frombody和fromuri的参数绑定规则)
- [前端接口请求传参](#前端接口请求传参)
    - [get 方法:](#get-方法)
    - [post方法:](#post方法)

# 总结webAPI的常用请求方法与后台参数的获取：
## 一：get请求：（会将所有参数拼接到URL里面）
### 1：基础类型：
**` string  a=“hello” `， 前端无论你是写到ajax里面的data属性还是直接拼接到URL里面，后台直接string a获取；**
``` csharp
[HttpGet]

public Object AddUserInfo(string a)
{
    .........
}
```

###   2：实体类型：
#### (1)使用 `[FromUri]` 关键字：前端写到ajax里面的data属性里面提交，如
```
data:{
      Id:"1",
      Name:"lsm",
      Old:"25",
    }
```

后台采用实体接收，先定义实体，属性名称需要和前台传过来的属性名称一致，使用 `[FromUri]` 关键字接收，

如模型定义为
``` csharp
 public class UserModel
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Old { get; set; }
    }
```
接口写成：
``` csharp
[HttpGet]

public JObject AddUserInfo([FromUri]UserModel userInfo)
{
    .........
}
```
#### (2)不使用 `[FromUri]` 关键字

前台将对象序列化成字符串：
```
data: { 
    strQuery: JSON.stringify({
        Id:"1",  
        Name:"lsm",
        Old:"25",
      })
    }
```

后台采用字符串接收：参数名需和前台传过来的一致，并再序列化json对象

 接口写法 
``` csharp
[HttpGet]
    public string GetByModel(string strQuery)
    {
       UserModel oData = Newtonsoft.Json.JsonConvert.DeserializeObject(strQuery);
        ...
    }
```
#### (3)：若web API的接口方法名称以get开头的时候，可以省略[HttpGet]过滤

## 二：post请求
### 1：基础类型：
```
data: { "": "Jim" },
```
注意这里不能写key值，否则后台获取到的值将为空，后台使用 ***[FromUri]*** 关键字获取
``` csharp
[HttpPost]
     public bool SaveData([FromBody]string NAME)
     {
        return true;
     }
```
### 2：多个基础类型数据参数
前台写法：
```
data:{
      Id:"1",
      Name:"lsm",
      Old:"25",
    }
```
后台取法：使用`dynamic`关键字
``` csharp
    [HttpPost]
    public object SaveData(dynamic obj)
    {
        var strName = Convert.ToString(obj.NAME);
        return strName;
    }
```

### 3：单个实体类型：
**注意此时不能指定contentType为*appplication/json*，应当默认的*application/x-www-form-urlencoded*，否则将取不到数据**
前台写法
```
data:{
      Id:"1",
      Name:"lsm",
      Old:"25",
    }
```
后台直接由实体接收：
``` csharp
[HttpPost]
   public bool SaveData(UserModel oData)
   {
       return true;
   }
```

### 4：单个实体类型：

**前台指定contentType为*appplication/json*，必须将json对象序列化在传输**

前台写法:
```
postdata:{
      Id:"1",
      Name:"lsm",
      Old:"25",
    }
data: JSON.stringify(postdata),
```

后台直接由实体接收：
``` csharp
[HttpPost]
   public bool SaveData(UserModel oData)
   {
       return true;
   }
 ```

### 5：基础类型+实体：
**指前台定contentType为*appplication/json*，后台使用`dynamic`关键字接收**
前台：
```
postdata:{
      Id:"1",
      Name:"lsm",
      Old:"25",
    }
data: JSON.stringify({NAME:"Lilei", Charging:postdata}),
```
后台：
``` csharp
[HttpPost]
     public object SaveData(dynamic obj)
     {
         var strName = Convert.ToString(obj.NAME);
         var oCharging = Newtonsoft.Json.JsonConvert.DeserializeObject(Convert.ToString(obj.Charging));
         return strName;
     }
```
### 6：数组为参数：
**前台指定contentType为*appplication/json***

前台：
```
arr:["2","3","3","5"]
data: JSON.stringify(arr),
```
后台：
``` csharp
  [HttpPost]
    public bool SaveData(string[] ids)
    {
         return true;
    }
 ```
### 7:实体集合：
**前台指定contentType为*appplication/json***

前台
```
var arr = [
        { ID: "1", NAME: "Jim", CREATETIME: "1988-09-11" },
        { ID: "2", NAME: "Lilei", CREATETIME: "1990-12-11" },
        { ID: "3", NAME: "Lucy", CREATETIME: "1986-01-10" }
    ];
 
data: JSON.stringify(arr),
```
后台：
``` csharp
 [HttpPost]
    public bool SaveData(List lstCharging)
    {
       return true;
    }
```
## 三：put请求机制和post一样
## 四：delete请求机制和post一样


_________________
_________________

# WebAPI之[FromBody]和[FromUri]的参数绑定规则

**在WebAPI中，请求主体(HttpContent)只能被读取一次，不被缓存，只能向前读取的流。**

举例子说明：

1. 请求地址：/?id=123&name=bob
    > 服务端方法：
    >` void Action(int id, string name)// 所有参数都是简单类型，因而都将来自url` 

2. 请求地址：/?id=123&name=bob
    > 服务端方法：
    > `void Action([FromUri] int id, [FromUri] string name) //  所有参数都是简单类型，因而都将来自url`

    >`void Action([FromBody] string name); //[FormBody]特性显示标明读取整个body为一个字符串作为参数`

3. 请求地址： /?id=123
    >类定义：
    >``` csharp
    >public class Customer {   // 定义的一个复杂对象类型 
    >  public string Name { get; set; } 
    >  public int Age { get; set; } 
    >}
    >```

    >服务端方法：
    > `void Action(int id, Customer c) // 参数id从query string中读取，参数c是一个复杂Customer对象类戏，通过formatter从body中读取`

    >服务端方法：
    ><font color=red>
    >` void Action(Customer c1, Customer c2) // 出错！多个参数都是复杂类型，都试图从body中读取，而body只能被读取一次`
    ></font>

    >服务端方法：
    >` void Action([FromUri] Customer c1, Customer c2) // 可以！不同于上面的action，复杂类型c1将从url中读取，c2将从body中读取`

4. ModelBinder方式：

    >`void Action([ModelBinder(MyCustomBinder)] SomeType c) // 标示使用特定的model binder来解析参数`

    >`[ModelBinder(MyCustomBinder)] public class
    >SomeType { } // 通过给特定类型SomeType声明标注[ModelBidner(MyCustomBinder)]特性使得所有SomeType类型参数应用此规则`

    >`void Action(SomeType c) // 由于c的类型为SomeType，因而应用SomeType上的特性决定其采用model binding`

5. 总结：
    1.  默认简单参数都通过URL参数方式传递，例外：
        *  如果路由中包含了Id参数，则id参数通过路由方式传递；

        * 如果参数被标记为[FromBody]，则可以该参数可以为简单参数，客户端通过POST方式传递：$.ajax(url, '=value')，或者$.ajax({url: url, data: {'': 'value'}});

   1.  默认复杂参数(自定义实体类)都通过POST方式传递，例外：
        * 如果参数值被标记为[FromUri]， 则该参数可以为复杂参数；

   2. 被标记为[FromBody]的参数只允许出现一次， 被标记为[FromUri]的参数可以出现多次，如果被标记为[FromUri]的参数是简单参数，该标记可以去掉。

_________________
_________________

# 前端接口请求传参
**我们都知道，前台请求后台控制的方法有get方法和post方法两种，**

**get 和 post 传递参数的不同**
### get 方法:
只支持url传数据，不管你是手动把参数拼接在Url里面还是写在data里面，只要是用get方法，都会自动绑定到url里面的形式传到后台。因此传送基本类型参数时，后台默认从url里面匹配参数，当传送class，实体等复杂参数时，我们必须在后台参数类型前面加上[fromurl]关键字，使后台强制从url里面获取参数，才能够正确的数据交互

***get 利用params 传递参数***
```
request({
    url: '/User/GetUserInfo',
    method: 'get' ,
    params :data
}}
```

### post方法:
只支持body传数据，我们将参数写到data里面传送到后台的时候，数据读是在body里面，因此传送基本类型参数时，后台默认从Body里面匹配参数，当传送class，实体等复杂参数时，我们必须在后台参数类型前面加上[frombodyl]关键字，使后台强制从body里面获取参数，才能够正确的数据交互

***post 利用data 传递参数***
```
request({
    url: ' /User/AddUser" ,
    method : ' post',
    data
})
```



