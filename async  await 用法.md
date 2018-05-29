## async 和 await 配套使用

### 基本规则
####  async 表示这是一个async函数，await只能用在这个函数里面。
####  await 表示在这里等待promise返回结果了，再继续执行。

####  在vue中的使用方式

####  1.直接调用接口方式
```  javascript
async methodName(){
    let params = {param:param1}
    const response = await axiosMethod(params);
    const {code , data , msg} = response.data;
    //TODO   
    //拿到data 进行后续处理
}
```

####  2.new Promise方式
````  javascript
async methodName(){
    let result = await this.normalMethod(params);
    //result 是收到的data
}
normalMethod(obj){
    return new Promise ((resolve, reject) => {
        setTimeout(() => {
            resolve(data)
        },time)
    })
}
````

####  await等待的虽然是promise对象，但不必写.then(..)，直接可以得到返回值。

####  既然.then(..)不用写了，那么.catch(..)也不用写，可以直接用标准的try catch语法捕捉错误。

```  javascript
async methodName(){
    try {
        let params = {param:param1}
        const response = await axiosMethod(params);
        const {code , data , msg} = response.data;
        //TODO   
        //拿到data 进行后续处理
    } catch (error){
        //错误处理
    }
}
```
