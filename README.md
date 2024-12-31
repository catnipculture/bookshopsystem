> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

系统分为管理员、用户两个角色

用户的主要功能：查看系统信息、注册登录、在线客服、交流论坛、购物车、个人中心、我的发布、我的订单、我的地址、我的收藏

管理员的主要功能：登录、个人中心、用户管理、图书分类管理、图书信息管理、交流论坛、系统管理、订单管理

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：Java、Spring、SpringMVC、Mybatis，SSM

前端：vue

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码地址：[http://www.codegym.top](http://www.codegym.top/)


# 运行截图

## 功能模块截图

![img](https://i-blog.csdnimg.cn/img_convert/cde00b239ff984bb159bbda5d58ddc0a.png)

### 项目截图

前台

![ssm119在线购书商城系统vue2](https://i-blog.csdnimg.cn/img_convert/6b1b97d8664535456c9ac1b4691780fa.png)

![ssm119在线购书商城系统vue3](https://i-blog.csdnimg.cn/img_convert/ad3fef3d99cc0dcd199bd6c64e865e5c.png)

![ssm119在线购书商城系统vue4](https://i-blog.csdnimg.cn/img_convert/252a5dccf357950fde088d619378b4ba.png)

![ssm119在线购书商城系统vue5](https://i-blog.csdnimg.cn/img_convert/65a57ecf1625571c00cc322df5bcb44d.png)

![ssm119在线购书商城系统vue6](https://i-blog.csdnimg.cn/img_convert/9f62f4bacc0e921089cde77e83536f6d.png)

![ssm119在线购书商城系统vue0](https://i-blog.csdnimg.cn/img_convert/8d1687dfc8b921afb3c3be7d81fee564.png)

![ssm119在线购书商城系统vue1](https://i-blog.csdnimg.cn/img_convert/32c3abc5716596e693900fc5b5135a14.png)

![ssm119在线购书商城系统vue4](https://i-blog.csdnimg.cn/img_convert/252a5dccf357950fde088d619378b4ba.png)

![ssm119在线购书商城系统vue5](https://i-blog.csdnimg.cn/img_convert/65a57ecf1625571c00cc322df5bcb44d.png)

![ssm119在线购书商城系统vue6](https://i-blog.csdnimg.cn/img_convert/9f62f4bacc0e921089cde77e83536f6d.png)

后台

![ssm119在线购书商城系统vue7](https://i-blog.csdnimg.cn/img_convert/29d28c379c45e7b401d53dfb4fba633b.png)

![ssm119在线购书商城系统vue8](https://i-blog.csdnimg.cn/img_convert/3f501843147e48c3d7712df41cdc2a49.png)

![ssm119在线购书商城系统vue9](https://i-blog.csdnimg.cn/img_convert/bf045a8751ae5cfbc845dd3b7ce671a6.png)

![ssm119在线购书商城系统vue10](https://i-blog.csdnimg.cn/img_convert/e74fc97221afe39c02434103e0aa0ad2.png)

![ssm119在线购书商城系统vue11](https://i-blog.csdnimg.cn/img_convert/bcd5cef7c7d6f11e76364696165f31e7.png)

### 代码

```
 private UserDO getUserByUserPhone(String currentUserPhone) {
        UserDO userDO = this.baseMapper.selectOne(new LambdaQueryWrapper<UserDO>().eq(UserDO::getTelephone, currentUserPhone));
        if (userDO != null){
            CustomerDO existCustomer = customerMapper.selectOne(new LambdaQueryWrapper<CustomerDO>().eq(CustomerDO::getTelephone, currentUserPhone));
            if (existCustomer != null){
                userDO.setCustomerFlag(isCustomer(existCustomer.getId()));
            }
            userDO.setPlatformFlag(true);
            return userDO;
        }

        //查询顾客信息
        CustomerDO customerDO = customerMapper.selectOne(new LambdaQueryWrapper<CustomerDO>().eq(CustomerDO::getTelephone, currentUserPhone));
        if (customerDO != null){
            UserDO copyUser = new UserDO();
            BeanUtils.copyProperties(customerDO, copyUser);
            copyUser.setCustomerFlag(isCustomer(customerDO.getId()));
            copyUser.setPlatformFlag(false);
            return copyUser;
        }
        throw new BizException("401", "用户不存在");
    }
```
