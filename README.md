# JFinal-ext2

#####v2.0.3更新内容
1. 加入 Logger 兼容旧版本JFinal中的 Logger;
2. 更新JFinal版本到正式版本 JFinal2.1;
3. 调整了结构;

#####v2.0.2更新内容
1. 加入 JFinalExt,更方面的获取DEV_MODE,UPLOAD_PATH,DOWNLOAD_PATH,ENCODING;
2. cfg.txt 中加入app.downloads.basedir,设置 app 的 uploads 和 downloads 目录,目录格式为basedir+app_name+文件路径;
3. 删除设计不合理的FileRenamePolicy,保留RandomFileRenamePolicy;
4. 加入UploadPathKit,获取日期格式的 path,比如当前日期是2016-1-7则目录为:/var/uploads/appname/2016/1/7/xxxxx.jpg;
5. 修改OreillyCos默认的 filerenamepolicy 为RandomFileRenamePolicy,可以在configMoreConstants中自行修改;
6. push到中央仓库;
7. 整合 jfinal-ext,修改了 jfinal-ext 中对 jfinal2.1的部分错误;

怎样使用

```java
<dependency>
  <groupId>com.jfinal</groupId>
  <artifactId>jfinal-ext2</artifactId>
  <version>2.0.2</version>
</dependency>
```

#####v2.0.1更新内容
1. 自动 mapping 生成的 model;
2. 在 model 中添加了一个常量 table,为对应的表名,便于在手写 sql 时候使用;

```java
/**
 * Generated by JFinal.
 */
@SuppressWarnings("serial")
public class Zcq extends BaseZcq<Zcq> {
	public static final Zcq dao = new Zcq();
	public static final String table = "zcq";
}
```

3. 修改了 cfg.txt 中数据源的配置格式;

```shell
#--------------------------------------------------------------------#
#  database　Config
# 1. db.ds: db datasource name, use ',' split. eg :mysql,oracle;数据源 name;
# 2. db.*.active:ture, use db,* is the ds name;数据源为*的数据源是否激活;
# 3. db.*.url: db url,* is the ds name;数据源为*的数据库的 url;
# 4. db.*.user: db username,* is the ds name;数据源为*的数据库用户名;
# 5. db.*.password: db password,* is the ds name, 数据源为*的数据库密码,已加密
#	use `java -cp druid-xx.jar com.alibaba.druid.filter.config.ConfigTools your_password`
#	generate your encrypt password;使用com.alibaba.druid.filter.config.ConfigTools获得加密密码;
# 6. db.*.initsize: db pool init size,* is the ds name;数据源为*的连接池初始化大小;
# 7. db.*.maxactive: db pool maxactive,* is the ds name;数据源为*的连接池最大连接数;
# 8. db.showsql: ture, show execute sql;是否显示 sql;
#--------------------------------------------------------------------#
db.ds = mysql
db.mysql.active = false
db.mysql.url = testing_host/db
db.mysql.user = 
db.mysql.password = lCzd9geWAuAuJtLhpaG/J+d28H8KiMFAWopxXkYpMNdUai6Xe/LsPqMQeg5MIrmvtMa+hzycdRhWs29ZUPU1IQ==
db.mysql.initsize = 6
db.mysql.maxactive = 100
db.showsql = true
```

#####v2.0.0更新内容
1. 基于 JFinal2.1;
2. 集成了 JFinal 牛逼的 Generetor, 让你自动生成 model 更Easy:);
3. 修改了配置文件格式,加入了很多的说明;
4. 扩展DruidPlugin做了一个DruidEncryptPlugin,在配置文件中使用加密的数据库密码;
5. 使用 maven 管理项目;

#####配置说明
[手册](MANUAL.md)

基于JFinal 2.0加入一些kit，它们有

1. 扩展JFinalConfig=> JFinalConfigExt

	1.1 给每一个app设置一个name；

	1.2 从配置文件中获取文件的保存路径；

	1.3 获取devmode；

	1.4 打包DruidPlugin和ActiveRecordPlugin；

	以上让你的config更加轻便

2. 加入ActionExtentionHandler
	更方面的伪静态处理

3. 加入 NotFoundActionInterceptor 当找不到对应的 action 时，fire 404

4. com.jfinal.ext2.kit

	3.1 DateTimeKit;

	3.2 DDLKit;

	...

5. com.jfinal.ext2.validate.ValidatorExt

	默认开启短路，校验失败403

6. 加入多个文件上传的FileRenamePolicy
	
	6.1 CustomNameFileRenamePolicy 自定义文件名称
	6.2 CustomParentDirFileRenamePolicy 自定义上级目录名称
	6.3 DateRandomFileRenamePolicy 按照时间分割目录
	6.4 RandomFileRenamePolicy 随机文件名称


Demo ： [http://git.oschina.net/brucezcq/JFinal-Ext2-Demo](http://git.oschina.net/brucezcq/JFinal-Ext2-Demo)
