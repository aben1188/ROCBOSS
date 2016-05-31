## 主要新特性

- 系统架构调整，优化Model层逻辑
- 热点数据缓存，提升负载能力
- 大量采用AJAX和PJAX，提升用户体验和系统运行速度
- 新增发帖、回帖本地自动草稿功能
- 新增图片CDN加速
- 新增支付宝积分充值功能
- 新增会员等级制度（可扩展）
- 新增主题打赏功能
- 新增私信手机短信通知功能
- 新增登录、注册人机行为验证

还有很多细节不一一介绍，留给伙伴们自行发现。

## 安装须知

**环境要求**

1. PHP >= 5.4

2. 部署Redis服务器以及对应的PHP Redis扩展

3. 开启pdo_mysql扩展

4. 支持伪静态

（建议使用Linux操作系统，基本不支持虚拟主机）

**安装步骤**

1. 打开根目录 index.php 文件，按照注释进行完整的配置

2. 导入 install.sql 数据库文件

3. 设置 app/cache 目录777权限

4. 配置文件完全填写结束后，访问首页，管理员登陆后，可进入管理地址 : `你的网址/admin`， 默认管理员 `admin` 密码 `123123123`

5. 关于伪静态，apache环境直接使用 .htaccess 文件，nginx使用如下规则：
    ```
    location / {
        try_files $uri $uri/ /index.php;
    }
    location ~* /app/(views|cache)/(.*)\.php$ {
        deny all;
    }
    ```

6. 由于使用[七牛云存储][1]，所以需要配置图片处理样式，分割符为“ - ”，必须配置，否则图片无法使用

    名称： `800`

    处理接口： 自行控制水印等，宽度800


    名称： `100x100`

    处理接口：`imageView2/1/w/100/h/100/q/100`


    名称：`800.png`

    处理接口：自行控制水印等，宽度800


    名称：`90x68.png`

    处理接口： `imageView2/1/w/90/h/68/q/100/format/png`


    名称：`avatar.png`

    处理接口：`imageView2/1/w/100/h/100/q/100/format/png`


## 附言
由于2.2环境要求比较严格，所以还请耐心安装，相关知识不了解的可以自行搜索相关资料。2.2.0 基于 ROCPHP v1.1，后面将整理出开发文档，另外由于时间问题，本次文章投稿功能暂时没有开发完上线，将于下个2.2.1版本中发布。

  [1]: https://portal.qiniu.com/signup?code=3lho3ffob4oya
