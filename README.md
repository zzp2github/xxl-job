# 《分布式任务调度平台XXL-JOB》(最新版本V1.4.2-SNAPSHOT)
## 一、简介

#### 1.1 概述
XXL-JOB是一个轻量级分布式任务调度框架，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。现已开放源代码并接入多家公司线上产品线，开箱即用。

#### 1.2 特性
- 1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；
- 2、动态：支持动态修改任务状态、暂停/恢复任务，以及终止运行中任务，即时生效；
- 3、调度HA：“调度中心”基于集群Quartz实现，可保证调度中心HA；
- 4、任务HA：任务支持多地址配置，可保证任务执行HA；
- 5、任务Failover：多地址配置时，调度失败时将会平滑切换执行器进行Failover；
- 6、一致性：“调度中心”通过DB锁保证集群分布式调度的一致性；
- 7、自定义任务参数：支持在线配置调度任务入参，即时生效；
- 8、调度线程池：调度系统多线程触发调度运行，确保调度精确执行，不被堵塞；
- 9、执行日志：支持在线查看调度结果，并且查看完整的执行日志；
- 10、邮件报警：任务失败时支持邮件报警，支持配置多邮件地址群发报警邮件；
- 11、支持登录验证；
- 12、GLUE：提供Web IDE，支持在线开发任务逻辑代码，动态发布，实时编译生效，省略部署上线的过程。支持30个版本的历史版本回溯。
- 13、数据加密：调度中心和执行器之间的通讯进行数据加密，提升调度信息安全性；
- 14、任务依赖：支持配置子任务依赖，当父任务执行结束且执行成功后将会主动触发一次子任务的执行, 多个子任务用逗号分隔；
- 15、推送maven中央仓库: 将会把最新稳定版推送到maven中央仓库, 方便用户接入和使用;

#### 1.3 发展
于2015年中，我在github上创建XXL-JOB项目仓库并提交第一个commit，随之进行系统结构设计，UI选型，交互设计……

于2015-11月，XXL-JOB终于REALEASE了第一个大版本V1.0， 随后我将之发布到OSCHINA，XXL-JOB在OSCHINA上获得了@红薯的热门推荐，同期分别达到了OSCHINA的“热门动弹”排行第一和git.oschina的开源软件月热度排行第一，在此特别感谢红薯，感谢大家的关注和支持。

于2015-12月，我将XXL-JOB发表到我司内部知识库，并且得到内部同事认可。

于2016-01月我司展开XXL-JOB的内部接入和定制工作，在此感谢袁某和尹某两位同事的贡献，同时也感谢内部其他给与关注与支持的同事。

**我司大众点评目前已接入XXL-JOB，内部别名《Ferrari》（Ferrari基于XXL-JOB的V1.1版本定制而成，新接入应用推荐升级最新版本）**。据最新统计, 自2016-01-21接入至2016-07-20期间，该系统已调度72000余次，表现优异。新接入应用推荐使用最新版本，因为经过数个大版本的更新，系统的任务模型、UI交互模型以及底层调度通讯模型都有了较大的优化和提升，核心功能更加稳定高效。

至今，XXL-JOB已接入多家公司的线上产品线，接入场景如电商业务，O2O业务和大数据作业等，截止2016-07-19为止，XXL-JOB已接入的公司包括不限于：
    
	- 1、大众点评；
	- 2、山东学而网络科技有限公司；
	- 3、安徽慧通互联科技有限公司；
	- 4、人人聚财金服；
	- 5、上海棠棣信息科技股份有限公司
	- 6、运满满
	- 7、米其林(中国区)
	- 8、妈妈联盟
	- 9、九樱天下（北京）信息技术有限公司
	- 10、万普拉斯科技有限公司(一加手机)
	- 11、上海亿保健康管理有限公司
	- ……

欢迎大家的关注和使用，XXL-JOB也将拥抱变化，持续发展。

#### 1.4 下载
##### 源码地址 (将会在两个git仓库同步发布最新代码)

- [github地址](https://github.com/xuxueli/xxl-job)
- [git.osc地址](http://git.oschina.net/xuxueli0323/xxl-job)

##### 中央仓库地址 (将会把最新稳定版本的公共依赖,推送到中央仓库)
    ```
    <!-- http://repo1.maven.org/maven2/com/xuxueli/xxl-job-core/ -->
    <dependency>
        <groupId>com.xuxueli</groupId>
        <artifactId>xxl-job-core</artifactId>
        <version>1.4.1</version>
    </dependency>
    ```

##### 博客地址 (将会在两个博客同步更新文档)

- [oschina地址](http://my.oschina.net/xuxueli/blog/690978)
- [cnblogs地址](http://www.cnblogs.com/xuxueli/p/5021979.html)

##### 技术交流群(仅作技术交流)：367260654    [![image](http://pub.idqqimg.com/wpa/images/group.png)](http://shang.qq.com/wpa/qunwpa?idkey=4686e3fe01118445c75673a66b4cc6b2c7ce0641528205b6f403c179062b0a52 )


##### Download: 历史Release版本下载位置如下图所示,请自行前往进行选择和下载。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23221244_nq9a.png "在这里输入图片标题")

#### 1.5 环境
- Maven3+
- Jdk1.7+
- Tomcat7+
- Mysql5.5+


## 二、快速入门

#### 2.1 初始化“调度数据库”
请下载项目源码并解压，获取 "调度数据库初始化SQL脚本"(脚本文件为: 源码解压根目录\xxl-job\db\tables_xxl_job.sql) 并执行即可。

正常情况下,应该生成如下图所示14张表;

![输入图片说明](https://static.oschina.net/uploads/img/201607/23221308_DDW8.png "在这里输入图片标题")

调度中心集群情况下,集群节点务必连接同一个mysql实例;如果mysql做主从,调度中心集群节点务必强制走主库;

#### 2.2 编译源码
解压源码,按照maven格式将源码导入IDE, 使用maven进行编译即可，源码结构如下图所示：


![输入图片说明](https://static.oschina.net/uploads/img/201607/23222522_JGCc.png "在这里输入图片标题")

    - xxl-job-admin：调度中心
    - xxl-job-core：公共依赖
    - xxl-job-executor-example：执行器（可直接使用该执行器，也可以将现有项目改造成执行器使用）

#### 2.3 配置部署“调度中心”
调度中心项目：xxl-job-admin

作用：统一管理任务调度平台上调度任务，负责触发调度执行。

- **A：配置调度中心JDBC链接**：请在下图所示位置配置jdbc链接地址，链接地址请保持和 2.1章节 所创建的调度数据库的地址一致。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23222438_wZv9.png "在这里输入图片标题")

- **B：配置报警邮箱和登陆账号**：请在下图所示位置，设置自己的报警邮件发送邮箱和登陆账号密码。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23223008_ArvZ.png "在这里输入图片标题")

- **C：配置“调度中心”任务执行结果回调端口**：由于“调度中心”和“执行器”部署在不同项目中，“执行器”会请求该端口回调通知任务执行结果。如下图所示，默认回调服务端口号为8888。（此端口除非与现有端口冲突，可自行修改，否则可忽视）

![输入图片说明](https://static.oschina.net/uploads/img/201607/23223301_I03k.png "在这里输入图片标题")

**部署项目**：如果已经正确进行上述配置，可将项目编译打war包并部署到tomcat中。

访问链接：http://localhost:8080/xxl-job-admin/ ，登陆界面如下图所示


![输入图片说明](https://static.oschina.net/uploads/img/201607/23223648_b8Dx.png "在这里输入图片标题")

至此“调度中心”项目已经部署成功。

#### 2.4 配置部署“执行器项目”
“执行器”项目：xxl-job-executor-example

作用：负责接收“调度中心”的调度并执行；

- **A：配置Jdbc链接**：请在下图所示位置配置jdbc链接地址，链接地址请保持和 2.1章节 所创建的调度数据库的地址一致。


![输入图片说明](https://static.oschina.net/uploads/img/201607/23224042_MeRg.png "在这里输入图片标题")

- **B：配置“执行器”端口**：由于“调度中心”和“执行器”部署在不同项目，“调度中心”会请求该端口触发任务执行。端口如下图所示，默认的“执行器”端口是9999，如果与系统现有端口冲突可自行修改，如若不冲突，可忽略。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23224304_0jxT.png "在这里输入图片标题")

**部署项目**：如果已经正确进行上述配置，可将项目编译打war包并部署到tomcat中。

至此“执行器”项目已经部署结束。

#### 2.5 开发第一个任务“Hello World”
本示例为新建一个“GLUE模式任务”（“GLUE模式任务”的执行代码支持托管到调度中心在线维护，相比“Bean模式任务”需要在执行器项目开发部署上线，更加简便轻量）。更多有关任务的详细配置，请查看“章节三：任务详解”。

**前提：请确认“调度中心”和“执行器”项目已经成功部署并启动；**

- **步骤一（新建任务）**：登陆调度中心，点击下图所示“新建任务”按钮，新建示例任务。然后，参考下面截图中任务的参数配置，点击保存。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24191531_2qRI.png "在这里输入图片标题")

![输入图片说明](https://static.oschina.net/uploads/img/201607/24192014_9YEz.png "在这里输入图片标题")

- **步骤二（GLUE任务开发）**：请点击下图中所示“GLUE入口按钮”，进入“GLUE编辑器开发界面”，见下图。GLUE任务默认已经初始化了示例任务代码，即打印Hello World。
（GLUE实际上是一段继承自IJobHandler的Java类代码，它在执行器项目中运行，可使用@Resource/@Autowire注入执行器里中的其他服务，详细介绍请查看第三章节）


![输入图片说明](https://static.oschina.net/uploads/img/201607/23225310_RYby.png "在这里输入图片标题")


![输入图片说明](https://static.oschina.net/uploads/img/201607/23225327_Y1cn.png "在这里输入图片标题")

- **步骤三（触发执行）**：点击下图所示“执行”按钮，可手动触发一次任务执行（通常情况下，通过配置Cron表达式进行任务调度出发）。


![输入图片说明](https://static.oschina.net/uploads/img/201607/23225653_iY9K.png "在这里输入图片标题")

- **步骤四（查看日志）**：
点击图2.5F所示“日志”按钮，可前往任务日志界面查看任务日志。
在如图2.5G的任务日志界面中，可查看任务调度状态，执行器接收到调度请求后的执行状态。
同时，点击如图2.5G中的“执行日志”按钮，可以查看本此调度在执行器端的完整执行日志，完整执行日志如图2.5H。


![输入图片说明](https://static.oschina.net/uploads/img/201607/23225953_7ey7.png "在这里输入图片标题")

（图2.5F：“调度中心”管理管理界面，任务日志入口）


![输入图片说明](https://static.oschina.net/uploads/img/201607/23230953_BFVV.png "在这里输入图片标题")

（图2.5G：“调度中心”管理管理界面，任务日志入口）


![输入图片说明](https://static.oschina.net/uploads/img/201607/23230416_2cLu.png "在这里输入图片标题")

（图2.5H：“调度中心”管理管理界面，任务日志入口）

## 三、任务详解

**配置属性详细说明：**
    - 任务组：任务的分组，便于任务管理；
    - 描述：任务的描述信息，便于任务管理；
    - 执行器地址：执行器接受任务调度的地址，格式为“IP:Port”，支持配置多个地址进行Failover，当存在多个地址时用逗号分隔，格式为“IP1:Port,IP2:Port...”
    - Cron：触发任务执行的Cron表达式；
    - JobHandler + GLUE复选框：
        BEAN模式任务：不选中GLUE复选框，JobHandler输入框为必填项，需要输入该任务对应的JobHandler的名称，即执行器中新开发的JobHandler类“@JobHander”注解自定义的value值；
        GLUE模式任务：选中GLUE复选框，JobHandler输入框被禁用，不必输入，因为此时任务逻辑维护在线上。
    - 执行参数：任务执行所需的参数，多个参数时用逗号分隔，任务执行时将会把多个参数抓换成数组传入；
    - 报警邮件：任务调度失败时邮件通知的邮箱地址，支持配置多邮箱地址，配置多个邮箱地址时用逗号分隔；
    - 负责人：任务的负责人；
    - 子任务Key：每个任务都拥有一个唯一的任务Key(任务Key可以从任务列表获取)，当本任务执行结束并且执行成功时，将会触发子任务Key所对应的任务的一次主动调度。

#### 3.1 BEAN模式任务
Bean模式任务：任务逻辑以JobHandler的形式存在于“执行器”所在项目中，开发流程如下：

- **步骤一：执行器项目中，开发JobHandler**：
    - 1、 新建一个继承com.xxl.job.core.handler.IJobHandler的Java类；
    - 2、 该类被Spring容器扫描为Bean实例，如加“@Service注解”；
    - 3、 添加 “@JobHander(value="自定义jobhandler名称")”注解，注解的value值为自定义的JobHandler名称，该名称对应的是调度中心新建任务的JobHandler属性的值。
    （可参考xxl-job-executor-example项目中的DemoJobHandler，见下图）

![输入图片说明](https://static.oschina.net/uploads/img/201607/23232347_oLlM.png "在这里输入图片标题")

- **步骤二：调度中心，新建调度任务并配置（BEAN模式）**，

参考上文“配置属性详细说明”对新建的任务进行参数配置，需要注意的是“JobHandler + GLUE复选框”任务属性，需要按照“GLUE模式”任务进行配置；

![输入图片说明](https://static.oschina.net/uploads/img/201607/24191939_pWgf.png "在这里输入图片标题")

#### 3.2 GLUE模式任务
GLUE模式任务：任务逻辑以GLUE代码的形式存储在DB中，支持通过Web IDE在线更新，实时编译和生效，因此不需要指定JobHandler。开发流程如下：

- **步骤一：调度中心，新建调度任务并配置（GLUE模式）**：

参考上文“配置属性详细说明”对新建的任务进行参数配置，需要注意的是“JobHandler + GLUE复选框”任务属性，需要按照“GLUE模式”任务进行配置；

![输入图片说明](https://static.oschina.net/uploads/img/201607/24192014_9YEz.png "在这里输入图片标题")

- **步骤二：开发GLUE代码**：

选中指定任务，点击该任务右侧“GLUE”按钮（仅GLUE模式任务支持），将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（当然也可以在IDE中开发完成后，复制粘贴到编辑中），可使用@Resource或@Autoward注解注入“执行器”项目中的Spring服务；

版本回溯功能（支持30个版本的版本回溯）：可参考下图，选择下拉框“版本回溯”，会列出该GLUE的更新历史，选择相应版本即可显示该版本代码，保存后GLUE代码即回退到对应的历史版本；

## 四、任务管理
#### 4.1 新建任务
进入任务管理界面，点击“新增任务”按钮，在弹出的“新增任务”界面配置任务属性后保存即可，可参考下图：

![输入图片说明](https://static.oschina.net/uploads/img/201607/24123920_b9UQ.png "在这里输入图片标题")

![输入图片说明](https://static.oschina.net/uploads/img/201607/24192243_9NvE.png "在这里输入图片标题")

#### 4.2 编辑任务
进入任务管理界面，选中指定任务。点击该任务右侧“编辑”按钮，在弹出的“编辑任务”界面更新任务属性后保存即可，可参考下图：

![输入图片说明](https://static.oschina.net/uploads/img/201607/24124734_UYp2.png "在这里输入图片标题")

![输入图片说明](https://static.oschina.net/uploads/img/201607/24192805_Yhmj.png "在这里输入图片标题")

#### 4.3 编辑GLUE代码

该操作仅针对GLUE任务。

GLUE任务开发：进入任务管理界面，选中指定任务。点击该任务右侧“GLUE”按钮（仅GLUE模式任务支持），将会前往GLUE任务的Web IDE界面，在该界面支持对任务代码进行开发（当然也可以在IDE中开发完成后，复制粘贴到编辑中）

版本回溯功能（支持30个版本的版本回溯）：可参考下图，选择下拉框“版本回溯”，会列出该GLUE的更新历史，选择相应版本即可显示该版本代码，保存后GLUE代码即回退到对应的历史版本；

![输入图片说明](https://static.oschina.net/uploads/img/201607/24125405_tk1u.png "在这里输入图片标题")

![输入图片说明](https://static.oschina.net/uploads/img/201607/24125452_qwGM.png "在这里输入图片标题")

#### 4.4 暂停/恢复任务
可对任务进行“暂停”和“恢复”操作。
需要注意的是，此处的暂停/恢复仅针对任务的后续调度触发行为，不会影响到已经触发的调度任务，如需终止已经触发的调度任务，可查看“4.8 终止运行中的任务”

![输入图片说明](https://static.oschina.net/uploads/img/201607/24130337_ZAhX.png "在这里输入图片标题")

#### 4.5 手动触发一次调度
点击“执行”按钮，可手动触发一次任务调度，不影响原有调度规则。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24133348_Z5wp.png "在这里输入图片标题")

#### 4.6 查看调度日志
点击“日志”按钮，可以查看任务历史调度日志。在历史调入日志界面可查看每次任务调度的调度结果、执行结果等，点击“执行日志”按钮可查看执行器完整日志。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24133500_9235.png "在这里输入图片标题")

![输入图片说明](https://static.oschina.net/uploads/img/201607/24134148_6xpS.png "在这里输入图片标题")

调度日志，针对单次调度，属性说明如下：
- 执行器地址：任务执行的机器地址；
- JobHandler：Bean模式表示任务执行的JobHandler名称；
- 任务参数：任务执行的入参；
- 调度时间：调度中心，发起调度的时间；
- 调度结果：调度中心，发起调度的结果，SUCCESS或FAIL；
- 调度备注：调度中心，发起调度的备注信息，如地址心跳检测日志等；
- 执行时间：执行器，任务执行结束后回调的时间；
- 执行结果：执行器，任务执行的结果，SUCCESS或FAIL；
- 执行备注：执行器，任务执行的备注信息，如异常日志等；
- 执行日志：任务执行过程中，业务代码中打印的完整执行日志，见“4.7 查看执行日志”；

#### 4.7 查看执行日志
点击执行日志右侧的 “执行日志” 按钮，可跳转至执行日志界面，可以查看业务代码中打印的完整日志，如下图；

![输入图片说明](https://static.oschina.net/uploads/img/201607/24134243_BGuL.png "在这里输入图片标题")

#### 4.8 终止运行中的任务
仅针对执行中的任务。
在任务日志界面，点击右侧的“终止任务”按钮，将会向本次任务对应的执行器发送任务终止请求，将会终止掉本次任务，同时会清空掉整个任务执行队列。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24140048_hIci.png "在这里输入图片标题")

任务终止时通过 "interrupt" 执行线程的方式实现, 将会触发 "InterruptedException" 异常。因此如果JobHandler内部catch到了该异常并消化掉的话, 任务终止功能将不可用。

因此, 如果遇到上述任务终止不可用的情况, 需要在JobHandler中应该针对 "InterruptedException" 异常进行特殊处理 (向上抛出) , 正确逻辑如下:
```
try{
    // TODO
} catch (Exception e) {
    if (e instanceof InterruptedException) {
        throw e;
    }
    logger.warn("{}", e);
}
```

#### 4.9 删除任务
点击删除按钮，可以删除对应任务。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24140641_Z9Qr.png "在这里输入图片标题")

## 五、总体设计
#### 5.1 源码目录介绍
    - /doc :文档资料
    - /db :“调度数据库”建表脚本
    - /xxl-job-admin :调度中心，项目源码
    - /xxl-job-core :公共Jar依赖
    - /xxl-job-executor-example :执行器，Demo项目源码（大家可以在该项目上进行开发，也可以将现有项目改造生成执行器项目）

#### 5.2 “调度数据库”配置
XXL-JOB调度模块基于Quartz集群实现，其“调度数据库”是在Quartz的11张集群mysql表基础上扩展而成。

XXL-JOB首先定制了Quartz原生表结构前缀（XXL_JOB_QRTZ_）。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24143957_bNwm.png "在这里输入图片标题")

然后，在此基础上新增了三张扩展表，如下：
    - XXL_JOB_QRTZ_TRIGGER_INFO：调度扩展信息表： 用于保存XXL-JOB调度任务的扩展信息，如任务分组、任务名、机器地址、执行器、执行入参和报警邮件等等；
    - XXL_JOB_QRTZ_TRIGGER_LOG：调度日志表： 用于保存XXL-JOB任务调度的历史信息，如调度结果、执行结果、调度入参、调度机器和执行器等等；
    - XXL_JOB_QRTZ_TRIGGER_LOGGLUE：任务GLUE日志：用于保存GLUE更新历史，用于支持GLUE的版本回溯功能；

因此，XXL-JOB调度数据库共计用于14张数据库表。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23221308_DDW8.png "在这里输入图片标题")

#### 5.3 架构设计
##### 5.3.1 设计思想
将调度行为抽象形成“调度中心”公共平台，而平台自身并不承担业务逻辑，“调度中心”负责发起调度请求。

将任务抽象成分散的JobHandler，交由“执行器”统一管理，“执行器”负责接收调度请求并执行对应的JobHandler中业务逻辑。

因此，“调度”和“任务”两部分可以相互解耦，提高系统整体稳定性和扩展性；

##### 5.3.2 系统组成
- **调度模块（调度中心）**：
    负责管理调度信息，按照调度配置发出调度请求，自身不承担业务代码。调度系统与任务解耦，提高了系统可用性和稳定性，同时调度系统性能不再受限于任务模块；
    支持可视化、简单且动态的维管理调度信息，包括任务新建，更新，删除，GLUE开发和任务报警等，所有上述操作都会实时生效，同时支持监控调度结果以及执行日志，支持执行器Failover。
- **执行模块（执行器）**：
    负责接收调度请求并执行任务逻辑。任务模块专注于任务的执行等操作，开发和维护更加简单和高效；
    接收“调度中心”的执行请求、终止请求和日志请求等。

##### 5.3.3 架构图（绘制中）
![输入图片说明](https://static.oschina.net/uploads/img/201607/24144555_SUI2.png "在这里输入图片标题")

#### 5.4 调度模块剖析
##### 5.4.1 quartz的不足
Quartz作为开源作业调度中的佼佼者，是作业调度的首选。但是集群环境中Quartz采用API的方式对任务进行管理，从而可以避免上述问题，但是同样存在以下问题：
    - 问题一：调用API的的方式操作任务，不人性化；
    - 问题二：需要持久化业务QuartzJobBean到底层数据表中，系统侵入性相当严重。
    - 问题三：调度逻辑和QuartzJobBean耦合在同一个项目中，这将导致一个问题，在调度任务数量逐渐增多，同时调度任务逻辑逐渐加重的情况加，此时调度系统的性能将大大受限于业务；
XXL-JOB弥补了quartz的上述不足之处。

##### 5.4.2 RemoteHttpJobBean
常规Quartz的开发，任务逻辑一般维护在QuartzJobBean中，耦合很严重。XXL-JOB中“调度模块”和“任务模块”完全解耦，调度模块中的所有调度任务使用同一个QuartzJobBean，即RemoteHttpJobBean。不同的调度任务将各自参数维护在各自扩展表数据中，当触发RemoteHttpJobBean执行时，将会解析不同的任务参数发起远程调用，调用各自的远程执行器服务。

这种调用模型类似RPC调用，RemoteHttpJobBean提供调用代理的功能，而执行器提供远程服务的功能。

##### 5.4.3 调度中心HA（集群）
基于Quartz的集群方案，数据库选用Mysql；集群分布式并发环境中使用QUARTZ定时任务调度，会在各个节点会上报任务，存到数据库中，执行时会从数据库中取出触发器来执行，如果触发器的名称和执行时间相同，则只有一个节点去执行此任务。

```
# for cluster
org.quartz.jobStore.tablePrefix = XXL_JOB_QRTZ_
org.quartz.scheduler.instanceId: AUTO
org.quartz.jobStore.class: org.quartz.impl.jdbcjobstore.JobStoreTX
org.quartz.jobStore.isClustered: true
org.quartz.jobStore.clusterCheckinInterval: 1000
```

##### 5.4.4 调度线程池
默认线程池中线程的数量为10个，避免单线程因阻塞而引起任务调度延迟。

```
org.quartz.threadPool.class: org.quartz.simpl.SimpleThreadPool
org.quartz.threadPool.threadCount: 10
org.quartz.threadPool.threadPriority: 5
org.quartz.threadPool.threadsInheritContextClassLoaderOfInitializingThread: true
```

##### 5.4.5 @DisallowConcurrentExecution
XXL-JOB调度模块的“调度中心”默认不使用该注解，即默认开启并行机制，因为RemoteHttpJobBean为公共QuartzJobBean，这样在多线程调度的情况下，调度模块被阻塞的几率很低，大大提高了调度系统的承载量。

XXL-JOB的每个调度任务虽然在调度模块是并行调度执行的，但是任务调度传递到任务模块的“执行器”确实串行执行的，同时支持任务终止。

##### 5.4.6 misfire
错过了触发时间，处理规则。
可能原因：服务重启；调度线程被QuartzJobBean阻塞，线程被耗尽；某个任务启用了@DisallowConcurrentExecution，上次调度持续阻塞，下次调度被错过；

quartz.properties中关于misfire的阀值配置如下，单位毫秒：
```
org.quartz.jobStore.misfireThreshold: 60000
```

Misfire规则：
    withMisfireHandlingInstructionDoNothing：不触发立即执行，等待下次调度；
    withMisfireHandlingInstructionIgnoreMisfires：以错过的第一个频率时间立刻开始执行；
    withMisfireHandlingInstructionFireAndProceed：以当前时间为触发频率立刻触发一次执行；

XXL-JOB默认misfire规则为：withMisfireHandlingInstructionDoNothing

```
CronScheduleBuilder cronScheduleBuilder = CronScheduleBuilder.cronSchedule(jobInfo.getJobCron()).withMisfireHandlingInstructionDoNothing();
CronTrigger cronTrigger = TriggerBuilder.newTrigger().withIdentity(triggerKey).withSchedule(cronScheduleBuilder).build();
```

##### 5.4.7 日志回调服务
调度模块的“调度中心”作为Web服务单独部署，除此之外，内部嵌入jetty服务器提供日志回调服务。

“执行器”在接收到任务执行请求后，执行任务，在执行结束之后会将执行结果回调通知“调度中心”，回调端口如下图所示。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23223301_I03k.png "在这里输入图片标题")

##### 5.4.8 任务HA（Failover）
任务“执行器地址”支持配置多个，用逗号分隔，如“127.0.0.1:9998,127.0.0.1:9999”。

如果任务配置多个执行器地址，当调度中心每次发起调度请求时，会按照地址配置的顺序依次对执行器发出心跳检测请求，第一个检测为存活状态的执行器将会被选定。

调度成功后，可在日志监控界面查看“调度备注”，如下；
![输入图片说明](https://static.oschina.net/uploads/img/201607/24150809_TNqT.png "在这里输入图片标题")

“调度备注”可以查看执行器地址选择日志，任务配置的地址“227.0.0.1:9999,127.0.0.1:9999”，首先对第一个执行器地址“227.0.0.1:9999”进行心跳检测，心跳失败因此跳过；然后对第二个执行器地址“127.0.0.1:9999”进行心跳检测，心跳检测成功，选定为“目标执行器”；然后对“目标执行器”发送调度请求，调度流程结束，等待执行器回调执行结果。

##### 5.4.9 调度日志
调度中心每次进行任务调度，都会记录一条任务日志，任务日志主要包括以下三部分内容：

- 任务信息：包括“执行器地址”、“JobHandler”和“执行参数”等属性，根据这些参数，可以精确的定位任务执行的具体机器和任务代码；
- 调度信息：包括“调度时间”、“调度结果”和“调度日志”等，根据这些参数，可以了解“调度中心”发起调度请求时具体情况。
- 执行信息：包括“执行时间”、“执行结果”和“执行日志”等，根据这些参数，可以了解在“执行器”端任务执行的具体情况；


![输入图片说明](https://static.oschina.net/uploads/img/201607/24134148_6xpS.png "在这里输入图片标题")

调度日志，针对单次调度，属性说明如下：
- 执行器地址：任务执行的机器地址；
- JobHandler：Bean模式表示任务执行的JobHandler名称；
- 任务参数：任务执行的入参；
- 调度时间：调度中心，发起调度的时间；
- 调度结果：调度中心，发起调度的结果，SUCCESS或FAIL；
- 调度备注：调度中心，发起调度的备注信息，如地址心跳检测日志等；
- 执行时间：执行器，任务执行结束后回调的时间；
- 执行结果：执行器，任务执行的结果，SUCCESS或FAIL；
- 执行备注：执行器，任务执行的备注信息，如异常日志等；
- 执行日志：任务执行过程中，业务代码中打印的完整执行日志，见“4.7 查看执行日志”；

##### 5.4.10 任务依赖
原理：XXL-JOB中每个任务都对应有一个任务Key，同时，每个任务支持设置属性“子任务Key”，因此，通过“任务Key”可以匹配任务依赖关系。

当父任务执行结束并且执行成功时，将会根据“子任务Key”匹配子任务依赖，如果匹配到子任务，将会主动触发一次子任务的执行。

在任务日志界面，点击任务的“执行备注”的“查看”按钮，可以看到匹配子任务以及触发子任务执行的日志信息，如无信息则表示未触发子任务执行，可参考下图。

![输入图片说明](https://static.oschina.net/uploads/img/201607/24194134_Wb2o.png "在这里输入图片标题")

![输入图片说明](https://static.oschina.net/uploads/img/201607/24194212_jOAU.png "在这里输入图片标题")

#### 5.5 执行模块剖析
##### 5.5.1 Bean模式任务
开发步骤：见章节三；
原理：每个Bean模式任务都是一个Spring的Bean类实例，它被维护在“执行器”项目的Spring容器中。任务类需要加“@JobHander(value="名称")”注解，因为“执行器”会根据该注解识别Spring容器中的任务。任务类需要继承统一接口“IJobHandler”，任务逻辑在execute方法中开发，因为“执行器”在接收到调度中心的调度请求时，将会调用“IJobHandler”的execute方法，执行任务逻辑。

##### 5.5.2 GLUE模式任务
开发步骤：见章节三；
原理：每个Glue任务的代码，实际上是“一个继承自“IJobHandler”的实现类的类代码”，“执行器”接收到“调度中心”的调度请求时，会通过Groovy类加载器加载此代码，实例化成Java对象，同时注入此代码中声明的Spring服务（请确保Glue代码中的服务和类引用在“执行器”项目中存在），然后调用该对象的execute方法，执行任务逻辑。

##### 5.5.3 执行器
执行器实际上是一个内嵌的Jetty服务器，默认端口9999。

![输入图片说明](https://static.oschina.net/uploads/img/201607/23224304_0jxT.png "在这里输入图片标题")

在项目启动时，执行器会通过“@JobHander”识别Spring容器中“Bean模式任务”，以注解的value属性为key管理起来。

“执行器”接收到“调度中心”的调度请求时，如果任务类型为“Bean模式”，将会匹配Spring容器中的“Bean模式任务”，然后调用其execute方法，执行任务逻辑。如果任务类型为“GLUE模式”，将会加载GLue代码，实例化Java对象，注入依赖的Spring服务（注意：Glue代码中注入的Spring服务，必须存在与该“执行器”项目的Spring容器中），然后调用execute方法，执行任务逻辑。

##### 5.5.4 任务日志
XXL-JOB会为每次调度请求生成一个单独的日志文件，通过重写LOG4J的Appender实现，“调度中心”查看执行日志时将会加载对应的日志文件。

需要注意的是，“执行器”中日志Appender上配置的包名，需要覆盖到所有任务（Bean模式 + GLUE模式）的包名，否则覆盖不到的任务将不会生成日志文件。

```
// 以下代码见/xxl-job/xxl-job-executor-example/src/main/resources/log4j.xml文件
<appender name="xxl-job" class="com.xxl.job.core.log.XxlJobFileAppender">
    <param name="filePath" value="/data/applogs/xxl-job/jobhandler/"/>
    <param name="append" value="true"/>
    <param name="encoding" value="UTF-8"/>
    <layout class="org.apache.log4j.PatternLayout">
        <param name="ConversionPattern" value="%-d{yyyy-MM-dd HH:mm:ss} [%c]-[%t]-[%M]-[%L]-[%p] %m%n"/>
    </layout>
</appender>
...
<logger name="com.xxl.job.executor.service.jobhandler" additivity="false">
    <level value="INFO" />
    <appender-ref ref="CONSOLE" />
    <appender-ref ref="FILE" />
    <appender-ref ref="xxl-job"/>
</logger>
```

单独日志文件存放的位置可在“执行器”的log.xml文件进行自定义，默认位置为项目磁盘根目录下“/data/applogs/xxl-job/jobhandler/”；

目录格式为：/data/applogs/xxl-job/jobhandler/“格式化日期”/“数据库调度日志记录的主键ID.log”。

#### 5.6 通讯模块剖析

##### 5.6.1 一次完整的任务调度通讯流程 
    - 1、“调度中心”向“执行器”发送http调度请求: “执行器”中接收请求的服务，实际上是一台内嵌jetty服务器，默认端口9999;
    - 2、“执行器”执行任务逻辑；
    - 3、“执行器”http回调“调度中心”调度结果: “调度中心”中接收回调的服务，实际上是一台内嵌jetty服务器，默认端口8888;

##### 5.6.2 通讯数据加密
调度中心与执行器之间使用RequestModel和ResponseModel两个对象封装调度请求参数和响应数据, 在进行通讯之前底层会将上述两个对象对象序列化字节数组,最终转化成16进制数据进行数据交互,从而达到数据加密的功能;

## 六、版本更新日志
#### 6.1 版本 V1.1.x，新特性
**【于V1.1.x版本，XXL-JOB正式应用于我司，内部定制别名为 “Ferrari”，新接入应用推荐使用最新版本】**
- 1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；
- 2、动态：支持动态修改任务状态，动态暂停/恢复任务，即时生效；
- 3、服务HA：任务信息持久化到mysql中，Job服务天然支持集群，保证服务HA；
- 4、任务HA：某台Job服务挂掉，任务会平滑分配给其他的某一台存活服务，即使所有服务挂掉，重启时或补偿执行丢失任务；
- 5、一个任务只会在其中一台服务器上执行；
- 6、任务串行执行；
- 7、支持自定义参数；
- 8、支持远程任务执行终止；

#### 6.2 版本 V1.2.x，新特性
- 1、支持任务分组；
- 2、支持“本地任务”、“远程任务”；
- 3、底层通讯支持两种方式，Servlet方式 + JETTY方式；
- 4、支持“任务日志”；
- 5、支持“串行执行”，并行执行；
	
	说明：V1.2版本将系统架构按功能拆分为：
	
		- 调度模块（调度中心）：负责管理调度信息，按照调度配置发出调度请求；
		- 执行模块（执行器）：负责接收调度请求并执行任务逻辑；
		- 通讯模块：负责调度模块和任务模块之间的信息通讯；
	优点：
	
		- 解耦：任务模块提供任务接口，调度模块维护调度信息，业务相互独立；
		- 高扩展性；
		- 稳定性；

#### 6.3 版本 V1.3.0，新特性
- 1、遗弃“本地任务”模式，推荐使用“远程任务”，易于系统解耦，任务对应的JobHander统称为“执行器”；
- 2、遗弃“servlet”方式底层系统通讯，推荐使用JETTY方式，调度+回调双向通讯，重构通讯逻辑；
- 3、UI交互优化：左侧菜单展开状态优化，菜单项选中状态优化，任务列表打开表格有压缩优化；
- 4、【重要】“执行器”细分为：BEAN、GLUE两种开发模式，简介见下文：
	
	“执行器” 模式简介：
		- BEAN模式执行器：每个执行器都是Spring的一个Bean实例，XXL-JOB通过注解@JobHander识别和调度执行器；
		 -GLUE模式执行器：每个执行器对应一段代码，在线Web编辑和维护，动态编译生效，执行器负责加载GLUE代码和执行；

#### 6.4 版本 V1.3.1，新特性	
- 1、更新项目目录结构：
	- /xxl-job-admin -------------------- 【调度中心】：负责管理调度信息，按照调度配置发出调度请求；
	- /xxl-job-core ----------------------- 公共依赖
	- /xxl-job-executor-example ------ 【执行器】：负责接收调度请求并执行任务逻辑；
	- /db ---------------------------------- 建表脚本
	- /doc --------------------------------- 用户手册
- 2、在新的目录结构上，升级了用户手册；
- 3、优化了一些交互和UI；

#### 6.5 版本 V1.3.2，新特性	
- 1、调度逻辑进行事务包裹；
- 2、执行器异步回调执行日志；
- 3、【重要】在 “调度中心” 支持HA的基础上，扩展执行器的Failover支持，支持配置多执行期地址；

#### 6.6 版本 V1.4.0 新特性
- 1、任务依赖: 通过事件触发方式实现, 任务执行成功并回调时会主动触发一次子任务的调度, 多个子任务用逗号分隔;
- 2、执行器底层实现代码进行重度重构, 优化底层建表脚本;
- 3、执行器中任务线程分组逻辑优化: 之前根据执行器JobHandler进行线程分组,当多个任务复用Jobhanlder会导致相互阻塞。现改为根据调度中心任务进行任务线程分组,任务与任务执行相互隔离;
- 4、执行器调度通讯方案优化, 通过Hex + HC实现建议RPC通讯协议, 优化了通讯参数的维护和解析流程;
- 5、调度中心, 新建/编辑任务, 界面属性调整: 
    - 5.1、任务新增/编辑界面中去除 "任务名JobName"属性 ,该属性改为系统自动生成: 该字段之前主要用于在 "调度中心" 唯一标示一个任务, 现实意义不大, 因此计划淡化掉该字段,改为系统生成UUID,从而简化任务新建的操作;
    - 5.2、任务新增/编辑界面中去除 "GLUE模式" 复选框位置调整, 改为贴近"JobHandler"输入框右侧;
    - 5.3、任务新增/编辑界面中去除 "报警阈值" 属性;
    - 5.4、任务新增/编辑界面中去除 "子任务Key" 属性, 每个任务全局任务Key可以从任务列表获取, 当本任务执行结束且成功后, 将会根据子任务Key匹配子任务并主动触发一次子任务执行;
- 6、问题修复:
    - 6.1、执行器jetty关闭优化,解决一处可能导致jetty无法关闭的问题;
    - 6.2、执行器任务终止时,执行队列回调优化,解决一处导致任务无法回调的问题；
    - 6.3、调度中心中列表分页参数优化,解决一处因服务器限制post长度而引起的问题;
    - 6.4、执行器Jobhandler注解优化,解决一处因事务代理导致的容器无法加载JobHandler的问题;
    - 6.5、远程调度优化,禁用retry策略,解决一处可能导致重复调用的问题;
    
#### 6.7 版本 V1.4.1 新特性
- 1、项目成功推送maven中央仓库, 中央仓库地址以及依赖如下: 
    ```
    <!-- http://repo1.maven.org/maven2/com/xuxueli/xxl-job-core/ -->
    <dependency>
        <groupId>com.xuxueli</groupId>
        <artifactId>xxl-job-core</artifactId>
        <version>1.4.1</version>
    </dependency>
    ```
- 2、为适配中央仓库规则, 项目groupId从com.xxl改为com.xuxueli。
- 3、系统版本不在维护在项目跟pom中,各个子模块单独配置版本配置,解决子模块无法单独编译的问题;
- 4、底层RPC通讯,传输数据的字节长度统计规则优化,可节省50%数据传输量;
- 5、IJobHandler取消任务返回值,原通过返回值判断执行状态,逻辑改为:默认任务执行成功,仅在捕获异常时认定任务执行失败。
- 6、系统公共弹框功能,插件化;
- 7、底层表结构,表明统一大写;
- 8、调度中心,异常处理器JSON响应的ContentType修改,修复浏览器不识别的问题;


Tips: 历史版本(V1.3.x)目前已经Release至稳定版本, 进入维护阶段, 地址见分支 [V1.3](https://github.com/xuxueli/xxl-job/tree/v1.3) 。新特性将会在master分支持续更新。


#### 规划中
- 1、任务执行规则自定义：假如前一个任务正在执行，后续调度执行规则支持自定义；
    串行（默认，当前逻辑）：后续调度入调度队列；
    并行：后续调度并行执行；
    Pass：后续调度被Pass；
- 2、兼容oracle；
- 3、执行器JobHandler自动注册发现: 执行器中JobHandler自动上报到注册中心,调度中心自动发现注册中心的JobHandler并触发对应的执行器执行任务逻辑; 一方面省略了人工指定器地址的流程,另一方面可以方便的进行执行器机器扩充;(但是,XXL-JOB的定位是轻量级作业调度系统,目前而言使用非常方便,担心引入注册机器会增加运维和学习成本,权衡得失中...)
- 4、后续优化：在线维护分组，在线修改密码，回调多地址+重试，
- 5、支持脚本JOB, 即shell/python/php等, glue实现;
- 6、通过数据库实现JobHandler自动发现: 每个执行器指定appname, 执行器15注册一次粒度为appname和ip, 调度中心15秒加载一次注册表, 超时记录则心跳检测, 调度未配置执行地址,则使用注册表;

## 七、其他

#### 7.1 报告问题
XXL-JOB托管在Github上，如有问题可在 [ISSUES](https://github.com/xuxueli/xxl-job/issues/) 上提问，也可以加入技术交流群(仅作技术交流)：367260654

#### 7.2 接入登记
更多接入公司，欢迎在github [登记](https://github.com/xuxueli/xxl-job/issues/1 )