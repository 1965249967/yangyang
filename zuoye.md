### git基础配置
#### 配置用户名
##### git config --global user.name "你的用户名"
#### 配置邮箱
##### git config --global user.email "你的邮箱"
#### 编码设置
##### 避免git gui 中的中文乱码
##### git config --global gui.encoding utf-8
##### 避免git status 显示的中文文件名乱码
##### git config --global core.quotepath off
#### 其他
##### git config --global core.ignorecase false
### git ssh key pair配置
#### 1 在git bash命令行窗口中输入
##### ssh-keygen -t rsa -C "你的邮箱"
#### 2 然后一路回车，不输入任何东西，生成ssh key pair
#### 3 在用户目录下生成.ssh文件夹，找到公钥和私钥 id_rsa id_rsa.pub
#### 4 将公钥的内容复制
#### 5 进入github网站，将公钥添加进去
### git验证
#### 显示版本信息
##### git--version
### git常用命令
#### 创建本地仓库
##### git init
#### 添加到暂存区
##### git add
#### 提交到本地仓库
##### git commit -m "描述"
#### 检查工作区文件状态
##### git status
#### 查看提交committid
##### git log
#### 版本回退
##### git reset --hard committid
#### 查看分支
##### git branch
#### 创建并切换到dev分支
##### git checkout -b dev
#### 切换分支
##### git checkout 分支名
#### 拉取
##### git pull
#### 提交
##### git push -u origin master
#### 分之合并
##### git merge branch name
#### 本地仓库与远程仓库关联
#####  git remote add origin "远程仓库地址"
#### 第一次向远程仓库推送
##### git push -u -f origin master
#### 以后提交到远程
##### git push origin master
#### 创建分支
##### git checkout -b v1.0 origin/master
#### 将分支推送到远程
##### git push origin HEAD -u
#### 提交所有
##### git add  .
### .gitignore文件：告诉Git哪些文件不需要添加到版本管理中
#### 忽略规则
##### *.a  忽略所有.a结尾的文件
##### ！lib.a  lib.a文件除外
##### /TODO  仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
##### build/  忽略 build/ 目录下的所有文件
##### doc/*.txt  忽略 doc/notes.txt 但不包括 doc/server/arch.txt
------------20181204------------
###远程分支合并dev分支
#### git checkout dev
#### git pull origin dev
#### git checkout master
#### git merge dev
#### git push origin master

### 数据库设计
#### 创建数据库
```
create database ilearnshopping;
```
#### 用户表
```
create table neuedu_user(
`id`             int(11)   not null auto_increment  comment '用户id',
`username`       varchar(50) not null  comment '用户名',
`password`       varchar(50) not null  comment '密码',
`email`          varchar(50) not null  comment '邮箱',
`phone`          varchar(11) not null  comment '联系方式',
`question`       varchar(100) not null comment '密保问题',
`answer`         varchar(100) not null comment '答案',
`role`           int(4)       not null default 0 comment '用户角色',
`create_time`    datetime     comment '创建时间',
`update_time`    datetime     comment '修改时间',
PRIMARY KEY (`id`),
UNIQUE KEY `user_name_index`(`username`) USING BTREE
)ENGINE=InnoDB DEFAULT CHARSET=UTF8;
```
#### 类别表
create table neuedu_category(
`id`           int(11)  not null   auto_increment  comment '类别id',
`parent_id`    int(11)  not null  default 0 comment '父类id',
`name`         varchar(50)  not null  comment '类别名称',
`status`       int(4)  default 1 comment '类别状态 1:正常 0:废弃',
`create_time`    datetime     comment '创建时间',
`update_time`    datetime     comment '修改时间',
PRIMARY KEY (`id`)
)ENGINE=InnoDB DEFAULT CHARSET=UTF8;
#### 商品表
#### 购物车表
#### 订单表
#### 订单明细表
#### 支付表
#### 地址表