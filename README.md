# json-server
1. 全局安装json-server

    ```
    npm i -g json-server
    ```
2. 全局安装nodemon 监听mock文件变化

    ```
    npm i -g nodemon
    ```
3. 启动json-server，指定主配置文件，路由配置，中间件配置，端口
    * 单独启动json-server
    
    ```
    json-server mock/mock.js --routes mock/routes.json --middlewares mock/convert.js --watch --port 9090
    ```
    * 同时启动前端项目和json-server

        将mock放在前端项目根目录中，并且package.json 配置命令脚本
        ```
         "mock": "nodemon --watch mock --exec json-server mock/mock.js --routes mock/routes.json --middlewares mock/convert.js --port 9090",
         "mockdev": "npm run mock | npm run dev"
        ```
         mac系统 "mockdev": "npm run mock & npm run dev"

1. routes.json 配置路由映射规则
2. mock.js作为主配置文件  配置对应路由对应的mock json数据存放路径
3. /srv/accountInfo.do?method=getAccountInfo  新建accountInfo文件夹，在该文件夹中新建getAccountInfo文件夹，其中存放多个test.json案例集即对应接口返回的数据
4. 中间件，用以将POST请求转换为GET请求

    ```
      module.exports = (req, res, next) => {
        req.method = 'GET'
        next()
        }
    ```
5. 启动json-server，指定主配置文件，路由配置，中间件配置，端口

    进入项目的根目录下，执行
    ```
    json-server mock/mock.js --routes mock/routes.json --middlewares mock/convert.js --watch --port 8080
    ```
样例：
  --mock/mock.js  当遇到请求路径/login.do时，返回mock/login/login.json中的数据
  ```
  /* 办卡进度查询测试案例 */
  let login = require('./login/login.json')
  module.exports = function () {
    return {
      'login.do': login // 办卡进度查询
    }
  }
  ```
  --mock/routes.json  配置自定义路由，当遇到/CMBANK/pub/xxxx路径时，相当于请求了mock.js主配置文件中的/xxxx，如/CMBANK/pub/login.do相当于访问了/login.do
    ```
  {
    "/CMBANK/pub/*": "/$1",
    "/CMBANK/srv/*": "/$1",
    /CMBANK/srv/installment.do\\?method=:method": "/installmentMethod:method",  
  }
```
  一个.do，多个method的配置规则
  ```
    /CMBANK/srv/installment.do\\?method=:method": "/installmentMethod:method"  
    /CMBANK/srv/installment.do?method=installQuery =>  installmentMETHODinstallQuery
    /CMBANK/srv/installment.do?method=transQuery =>  installmentMETHODtransQuery
```
  --mock/login/login.json	数据文件
```
  {
    "rspCode": "000",
    "rspMsg": "成功"
  }
  ```

        
