## 变量

对部署时设定的变量做如下说明。

| 变量 | 默认值 | 说明 |
| :--- | :--- | :--- |
| `DATABASE_URL` | `` | 数据库连接 URL，默认留空为使用本地 sqlite 数据库 |
| `SITE_URL` | `` | 网站URL，比如 https://example.com ，这个地址会在 Alist 程序中的某些地方使用，如果不设置这个字段，一些功能可能无法正常工作。 |
| `TZ` | `UTC` | 时区，国内时区为 Asia/Shanghai。 |

更多变量及说明请参考：

https://github.com/alist-org/alist/blob/main/internal/conf/config.go

https://alist.nn.ci/zh/config/configuration.html

## 数据持久化

有两种解决方法：

1. 在支持持久存储卷的 PaaS 平台上（Northflank 等），可以使用默认的 SQLite 数据库，需要将持久存储卷挂载到 "/data" 目录下 。

2. 在不支持持久存储卷的 PaaS 平台上（Koyeb 等），需要连接 MySQL 或是 PostgreSQL 数据库。

**bit.to 将于 2023.6.29 停止服务**

<details>
<summary><b>  planetscale.com 免费 MySQL 数据库</b></summary>

1. 前往 https://planetscale.com 注册账号，并新建一个数据库。
2. 点击数据库名称，进入数据库管理页面，点击左侧的 "Get connection strings"，在 "connect with" 下拉菜单中选择 Symfony。
3. 下方 "mysql://" 开头字符串即为数据库连接 URL。密码只会显示一次，如果忘记保存了可以点击 "New password" 重新生成。
</details> 

<details>
<summary><b> elephantsql 免费 PostgreSQL 数据库</b></summary>

1. 前往 https://www.elephantsql.com 注册账号，并新建一个数据库。
2. 点击数据库名称，进入数据库管理页面，右侧的 Details 下方，复制 "URL" 项即为数据库连接 URL。
</details>


## 部署方式

**请勿使用本仓库直接部署**

 <details>
<summary><b>Heroku 部署方法</b></summary>

## 首次使用

1. 默认用户名为 admin，密码显示在 PaaS 平台容器初次运行日志中，登录后请尽快修改密码。

2. Aria2 地址为 http://localhost:61800/jsonrpc ，RPC 密钥为空。
