# 新星 Api 项目

```
你的第一款 api 何必是 api
```

---

文件目录

```
- server.js            # 服务器入口文件
- server2.js           # 服务器入口文件(带热更新)
- create_new_api.js    # 创建新的 API 文件脚本
- req_args.js          # 中间件-参数验证等
- res_code.js          # 中间件-自定义状态码
- res_put.js           # 中间件-输出格式化
- private              # 所有api私有文件储存位置
- public               # 所有api公有文件储存位置
- developer_directory  # 开发者目录,禁止公开,用于备忘录等
- open_api/            # 存放所有的 API 文件夹
  - api1/              # API1 文件夹
    - index.js         # API1 路由定义文件
    - api_config.json  # API1 配置文件
  - api2/              # API2 文件夹
    - index.js         # API2 路由定义文件
    - api_config.json  # API2 配置文件
  ...
```

请注意在 github 的忽略文件(.gitignore)文件中有如下内容

```
.vscode/
developer_directory/*
private/*
public/*
system_api/
package.json
README.MD
server.js
server2.js
.git/
```

# 项目必看

```
本项目位于github qingshani的库中
暂定两个分支
        - server : 服务端本体,.
        - apis : 各类api,.
server内负责挂载api,协同,统一输出格式等,一般情况不允许更改
---
所有作者都应统一模板,这样才方便管理


```

> ### 创建新的 API
>
> 0 将 server 分支 clone 到本地以后,执行脚本  
> 1 npm run apii [api 名称]  
> 2 则自动在./open_api 目录下创建[api 名称]的文件夹

> ### res.put 的使用方式
>
> 0 暂时懒得写 反正都是大佬 稍微看几眼就能明白  
> 1 大概的逻辑就是 res.put(data,code=200)  
> 2 code 不填默认 200  
> 3 data 就是你 api 要返回的数据  
> 4 如果 code!=200 则在文件./system_api/main_lang.json 中找对应的状态码然后输出对应数据

> ### req.args 的使用方式
>
> 0 暂时没有任何作用

> ### res.code 的使用方式
>
> 0 暂时没有任何作用

# manifest.json

```json
{
  // API名字
    "api_name": "test",

  // API 作者名称
    "author":"null"

  // API 作者的GITHUB首页地址
    "github":"https://github.com/author"

  // 由系统分配的ID序号 不需要填
    "id": "0",

  // 是公开或者私有?公开任何人都可以访问,私有则有白名单(暂未开发)
    "type": "public",

  // api的状态?normal:一切正常;
  // maintenance:正在维护;
  // delete:表示永久删除;
  // stop:表示没有原因就是必须暂时使用
    "state": "normal",

  // 表示是否需要挂载此api?只有每次启动服务器时才会需要用到
    "open": true,

  // 是否开启参数验证?true/false默认false 至于如何验证请查看文档
    "args_test": false

  // API参数列表,
    "args": {
        "min_length": {}
    }

  // API支持的请求方式GET/POST/DELETE/UPDATA,数组格式,*已废弃
    "method":"GET"
}
```

# 待更新

[*] 访问 http://127.0.0.1:3000/api 时 会直接去验证 apis_info[api]的 open 导致报错  
[*] manifest.json 格式化
