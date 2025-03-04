---
type: docs
title: "配置项参考手册"
linkTitle: "配置项手册"
weight: 6
description: "包含 Dubbo 支持的所有配置组件及每个配置组件支持的所有配置项"
---

## 配置详情

### application

每个应用必须要有且只有一个 application 配置，对应的配置类：`org.apache.dubbo.config.ApplicationConfig`

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| name | application | string | <b>必填</b> | | 服务治理 | 当前应用名称，用于注册中心计算应用间依赖关系，注意：消费者和提供者应用名不要一样，此参数不是匹配条件，你当前项目叫什么名字就填什么，和提供者消费者角色无关，比如：kylin应用调用了morgan应用的服务，则kylin项目配成kylin，morgan项目配成morgan，可能kylin也提供其它服务给别人使用，但kylin项目永远配成kylin，这样注册中心将显示kylin依赖于morgan | 2.7.0以上版本 |
| compiler | compiler | string | 可选 | javassist | 性能优化 | Java字节码编译器，用于动态类的生成，可选：jdk或javassist | 2.7.0以上版本 |
| logger | logger | string | 可选 | slf4j | 性能优化 | 日志输出方式，可选：slf4j,jcl,log4j,log4j2,jdk | 2.7.0以上版本 |
| owner | owner | string | 可选 | | 服务治理 | 应用负责人，用于服务治理，请填写负责人公司邮箱前缀 | 2.0.5以上版本 |
| organization | organization | string | 可选 | | 服务治理 | 组织名称(BU或部门)，用于注册中心区分服务来源，此配置项建议不要使用autoconfig，直接写死在配置中，比如china,intl,itu,crm,asc,dw,aliexpress等 | 2.0.0以上版本 |
| architecture <br class="atl-forced-newline" /> | architecture <br class="atl-forced-newline" /> | string | 可选 | | 服务治理 | 用于服务分层对应的架构。如，intl、china。不同的架构使用不同的分层。 | 2.0.7以上版本 |
| environment | environment | string | 可选 | | 服务治理 | 应用环境，如：develop/test/product，不同环境使用不同的缺省值，以及作为只用于开发测试功能的限制条件 | 2.0.0以上版本 |
| version | application.version | string | 可选 | | 服务治理 | 当前应用的版本 | 2.7.0以上版本 |
| dumpDirectory | dump.directory | string | 可选 | | 服务治理 | 当进程出问题如线程池满时，框架自动dump文件的存储路径 | 2.7.0以上版本 |
| qosEnable | qos.enable | boolean | 可选 | | 服务治理 | 是否启用 qos 运维端口 | 2.7.0以上版本 |
| qosHost | qos.host | string | 可选 | | 服务治理 | 监听的网络接口地址，默认 0.0.0.0 | 2.7.3以上版本 |
| qosPort | qos.port | int | 可选 | | 服务治理 | 监听的网络端口 | 2.7.0以上版本 |
| qosAcceptForeignIp | qos.accept.foreign.ip | boolean | 可选 | | 服务治理 | 安全配置，是否接收除localhost本机访问之外的外部请求 | 2.7.0以上版本 |
| shutwait | dubbo.service.shutdown.wait | string | 可选 | | 服务治理 | 优雅停机时 shutdown 的等待时间(ms) | 2.7.0以上版本 |
| hostname | | string | 可选 | 本机主机名 | 服务治理 | 主机名 | 2.7.5以上版本 |
| registerConsumer | registerConsumer | boolean | 可选 | true | 服务治理 | 是否注册实例到注册中心。当时实例为纯消费者时才设置为`false` | 2.7.5以上版本 |
| repository | application.version | string | 可选 | | 服务治理 | 当前应用的版本 | 2.7.6以上版本 |
| enableFileCache | file.cache | boolean | 可选 | true | 服务治理 | 是否开启本地缓存 | 3.0.0以上版本 |
| protocol | | string | 可选 | dubbo | 服务治理 | 首选协议，适用于无法确定首选协议的时候 | 3.0.0以上版本 |
| metadataType | metadata-type |String| 可选 | local | 服务治理 | 应用级服务发现 metadata 传递方式，是以 Provider 视角而言的，Consumer 侧配置无效，可选值有：<br>* remote - Provider 把 metadata 放到远端注册中心，Consumer 从注册中心获取；<br/>* local - Provider 把 metadata 放在本地，Consumer 从 Provider 处直接获取；| 2.7.5以上版本 |
| metadataServiceProtocol | metadata-service-protocol | string | 可选 | dubbo | 服务治理 | 如 metadataType 配置为 local，则该属性设置 MetadataService 服务所用的通信协议，默认为 dubbo| 3.0.0以上版本 |
| metadataServicePort | metadata-service-port | int | 可选 | | 服务治理 | 如 metadataType 配置为 local，则该属性设置 MetadataService 服务所用的端口号| 2.7.9以上版本 |
| livenessProbe | liveness-probe | string | 可选 | | 服务治理 | 概念和格式对应 k8s 体系 liveness probe | 3.0.0以上版本 |
| readinessProbe | readiness-probe | string | 可选 | | 服务治理 | 概念和格式对应 k8s 体系 readiness probe | 3.0.0以上版本 |
| startupProbe | startup-probe | string | 可选 | | 服务治理 | 概念和格式对应 k8s 体系 startup probe | 3.0.0以上版本 |
| registerMode | register-mode | string | 可选 | all | 服务治理 | 控制地址注册行为，应用级服务发现迁移用。<br/>* instance 只注册应用级地址；<br/>* interface 只注册接口级地址；<br/>* all(默认) 同时注册应用级和接口级地址； | 3.0.0以上版本 |
| enableEmptyProtection | enable-empty-protection | boolean | 可选 | true | 服务治理 | 是否全局启用消费端的空地址列表保护，开启后注册中心的空地址推送将被忽略，默认 true | 3.0.0以上版本 |
| parameters | 无 | Map<string, string> | 可选 | | 服务治理 | 扩展预留，可扩展定义任意参数，所有扩展参数都将原样反映在 URL 配置上 | 2.7.0以上版本 |


### service

服务提供者暴露服务配置。对应的配置类：`org.apache.dubbo.config.ServiceConfig`

|  属性 |  对应URL参数 |  类型 |  是否必填 |  缺省值 |  作用 |  描述 |  兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| interface | | class | <b>必填</b> | | 服务发现 | 服务接口名 | 1.0.0以上版本 |
| ref | | object | <b>必填</b> | | 服务发现 | 服务对象实现引用 | 1.0.0以上版本 |
| version | version | string | 可选 | 0.0.0 | 服务发现 | 服务版本，建议使用两位数字版本，如：1.0，通常在接口不兼容时版本号才需要升级 | 1.0.0以上版本 |
| group | group | string | 可选 | | 服务发现 | 服务分组，当一个接口有多个实现，可以用分组区分 | 1.0.7以上版本 |
| path | &lt;path&gt; | string | 可选 | 缺省为接口名 | 服务发现 | 服务路径 (注意：1.0不支持自定义路径，总是使用接口名，如果有1.0调2.0，配置服务路径可能不兼容) | 1.0.12以上版本 |
| delay | delay | int | 可选 | 0 | 性能调优 | 延迟注册服务时间(毫秒) ，设为-1时，表示延迟到Spring容器初始化完成时暴露服务 | 1.0.14以上版本 |
| timeout | timeout | int | 可选 | 1000 | 性能调优 | 远程服务调用超时时间(毫秒) | 2.0.0以上版本 |
| retries | retries | int | 可选 | 2 | 性能调优 | 远程服务调用重试次数，不包括第一次调用，不需要重试请设为0 | 2.0.0以上版本 |
| connections | connections | int | 可选 | 100 | 性能调优 | 对每个提供者的最大连接数，rmi、http、hessian等短连接协议表示限制连接数，dubbo等长连接协表示建立的长连接个数 | 2.0.0以上版本 |
| loadbalance | loadbalance | string | 可选 | random | 性能调优 | 负载均衡策略，可选值：<br/>* random - 随机; <br/>* roundrobin - 轮询; <br/>* leastactive - 最少活跃调用; <br/>* consistenthash - 哈希一致 (2.1.0以上版本); <br/>* shortestresponse - 最短响应 (2.7.7以上版本);| 2.0.0以上版本 |
| async | async | boolean | 可选 | false | 性能调优 | 是否缺省异步执行，不可靠异步，只是忽略返回值，不阻塞执行线程 | 2.0.0以上版本 |
| local | local | class/boolean | 可选 | false | 服务治理 | 设为true，表示使用缺省代理类名，即：接口名 + Local后缀，已废弃，请使用stub| 2.0.0以上版本 |
| stub | stub | class/boolean | 可选 | false | 服务治理 | 设为true，表示使用缺省代理类名，即：接口名 + Stub后缀，服务接口客户端本地代理类名，用于在客户端执行本地逻辑，如本地缓存等，该本地代理类的构造函数必须允许传入远程代理对象，构造函数如：public XxxServiceStub(XxxService xxxService) | 2.0.0以上版本 |
| mock | mock | class/boolean | 可选 | false | 服务治理 | 设为true，表示使用缺省Mock类名，即：接口名 + Mock后缀，服务接口调用失败Mock实现类，该Mock类必须有一个无参构造函数，与Local的区别在于，Local总是被执行，而Mock只在出现非业务异常(比如超时，网络异常等)时执行，Local在远程调用之前执行，Mock在远程调用后执行。 | 2.0.0以上版本 |
| token | token | string/boolean | 可选 | false | 服务治理 | 令牌验证，为空表示不开启，如果为true，表示随机生成动态令牌，否则使用静态令牌，令牌的作用是防止消费者绕过注册中心直接访问，保证注册中心的授权功能有效，如果使用点对点调用，需关闭令牌功能 | 2.0.0以上版本 |
| registry | | string | 可选 | 缺省向所有registry注册 | 配置关联 | 向指定注册中心注册，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔，如果不想将该服务注册到任何registry，可将值设为N/A | 2.0.0以上版本 |
| provider | | string | 可选 | 缺省使用第一个provider配置 | 配置关联 | 指定provider，值为&lt;dubbo:provider&gt;的id属性 | 2.0.0以上版本 |
| deprecated | deprecated | boolean | 可选 | false | 服务治理 | 服务是否过时，如果设为true，消费方引用时将打印服务过时警告error日志 | 2.0.5以上版本 |
| dynamic | dynamic | boolean | 可选 | true | 服务治理 | 服务是否动态注册，如果设为false，注册后将显示后disable状态，需人工启用，并且服务提供者停止时，也不会自动取消册，需人工禁用。 | 2.0.5以上版本 |
| accesslog | accesslog | string/boolean | 可选 | false | 服务治理 | 设为true，将向logger中输出访问日志，也可填写访问日志文件路径，直接把访问日志输出到指定文件 | 2.0.5以上版本 |
| owner | owner | string | 可选 | | 服务治理 | 服务负责人，用于服务治理，请填写负责人公司邮箱前缀 | 2.0.5以上版本 |
| document | document | string | 可选 | | 服务治理 | 服务文档URL | 2.0.5以上版本 |
| weight | weight | int | 可选 | | 性能调优 | 服务权重 | 2.0.5以上版本 |
| executes | executes | int | 可选 | 0 | 性能调优 | 服务提供者每服务每方法最大可并行执行请求数 | 2.0.5以上版本 | 
| actives | actives | int | 可选 | 0 | 性能调优 | 每服务消费者每服务每方法最大并发调用数 | 2.0.5以上版本 |
| proxy | proxy | string | 可选 | javassist | 性能调优 | 生成动态代理方式，可选：jdk/javassist | 2.0.5以上版本 |
| cluster | cluster | string | 可选 | failover | 性能调优 | 集群方式，可选：failover/failfast/failsafe/failback/forking/available/mergeable(2.1.0以上版本)/broadcast(2.1.0以上版本)/zone-aware(2.7.5以上版本) | 2.0.5以上版本 |
| filter | service.filter | string | 可选 | default | 性能调优 | 服务提供方远程调用过程拦截器名称，多个名称用逗号分隔 | 2.0.5以上版本 |
| listener | exporter.listener | string | 可选 | default | 性能调优 | 服务提供方导出服务监听器名称，多个名称用逗号分隔 | |
| protocol | | string | 可选 | | 配置关联 | 使用指定的协议暴露服务，在多协议时使用，值为&lt;dubbo:protocol&gt;的id属性，多个协议ID用逗号分隔 | 2.0.5以上版本 |
| layer | layer | string | 可选 | | 服务治理 | 服务提供者所在的分层。如：biz、dao、intl:web、china:acton。 | 2.0.7以上版本 |
| register | register | boolean | 可选 | true | 服务治理 | 该协议的服务是否注册到注册中心 | 2.0.8以上版本 |
| validation | validation | string | 可选 | | 服务治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 | 2.7.0以上版本 |
| parameters | 无 | Map<string, string> | 可选 | | 服务治理 | 扩展预留，可扩展定义任意参数，所有扩展参数都将原样反映在 URL 配置上 | 2.0.0以上版本 |

### reference


服务消费者引用服务配置。对应的配置类： `org.apache.dubbo.config.ReferenceConfig`

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| id | | string | <b>必填</b> | | 配置关联 | 服务引用BeanId | 1.0.0以上版本  |
| interface | | class | <b>必填</b> | | 服务发现 | 服务接口名 | 1.0.0以上版本  |
| version | version | string | 可选 | | 服务发现 | 服务版本，与服务提供者的版本一致 | 1.0.0以上版本  |
| group | group | string | 可选 | | 服务发现 | 服务分组，当一个接口有多个实现，可以用分组区分，必需和服务提供方一致 | 1.0.7以上版本  |
| timeout | timeout | long | 可选 | 缺省使用&lt;dubbo:consumer&gt;的timeout | 性能调优 | 服务方法调用超时时间(毫秒) | 1.0.5以上版本  |
| retries | retries | int | 可选 | 缺省使用&lt;dubbo:consumer&gt;的retries | 性能调优 | 远程服务调用重试次数，不包括第一次调用，不需要重试请设为0 | 2.0.0以上版本  |
| connections | connections | int | 可选 | 缺省使用&lt;dubbo:consumer&gt;的connections | 性能调优 | 对每个提供者的最大连接数，rmi、http、hessian等短连接协议表示限制连接数，dubbo等长连接协表示建立的长连接个数 | 2.0.0以上版本  |
| loadbalance | loadbalance | string | 可选 | 缺省使用&lt;dubbo:consumer&gt;的loadbalance | 性能调优 | 负载均衡策略，可选值：<br/>* random - 随机; <br/>* roundrobin - 轮询; <br/>* leastactive - 最少活跃调用; <br/>* consistenthash - 哈希一致 (2.1.0以上版本); <br/>* shortestresponse - 最短响应 (2.7.7以上版本); | 2.0.0以上版本 |
| async | async | boolean | 可选 | 缺省使用&lt;dubbo:consumer&gt;的async | 性能调优 | 是否异步执行，不可靠异步，只是忽略返回值，不阻塞执行线程 | 2.0.0以上版本  |
| generic | generic | boolean | 可选 | 缺省使用&lt;dubbo:consumer&gt;的generic | 服务治理 | 是否缺省泛化接口，如果为泛化接口，将返回GenericService | 2.0.0以上版本  |
| check | check | boolean | 可选 | 缺省使用&lt;dubbo:consumer&gt;的check | 服务治理 | 启动时检查提供者是否存在，true报错，false忽略 | 2.0.0以上版本  |
| url | url | string | 可选 | | 服务治理 | 点对点直连服务提供者地址，将绕过注册中心 | 1.0.6以上版本  |
| stub | stub | class/boolean | 可选 | | 服务治理 | 服务接口客户端本地代理类名，用于在客户端执行本地逻辑，如本地缓存等，该本地代理类的构造函数必须允许传入远程代理对象，构造函数如：public XxxServiceLocal(XxxService xxxService) | 2.0.0以上版本  |
| mock | mock | class/boolean | 可选 | | 服务治理 | 服务接口调用失败Mock实现类名，该Mock类必须有一个无参构造函数，与Local的区别在于，Local总是被执行，而Mock只在出现非业务异常(比如超时，网络异常等)时执行，Local在远程调用之前执行，Mock在远程调用后执行。 | Dubbo1.0.13及其以上版本支持  |
| cache | cache | string/boolean | 可选 | | 服务治理 | 以调用参数为key，缓存返回结果，可选：lru, threadlocal, jcache等 | Dubbo2.1.0及其以上版本支持  |
| validation | validation | boolean | 可选 | | 服务治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 | Dubbo2.1.0及其以上版本支持  |
| proxy | proxy | boolean | 可选 | javassist | 性能调优 | 选择动态代理实现策略，可选：javassist, jdk | 2.0.2以上版本  |
| client | client | string | 可选 | | 性能调优 | 客户端传输类型设置，如Dubbo协议的netty或mina。 | Dubbo2.0.0以上版本支持  |
| registry | | string | 可选 | 缺省将从所有注册中心获服务列表后合并结果 | 配置关联 | 从指定注册中心注册获取服务列表，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔 | 2.0.0以上版本  |
| owner | owner | string | 可选 | | 服务治理 | 调用服务负责人，用于服务治理，请填写负责人公司邮箱前缀 | 2.0.5以上版本  |
| actives | actives | int | 可选 | 0 | 性能调优 | 每服务消费者每服务每方法最大并发调用数 | 2.0.5以上版本  |
| cluster | cluster | string | 可选 | failover | 性能调优 | 集群方式，可选：failover/failfast/failsafe/failback/forking/available/mergeable(2.1.0以上版本)/broadcast(2.1.0以上版本)/zone-aware(2.7.5以上版本) | 2.0.5以上版本  |
| connections | connections | int | 可选 | 100 | 性能调优 | 对每个提供者的最大连接数，rmi、http、hessian等短连接协议表示限制连接数，dubbo等长连接协表示建立的长连接个数 | 2.0.0以上版本 |
| filter | reference.filter | string | 可选 | default | 性能调优 | 服务消费方远程调用过程拦截器名称，多个名称用逗号分隔 | 2.0.5以上版本  |
| listener | invoker.listener | string | 可选 | default | 性能调优 | 服务消费方引用服务监听器名称，多个名称用逗号分隔 | 2.0.5以上版本  |
| layer | layer | string | 可选 | | 服务治理 | 服务调用者所在的分层。如：biz、dao、intl:web、china:acton。 | 2.0.7以上版本  |
| init | init | boolean | 可选 | false | 性能调优 | 是否在afterPropertiesSet()时饥饿初始化引用，否则等到有人注入或引用该实例时再初始化。 | 2.0.10以上版本  |
| protocol | protocol | string | 可选 | | 服务治理 | 只调用指定协议的服务提供方，其它协议忽略。 | 2.7.0以上版本 |
| client | client | string | 可选 | dubbo协议缺省为netty | 服务发现 | 协议的客户端实现类型，比如：dubbo协议的mina,netty等 | 2.7.0以上版本 |
| providerPort | provider-port | int | 可选 | | Service Mesh | 当dubbo.consumer.meshEnable=true，Dubbo默认会将请求转换成K8S标准格式，结合VirtualService和DestinationRule进行流量治理，此时consumer端可以感知到provider。如果不想使用VirtualService和DestinationRule，请设置providerPort，使consumer端感知provider暴露的服务端口 | 3.1.0以上版本 |
| unloadClusterRelated | unloadClusterRelated | boolean | 可选 | false | Service Mesh | 当dubbo.consumer.meshEnable=true，在Service Mesh模式下，设置为true，可在当前调用中卸载与Cluster相关的Directory、Router和Load Balance，将重试、负载平衡、超时和其他流量管理功能下放至Sidecar，使用VirtualService和DestinationRule进行流量治理 | 3.1.0以上版本 |
| parameters | 无 | Map<string, string> | 可选 | | 服务治理 | 扩展预留，可扩展定义任意参数，所有扩展参数都将原样反映在 URL 配置上 | 2.0.0以上版本 |
| providedBy | provided-by | string | 可选 | | Service Mesh | 当dubbo.consumer.meshEnable=true，Dubbo默认会将请求转换成K8S标准格式，结合VirtualService和DestinationRule进行流量治理，此时consumer端可以感知到provider。该值应当与声明的`k8s service`一致 | 3.1.0以上版本 |
| providerNamespace | provider-namespace | string | 可选 | | Service Mesh | 当dubbo.consumer.meshEnable=true，Dubbo默认会将请求转换成K8S标准格式，结合VirtualService和DestinationRule进行流量治理，此时consumer端可以感知到provider。请设置providerNamespace，使consumer端按照此配置寻址provider dns，默认`default` | 3.1.1以上版本 |


### registry

注册中心配置。对应的配置类： `org.apache.dubbo.config.RegistryConfig`。同时如果有多个不同的注册中心，可以声明多个 `<dubbo:registry>` 标签，并在 `<dubbo:service>` 或 `<dubbo:reference>` 的 `registry` 属性指定使用的注册中心。

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| id | | string | 可选 | | 配置关联 | 注册中心引用BeanId，可以在&lt;dubbo:service registry=""&gt;或&lt;dubbo:reference registry=""&gt;中引用此ID | 1.0.16以上版本 |
| address | &lt;host:port&gt; | string | <b>必填</b> | | 服务发现 | 注册中心服务器地址，如果地址没有端口缺省为9090，同一集群内的多个地址用逗号分隔，如：ip:port,ip:port，不同集群的注册中心，请配置多个&lt;dubbo:registry&gt;标签 | 1.0.16以上版本 |
| protocol | &lt;protocol&gt; | string | 可选 | dubbo | 服务发现 | 注册中心地址协议，支持`dubbo`, `multicast`, `zookeeper`, `redis`, `consul(2.7.1)`, `sofa(2.7.2)`, `etcd(2.7.2)`, `nacos(2.7.2)`等协议 | 2.0.0以上版本 |
| port | &lt;port&gt; | int | 可选 | 9090 | 服务发现 | 注册中心缺省端口，当address没有带端口时使用此端口做为缺省值 | 2.0.0以上版本 |
| username | &lt;username&gt; | string | 可选 | | 服务治理 | 登录注册中心用户名，如果注册中心不需要验证可不填 | 2.0.0以上版本 |
| password | &lt;password&gt; | string | 可选 | | 服务治理 | 登录注册中心密码，如果注册中心不需要验证可不填 | 2.0.0以上版本 |
| transport | registry.transporter | string | 可选 | netty | 性能调优 | 网络传输方式，可选mina,netty | 2.0.0以上版本 |
| timeout | registry.timeout | int | 可选 | 5000 | 性能调优 | 注册中心请求超时时间(毫秒) | 2.0.0以上版本 |
| session | registry.session | int | 可选 | 60000 | 性能调优 | 注册中心会话超时时间(毫秒)，用于检测提供者非正常断线后的脏数据，比如用心跳检测的实现，此时间就是心跳间隔，不同注册中心实现不一样。 | 2.1.0以上版本 |
| zone | zone | string | 可选 | | 服务治理 | 注册表所属区域，通常用于流量隔离 | 2.7.5以上版本
| file | registry.file | string | 可选 | | 服务治理 | 使用文件缓存注册中心地址列表及服务提供者列表，应用重启时将基于此文件恢复，注意：两个注册中心不能使用同一文件存储 | 2.0.0以上版本 |
| wait | registry.wait | int | 可选 | 0 | 性能调优 | 停止时等待通知完成时间(毫秒) | 2.0.0以上版本 |
| check | check | boolean | 可选 | true | 服务治理 | 注册中心不存在时，是否报错 | 2.0.0以上版本 |
| register | register | boolean | 可选 | true | 服务治理 | 是否向此注册中心注册服务，如果设为false，将只订阅，不注册 | 2.0.5以上版本 |
| subscribe | subscribe | boolean | 可选 | true | 服务治理 | 是否向此注册中心订阅服务，如果设为false，将只注册，不订阅 | 2.0.5以上版本 |
| dynamic | dynamic | boolean | 可选 | true | 服务治理 | 服务是否动态注册，如果设为false，注册后将显示为disable状态，需人工启用，并且服务提供者停止时，也不会自动取消注册，需人工禁用。 | 2.0.5以上版本 |
| group | group | string | 可选 | dubbo | 服务治理 | 服务注册分组，跨组的服务不会相互影响，也无法相互调用，适用于环境隔离。 | 2.0.5以上版本 |
| version | version | string | 可选 | | 服务发现 | 服务版本 | 1.0.0以上版本  |
| simplified | simplified | boolean | 可选 | false | 服务治理 | 注册到注册中心的URL是否采用精简模式的（与低版本兼容） | 2.7.0以上版本 |
| extra-keys | extraKeys | string | 可选 |  | 服务治理 | 在simplified=true时，extraKeys允许你在默认参数外将额外的key放到URL中，格式："interface,key1,key2"。 | 2.7.0以上版本 |
| useAsConfigCenter | | boolean | 可选 | | 服务治理 | 该注册中心是否作为配置中心使用 | 2.7.5以上版本 |
| useAsMetadataCenter | | boolean | 可选 | | 服务治理 | 该注册中心是否作为元数据中心使用 | 2.7.5以上版本 |
| accepts | accepts | string | 可选 | | 服务治理 | 该注册中心接收rpc协议列表，多协议用逗号隔开，例如dubbo,rest | 2.7.5以上版本 |
| preferred | preferred | boolean | 可选 | | 服务治理 | 是否作为首选注册中心。当订阅多注册中心时，如果设为true，该注册中心作为首选 | 2.7.5以上版本 |
| weight | weight | int | 可选 | | 性能调优 | 注册流量权重。使用多注册中心时，可通过该值调整注册流量的分布，当设置首选注册中心时该值不生效 | 2.7.5以上版本 |
| registerMode | register-mode | string | 可选 | all | 服务治理 | 控制地址注册行为，应用级服务发现迁移用。<br/>* instance 只注册应用级地址；<br/>* interface 只注册接口级地址；<br/>* all(默认) 同时注册应用级和接口级地址； | 3.0.0以上版本 |
| enableEmptyProtection | enable-empty-protection | boolean | 可选 | true | 服务治理 | 是否全局启用消费端的空地址列表保护，开启后注册中心的空地址推送将被忽略，默认 true | 3.0.0以上版本 |
| parameters | 无 | Map<string, string> | 可选 | | 服务治理 | 扩展预留，可扩展定义任意参数，所有扩展参数都将原样反映在 URL 配置上 | 2.0.0以上版本 |

### config-center

配置中心。对应的配置类：`org.apache.dubbo.config.ConfigCenterConfig`

| 属性             | 对应URL参数            | 类型                | 是否必填 | 缺省值           | 描述                                                         | 兼容性 |
| ---------------- | ---------------------- | ------------------- | -------- | ---------------- | ------------------------------------------------------------ | ------ |
| protocol         | protocol        | string              | 可选     | zookeeper        | 使用哪个配置中心：apollo、zookeeper、nacos等。<br />以zookeeper为例<br />1. 指定protocol，则address可以简化为`127.0.0.1:2181`；<br />2. 不指定protocol，则address取值为`zookeeper://127.0.0.1:2181` | 2.7.0以上版本 |
| address          | address         | string              | 必填     |                  | 配置中心地址。<br />取值参见protocol说明                     | 2.7.0以上版本 |
| highestPriority  | highest-priority| boolean             | 可选     | true             | 来自配置中心的配置项具有最高优先级，即会覆盖本地配置项。     | 2.7.0以上版本 |
| namespace        | namespace       | string              | 可选     | dubbo            | 通常用于多租户隔离，实际含义视具体配置中心而不同。<br />如：<br />zookeeper - 环境隔离，默认值`dubbo`；<br />apollo - 区分不同领域的配置集合，默认使用`dubbo`和`application` | 2.7.0以上版本 |
| cluster          | cluster         | string              | 可选     |                  | 含义视所选定的配置中心而不同。<br />如Apollo中用来区分不同的配置集群 | 2.7.0以上版本 |
| group            | group           | string              | 可选     | dubbo            | 含义视所选定的配置中心而不同。<br />nacos - 隔离不同配置集<br />zookeeper - 隔离不同配置集 | 2.7.0以上版本 |
| check            | check           | boolean             | 可选     | true             | 当配置中心连接失败时，是否终止应用启动。                     | 2.7.0以上版本 |
| configFile       | config-file     | string              | 可选     | dubbo.properties | 全局级配置文件所映射到的key<br />zookeeper - 默认路径/dubbo/config/dubbo/dubbo.properties<br />apollo - dubbo namespace中的dubbo.properties键 | 2.7.0以上版本 |
| appConfigFile    | app-config-file | string              | 可选     |                  | “configFile”是全局级共享的。此项仅限于此应用程序配置的属性 | 2.7.0以上版本 |
| timeout          | timeout         | int                 | 可选     | 3000ms           | 获取配置的超时时间                                           | 2.7.0以上版本 |
| username         | username        | string              | 可选     |                  | 如果配置中心需要做校验，用户名<br />Apollo暂未启用           | 2.7.0以上版本 |
| password         | password        | string              | 可选     |                  | 如果配置中心需要做校验，密码<br />Apollo暂未启用             | 2.7.0以上版本 |
| parameters       | parameters      | Map<string, string> | 可选     |                  | 扩展参数，用来支持不同配置中心的定制化配置参数               | 2.7.0以上版本 |
| includeSpringEnv |include-spring-env| boolean            | 可选     | false            | 使用Spring框架时支持，为true时，会自动从Spring Environment中读取配置。<br />默认依次读取<br />key为dubbo.properties的配置<br />key为dubbo.properties的PropertySource | 2.7.0以上版本 |

### metadata-report-config

元数据中心。对应的配置类：`org.apache.dubbo.config.MetadataReportConfig`

| 属性            | 对应URL参数 | 类型   | 是否必填 | 缺省值     | 描述                                                         | 兼容性 |
| --------------- | --------- | ------ | -------- | --------- | ------------------------------------------------------------ | ------ |
| address         | address   | string | 必填     |           | 元数据中心地址。                     | 2.7.0以上版本 |
| protocol        | protocol  | string | 可选     | zookeeper | 元数据中心协议：zookeeper、nacos、redis等。<br />以zookeeper为例<br />1. 指定protocol，则address可以简化为`127.0.0.1:2181`；<br />2. 不指定protocol，则address取值为`zookeeper://127.0.0.1:2181` | 2.7.13以上版本 |
| port            | port      | int    | 可选     |           | 元数据中心端口号。指定port，则address可简化，不用配置端口号 | 2.7.13以上版本 |
| username        | username  | string | 可选     |           | 元数据中心需要做校验，用户名<br />Apollo暂未启用           | 2.7.0以上版本 |
| password        | password  | string | 可选     |           | 元数据中心需要做校验，密码<br />Apollo暂未启用             | 2.7.0以上版本 |
| timeout         | timeout   | int    | 可选     |           | 获取元数据超时时间(ms)                                    | 2.7.0以上版本 |
| group           | group     | string | 可选     | dubbo     | 元数据分组，适用于环境隔离。与注册中心group意义相同         | 2.7.0以上版本 |
| retryTimes      | retry-times| int   | 可选     | 100       | 重试次数                                                 | 2.7.0以上版本 |  
| retryPeriod     | retry-period | int | 可选     | 3000ms    | 重试间隔时间(ms)                                         | 2.7.0以上版本 |
| cycleReport     | cycle-report | boolean| 可选  | true      | 是否每天更新完整元数据                                    | 2.7.0以上版本 |
| syncReport      | sync-report | boolean| 可选  | false      | 是否同步更新元数据，默认为异步                             | 2.7.0以上版本 |
| cluster         | cluster  | string | 可选    |            | 含义视所选定的元数据中心而不同。<br />如Apollo中用来区分不同的配置集群 | 2.7.0以上版本 |
| file            | file      | string | 可选   |            | 使用文件缓存元数据中心列表，应用重启时将基于此文件恢复，注意：两个元数据中心不能使用同一文件存储 | 2.7.0以上版本 |
| check           | check   | boolean | 可选   | true       | 当元数据中心连接失败时，是否终止应用启动。                     | 3.0.0以上版本 |
| reportMetadata  | report-metadata | boolean | 可选 | false | 是否上地址发现中的接口配置报元数据，`dubbo.application.metadata-type=remote` 该配置不起作用即一定会上报，`dubbo.application.metadata-type=local` 时是否上报由该配置值决定 | 3.0.0以上版本 |
| reportDefinition | report-definition | boolean | 可选 | true | 是否上报服务运维用元数据                                   | 3.0.0以上版本 |
| reportConsumerDefinition | report-consumer-definition | boolean | 可选 | true | 是否在消费端上报服务运维用元数据                                    | 3.0.0以上版本 |
| parameters      | parameters | Map<string, string> | 可选     |  | 扩展参数，用来支持不同元数据中心的定制化配置参数         | 2.7.0以上版本 |

### protocol

服务提供者协议配置。对应的配置类： `org.apache.dubbo.config.ProtocolConfig`。同时，如果需要支持多协议，可以声明多个 `<dubbo:protocol>` 标签，并在 `<dubbo:service>` 中通过 `protocol` 属性指定使用的协议。

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| id | | string | 可选 | dubbo | 配置关联 | 协议BeanId，可以在&lt;dubbo:service protocol=""&gt;中引用此ID，如果ID不填，缺省和name属性值一样，重复则在name后加序号。 | 2.0.5以上版本 |
| name | &lt;protocol&gt; | string | <b>必填</b> | dubbo | 性能调优 | 协议名称 | 2.0.5以上版本 |
| port | &lt;port&gt; | int | 可选 | dubbo协议缺省端口为20880，rmi协议缺省端口为1099，http和hessian协议缺省端口为80；如果<b>没有</b>配置port，则自动采用默认端口，如果配置为<b>-1</b>，则会分配一个没有被占用的端口。Dubbo 2.4.0+，分配的端口在协议缺省端口的基础上增长，确保端口段可控。 | 服务发现 | 服务端口 | 2.0.5以上版本 |
| host | &lt;host&gt; | string | 可选 | 自动查找本机IP | 服务发现 | &#45;服务主机名，多网卡选择或指定VIP及域名时使用，为空则自动查找本机IP，&#45;建议不要配置，让Dubbo自动获取本机IP | 2.0.5以上版本 |
| threadpool | threadpool | string | 可选 | fixed | 性能调优 | 线程池类型，可选：fixed/cached/limit(2.5.3以上)/eager(2.6.x以上) | 2.0.5以上版本 |
| threadname | threadname | string | 可选 |       | 性能调优 | 线程池名称 | 2.7.6以上版本 |
| threads | threads | int | 可选 | 200 | 性能调优 | 服务线程池大小(固定大小) | 2.0.5以上版本 |
| corethreads | corethreads | int | 可选 | 200 | 性能调优 | 线程池核心线程大小 | 2.0.5以上版本 |
| iothreads | threads | int | 可选 | cpu个数+1 | 性能调优 | io线程池大小(固定大小) | 2.0.5以上版本 |
| accepts | accepts | int | 可选 | 0 | 性能调优 | 服务提供方最大可接受连接数 | 2.0.5以上版本 |
| payload | payload | int | 可选 | 8388608(=8M) | 性能调优 | 请求及响应数据包大小限制，单位：字节 | 2.0.5以上版本 |
| codec | codec | string | 可选 | dubbo | 性能调优 | 协议编码方式 | 2.0.5以上版本 |
| serialization | serialization | string | 可选 | dubbo协议缺省为hessian2，rmi协议缺省为java，http协议缺省为json | 性能调优 | 协议序列化方式，当协议支持多种序列化方式时使用，比如：dubbo协议的dubbo,hessian2,java,compactedjava，以及http协议的json等 | 2.0.5以上版本 |
| accesslog | accesslog | string/boolean | 可选 | | 服务治理 | 设为true，将向logger中输出访问日志，也可填写访问日志文件路径，直接把访问日志输出到指定文件 | 2.0.5以上版本 |
| path | &lt;path&gt; | string | 可选 | | 服务发现 | 提供者上下文路径，为服务path的前缀 | 2.0.5以上版本 |
| transporter | transporter | string | 可选 | dubbo协议缺省为netty | 性能调优 | 协议的服务端和客户端实现类型，比如：dubbo协议的mina,netty等，可以分拆为server和client配置 | 2.0.5以上版本 |
| server | server | string | 可选 | dubbo协议缺省为netty，http协议缺省为servlet | 性能调优 | 协议的服务器端实现类型，比如：dubbo协议的mina,netty等，http协议的jetty,servlet等 | 2.0.5以上版本 |
| client | client | string | 可选 | dubbo协议缺省为netty | 性能调优 | 协议的客户端实现类型，比如：dubbo协议的mina,netty等 | 2.0.5以上版本 |
| dispatcher | dispatcher | string | 可选 | dubbo协议缺省为all | 性能调优 | 协议的消息派发方式，用于指定线程模型，比如：dubbo协议的all, direct, message, execution, connection等 | 2.1.0以上版本 |
| queues | queues | int | 可选 | 0 | 性能调优 | 线程池队列大小，当线程池满时，排队等待执行的队列大小，建议不要设置，当线程池满时应立即失败，重试其它服务提供机器，而不是排队，除非有特殊需求。 | 2.0.5以上版本 |
| charset | charset | string | 可选 | UTF-8 | 性能调优 | 序列化编码 | 2.0.5以上版本 |
| buffer | buffer | int | 可选 | 8192 | 性能调优 | 网络读写缓冲区大小 | 2.0.5以上版本 |
| heartbeat | heartbeat | int | 可选 | 0 | 性能调优 | 心跳间隔，对于长连接，当物理层断开时，比如拔网线，TCP的FIN消息来不及发送，对方收不到断开事件，此时需要心跳来帮助检查连接是否已断开 | 2.0.10以上版本 |
| telnet | telnet | string | 可选 | | 服务治理 | 所支持的telnet命令，多个命令用逗号分隔 | 2.0.5以上版本 |
| register | register | boolean | 可选 | true | 服务治理 | 该协议的服务是否注册到注册中心 | 2.0.8以上版本 |
| contextpath | contextpath | String | 可选 | 缺省为空串 | 服务治理 | 上下文路径 | 2.0.6以上版本 |
| sslEnabled | ssl-enabled | boolean | 可选 | false | 服务治理 | 是否启用ssl | 2.7.5以上版本 |
| parameters | parameters | Map<string, string> | 可选 |  | 扩展参数 | 2.0.0以上版本 |

### provider

服务提供者缺省值配置。对应的配置类： `org.apache.dubbo.config.ProviderConfig`。同时该标签为 `<dubbo:service>` 和 `<dubbo:protocol>` 标签的缺省值设置。

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| id | | string | 可选 | dubbo | 配置关联 | 协议BeanId，可以在&lt;dubbo:service proivder=""&gt;中引用此ID | 1.0.16以上版本 |
| protocol | &lt;protocol&gt; | string | 可选 | dubbo | 性能调优 | 协议名称 | 1.0.16以上版本 |
| host | &lt;host&gt; | string | 可选 | 自动查找本机IP | 服务发现 | 服务主机名，多网卡选择或指定VIP及域名时使用，为空则自动查找本机IP，建议不要配置，让Dubbo自动获取本机IP | 1.0.16以上版本 |
| threads | threads | int | 可选 | 200 | 性能调优 | 服务线程池大小(固定大小) | 1.0.16以上版本 |
| payload | payload | int | 可选 | 8388608(=8M) | 性能调优 | 请求及响应数据包大小限制，单位：字节 | 2.0.0以上版本 |
| path | &lt;path&gt; | string | 可选 | | 服务发现 | 提供者上下文路径，为服务path的前缀 | 2.0.0以上版本 |
| transporter | transporter | string | 可选 | dubbo协议缺省为netty | 性能调优 | 协议的服务端和客户端实现类型，比如：dubbo协议的mina,netty等，可以分拆为server和client配置 | 2.0.5以上版本 |
| server | server | string | 可选 | dubbo协议缺省为netty，http协议缺省为servlet | 性能调优 | 协议的服务器端实现类型，比如：dubbo协议的mina,netty等，http协议的jetty,servlet等 | 2.0.0以上版本 |
| client | client | string | 可选 | dubbo协议缺省为netty | 性能调优 | 协议的客户端实现类型，比如：dubbo协议的mina,netty等 | 2.0.0以上版本 |
| dispatcher | dispatcher | string | 可选 | dubbo协议缺省为all | 性能调优 | 协议的消息派发方式，用于指定线程模型，比如：dubbo协议的all, direct, message, execution, connection等 | 2.1.0以上版本 |
| codec | codec | string | 可选 | dubbo | 性能调优 | 协议编码方式 | 2.0.0以上版本 |
| serialization | serialization | string | 可选 | dubbo协议缺省为hessian2，rmi协议缺省为java，http协议缺省为json | 性能调优 | 协议序列化方式，当协议支持多种序列化方式时使用，比如：dubbo协议的dubbo,hessian2,java,compactedjava，以及http协议的json,xml等 | 2.0.5以上版本 |
| default | | boolean | 可选 | false | 配置关联 | 是否为缺省协议，用于多协议 | 1.0.16以上版本 |
| filter | service.filter | string | 可选 | | 性能调优 | 服务提供方远程调用过程拦截器名称，多个名称用逗号分隔 | 2.0.5以上版本 |
| listener | exporter.listener | string | 可选 | | 性能调优 | 服务提供方导出服务监听器名称，多个名称用逗号分隔 | 2.0.5以上版本 |
| threadpool | threadpool | string | 可选 | fixed | 性能调优 | 线程池类型，可选：fixed/cached/limit(2.5.3以上)/eager(2.6.x以上) | 2.0.5以上版本 |
| threadname | threadname | string | 可选 |       | 性能调优 | 线程池名称 | 2.7.6以上版本 |
| accepts | accepts | int | 可选 | 0 | 性能调优 | 服务提供者最大可接受连接数 | 2.0.5以上版本 |
| version | version | string | 可选 | 0.0.0 | 服务发现 | 服务版本，建议使用两位数字版本，如：1.0，通常在接口不兼容时版本号才需要升级 | 2.0.5以上版本 |
| group | group | string | 可选 |   | 服务发现 | 服务分组，当一个接口有多个实现，可以用分组区分 | 2.0.5以上版本 |
| delay | delay | int | 可选 | 0 | 性能调优 | 延迟注册服务时间(毫秒)&#45; ，设为-1时，表示延迟到Spring容器初始化完成时暴露服务 | 2.0.5以上版本 |
| timeout | default.timeout | int | 可选 | 1000 | 性能调优 | 远程服务调用超时时间(毫秒) | 2.0.5以上版本 |
| retries | default.retries | int | 可选 | 2 | 性能调优 | 远程服务调用重试次数，不包括第一次调用，不需要重试请设为0 | 2.0.5以上版本 |
| connections | default.connections | int | 可选 | 0 | 性能调优 | 对每个提供者的最大连接数，rmi、http、hessian等短连接协议表示限制连接数，dubbo等长连接协表示建立的长连接个数 | 2.0.5以上版本 |
| loadbalance | default.loadbalance | string | 可选 | random | 性能调优 | 负载均衡策略，可选值：<br/>* random - 随机; <br/>* roundrobin - 轮询; <br/>* leastactive - 最少活跃调用; <br/>* consistenthash - 哈希一致 (2.1.0以上版本); <br/>* shortestresponse - 最短响应 (2.7.7以上版本); | 2.0.5以上版本 |
| async | default.async | boolean | 可选 | false | 性能调优 | 是否缺省异步执行，不可靠异步，只是忽略返回值，不阻塞执行线程 | 2.0.5以上版本 |
| stub | stub | boolean | 可选 | false | 服务治理 | 设为true，表示使用缺省代理类名，即：接口名 + Local后缀。 | 2.0.5以上版本 |
| mock | mock | boolean | 可选 | false | 服务治理 | 设为true，表示使用缺省Mock类名，即：接口名 + Mock后缀。 | 2.0.5以上版本 |
| token | token | boolean | 可选 | false | 服务治理 | 令牌验证，为空表示不开启，如果为true，表示随机生成动态令牌 | 2.0.5以上版本 |
| registry | registry | string | 可选 | 缺省向所有registry注册 | 配置关联 | 向指定注册中心注册，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔，如果不想将该服务注册到任何registry，可将值设为N/A | 2.0.5以上版本 |
| dynamic | dynamic | boolean | 可选 | true | 服务治理 | 服务是否动态注册，如果设为false，注册后将显示后disable状态，需人工启用，并且服务提供者停止时，也不会自动取消册，需人工禁用。 | 2.0.5以上版本 |
| accesslog | accesslog | string/boolean | 可选 | false | 服务治理 | 设为true，将向logger中输出访问日志，也可填写访问日志文件路径，直接把访问日志输出到指定文件 | 2.0.5以上版本 |
| owner | owner | string | 可选 | | 服务治理 | 服务负责人，用于服务治理，请填写负责人公司邮箱前缀 | 2.0.5以上版本 |
| document | document | string | 可选 | | 服务治理 | 服务文档URL | 2.0.5以上版本 |
| weight | weight | int | 可选 | | 性能调优 | 服务权重 | 2.0.5以上版本 |
| executes | executes | int | 可选 | 0 | 性能调优 | 服务提供者每服务每方法最大可并行执行请求数 | 2.0.5以上版本 |
| actives | default.actives | int | 可选 | 0 | 性能调优 | 每服务消费者每服务每方法最大并发调用数 | 2.0.5以上版本 |
| proxy | proxy | string | 可选 | javassist | 性能调优 | 生成动态代理方式，可选：jdk/javassist | 2.0.5以上版本 |
| cluster | default.cluster | string | 可选 | failover | 性能调优 | 集群方式，可选：failover/failfast/failsafe/failback/forking | 2.0.5以上版本 |
| deprecated | deprecated | boolean | 可选 | false | 服务治理 | 服务是否过时，如果设为true，消费方引用时将打印服务过时警告error日志 | 2.0.5以上版本 |
| queues | queues | int | 可选 | 0 | 性能调优 | 线程池队列大小，当线程池满时，排队等待执行的队列大小，建议不要设置，当线程池满时应立即失败，重试其它服务提供机器，而不是排队，除非有特殊需求。 | 2.0.5以上版本 |
| charset | charset | string | 可选 | UTF-8 | 性能调优 | 序列化编码 | 2.0.5以上版本 |
| buffer | buffer | int | 可选 | 8192 | 性能调优 | 网络读写缓冲区大小 | 2.0.5以上版本 |
| iothreads | iothreads | int | 可选 | CPU + 1 | 性能调优 | IO线程池，接收网络读写中断，以及序列化和反序列化，不处理业务，业务线程池参见threads配置，此线程池和CPU相关，不建议配置。 | 2.0.5以上版本 |
| alive | alive | int | 可选 | | 服务治理 | 线程池keepAliveTime，默认单位为ms | 2.0.5以上版本 |
| telnet | telnet | string | 可选 | | 服务治理 | 所支持的telnet命令，多个命令用逗号分隔 | 2.0.5以上版本 |
| wait | wait | int | 可选 | | 服务治理 | 停服务时等待时间 | 2.0.5以上版本 |
| contextpath | contextpath | String | 可选 | 缺省为空串 | 服务治理 | 上下文路径 | 2.0.6以上版本 |
| layer | layer | string | 可选 | | 服务治理 | 服务提供者所在的分层。如：biz、dao、intl:web、china:acton。 | 2.0.7以上版本 |
| parameters | parameters | Map<string, string> | 可选 | | 服务治理 | 扩展参数 | 2.0.0以上版本 |

### consumer

服务消费者缺省值配置。配置类： `org.apache.dubbo.config.ConsumerConfig` 。同时该标签为 `<dubbo:reference>` 标签的缺省值设置。

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| timeout | default.timeout | int | 可选 | 1000 | 性能调优 | 远程服务调用超时时间(毫秒) | 1.0.16以上版本 |
| retries | default.retries | int | 可选 | 2 | 性能调优 | 远程服务调用重试次数，不包括第一次调用，不需要重试请设为0,仅在cluster为failback/failover时有效 | 1.0.16以上版本 |
| loadbalance | default.loadbalance | string | 可选 | random | 性能调优 | 负载均衡策略，可选值：<br/>* random - 随机; <br/>* roundrobin - 轮询; <br/>* leastactive - 最少活跃调用; <br/>* consistenthash - 哈希一致 (2.1.0以上版本); <br/>* shortestresponse - 最短响应 (2.7.7以上版本); | 1.0.16以上版本 |
| async | default.async | boolean | 可选 | false | 性能调优 | 是否缺省异步执行，不可靠异步，只是忽略返回值，不阻塞执行线程 | 2.0.0以上版本 |
| sent | default.sent | boolean | 可选 | true | 服务治理 | 异步调用时，标记sent=true时，表示网络已发出数据 | 2.0.6以上版本 |
| connections | default.connections | int | 可选 | 100 | 性能调优 | 每个服务对每个提供者的最大连接数，rmi、http、hessian等短连接协议支持此配置，dubbo协议长连接不支持此配置 | 1.0.16以上版本 |
| generic | generic | boolean | 可选 | false | 服务治理 | 是否缺省泛化接口，如果为泛化接口，将返回GenericService | 2.0.0以上版本 |
| check | check | boolean | 可选 | true | 服务治理 | 启动时检查提供者是否存在，true报错，false忽略 | 1.0.16以上版本 |
| proxy | proxy | string | 可选 | javassist | 性能调优 | 生成动态代理方式，可选：jdk/javassist | 2.0.5以上版本 |
| owner | owner | string | 可选 | | 服务治理 | 调用服务负责人，用于服务治理，请填写负责人公司邮箱前缀 | 2.0.5以上版本 |
| actives | default.actives | int | 可选 | 0 | 性能调优 | 每服务消费者每服务每方法最大并发调用数 | 2.0.5以上版本 |
| cluster | default.cluster | string | 可选 | failover | 性能调优 | 集群方式，可选：failover/failfast/failsafe/failback/forking/available/mergeable(2.1.0以上版本)/broadcast(2.1.0以上版本)/zone-aware(2.7.5以上版本) | 2.0.5以上版本 |
| filter | reference.filter | string | 可选 |   | 性能调优 | 服务消费方远程调用过程拦截器名称，多个名称用逗号分隔 | 2.0.5以上版本 |
| listener | invoker.listener | string | 可选 | | 性能调优 | 服务消费方引用服务监听器名称，多个名称用逗号分隔 | 2.0.5以上版本 |
| registry | | string | 可选 | 缺省向所有registry注册 | 配置关联 | 向指定注册中心注册，在多个注册中心时使用，值为&lt;dubbo:registry&gt;的id属性，多个注册中心ID用逗号分隔，如果不想将该服务注册到任何registry，可将值设为N/A | 2.0.5以上版本 |
| layer | layer | string | 可选 | | 服务治理 | 服务调用者所在的分层。如：biz、dao、intl:web、china:acton。 | 2.0.7以上版本 |
| init | init | boolean | 可选 | false | 性能调优 | 是否在afterPropertiesSet()时饥饿初始化引用，否则等到有人注入或引用该实例时再初始化。 | 2.0.10以上版本 |
| cache | cache | string/boolean | 可选 | | 服务治理 | 以调用参数为key，缓存返回结果，可选：lru, threadlocal, jcache等 | 2.1.0及其以上版本支持 |
| validation | validation | boolean | 可选 | | 服务治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 | 2.1.0及其以上版本支持 |
| version | version | string | 可选 | | 服务治理 | 在 Dubbo 中为同一个服务配置多个版本 | 2.2.0及其以上版本支持 |
| client | client | string | 可选 | dubbo协议缺省为netty | 性能调优 | 协议的客户端实现类型，比如：dubbo协议的mina,netty等 | 2.0.0以上版本 |
| threadpool | threadpool | string | 可选 | fixed | 性能调优 | 线程池类型，可选：fixed/cached/limit(2.5.3以上)/eager(2.6.x以上) | 2.0.5以上版本 |
| corethreads | corethreads | int | 可选 | 200 | 性能调优 | 线程池核心线程大小 | 2.0.5以上版本 |
| threads | threads | int | 可选 | 200 | 性能调优 | 服务线程池大小(固定大小) | 2.0.5以上版本 |
| queues | queues | int | 可选 | 0 | 性能调优 | 线程池队列大小，当线程池满时，排队等待执行的队列大小，建议不要设置，当线程池满时应立即失败，重试其它服务提供机器，而不是排队，除非有特殊需求。 | 2.0.5以上版本 |
| shareconnections | shareconnections | int | 可选 | 1 | 性能调优| 共享连接数。当connection参数设置为0时，会启用共享方式连接，默认只有一个连接。仅支持dubbo协议 | 2.7.0以上版本 |
| referThreadNum | | int | 可选 | | 性能优化 | 异步调用线程池大小 | 3.0.0以上版本 |
| meshEnable | mesh-enable| boolean | 可选 | false | Service Mesh | Dubbo Mesh模式的开关。开启后，可适配SideCar模式，将Dubbo服务调用转换为K8S标准调用。仅支持Triple协议，兼容GRPC。设置为true后，原生对接K8S，无需第三方注册中心，设置dubbo.registry.address=N/A即可 | 3.1.0以上版本 |
| parameters | parameters | Map<string, string> | 可选 | | 服务治理 | 扩展参数 | 2.0.0以上版本 |

### metrics

指标配置。配置类： `org.apache.dubbo.config.MetricsConfig`

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| protocol | protocol | string | 可选 | prometheus | 性能调优 | 协议名称，默认使用prometheus | 3.0.0以上版本 |
| prometheus | | PrometheusConfig | 可选 | | 配置关联 | prometheus相关配置 | 3.0.0以上版本 |
| aggregation | | AggregationConfig | 可选 | | 配置关联 | 指标聚合相关配置 | 3.0.0以上版本 |

- PrometheusConfig 对应类：`org.apache.dubbo.config.nested.PrometheusConfig`

| 属性 | 类型 | 是否必填 | 缺省值 | 描述 |
| --- | --- | ---- | --- | --- |
| exporter.enabled | boolean | 可选 | | 是否启用prometheus exporter | 
| exporter.enableHttpServiceDiscovery | boolean | 可选 | | 是否启用http服务发现 |
| exporter.httpServiceDiscoveryUrl | string | 可选 | | http服务发现地址 |
| exporter.metricsPort | int | 可选 | | 当使用pull方法时，暴露的端口号 |
| exporter.metricsPath | string | 可选 | | 当使用pull方法时，暴露指标的路径 |
| pushgateway.enabled | boolean | 可选 | | 是否可以通过prometheus的Pushgateway发布指标 |
| pushgateway.baseUrl | string | 可选 | | Pushgateway地址 |
| pushgateway.username | string | 可选 | | Pushgateway用户名 |
| pushgateway.password | string | 可选 | | Pushgateway密码 |
| pushgateway.pushInterval | int | 可选 | | 推送指标间隔时间 |

- AggregationConfig 对应类：`org.apache.dubbo.config.nested.AggregationConfig`

| 属性 | 类型 | 是否必填 | 缺省值 | 描述 |
| --- | --- | ---- | --- | --- |
| enabled | boolean | 可选 | | 是否开启本地指标聚合功能 |
| bucketNum | int | 可选 | | 时间窗口存储桶个数 |
| timeWindowSeconds | int | 可选 | | 时间窗口时长（s） |


### ssl

TLS认证配置。配置类： `org.apache.dubbo.config.SslConfig`

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| serverKeyCertChainPath | server-key-cert-chain-path | string | 可选 | | 安全配置 | 服务端签名证书路径 | 2.7.5以上版本 |
| serverPrivateKeyPath | server-private-key-path | string | 可选 | | 安全配置 | 服务端私钥路径 | 2.7.5以上版本 |
| serverKeyPassword | server-key-password | string | 可选 | | 安全配置 | 服务端密钥密码 | 2.7.5以上版本 |
| serverTrustCertCollectionPath | server-trust-cert-collection-path | string | 可选 | | 安全配置 | 服务端信任证书路径 | 2.7.5以上版本 |
| clientKeyCertChainPath | client-key-cert-chain-path | string | 可选 | | 安全配置 | 客户端签名证书路径 | 2.7.5以上版本 |
| clientPrivateKeyPath | client-private-key-path | string | 可选 | | 安全配置 | 客户端私钥路径 | 2.7.5以上版本 |
| clientKeyPassword | client-key-password | string | 可选 | | 安全配置 | 客户端密钥密码 | 2.7.5以上版本 |
| clientTrustCertCollectionPath | client-trust-cert-collection-path | string | 可选 | | 安全配置 | 客户端信任证书路径 | 2.7.5以上版本 |

### module

模块信息配置。对应的配置类 `org.apache.dubbo.config.ModuleConfig`

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| name | module | string | <b>必填</b> | | 服务治理 | 当前模块名称，用于注册中心计算模块间依赖关系 | 2.2.0以上版本 |
| version | module.version | string | 可选 | | 服务治理 | 当前模块的版本 | 2.2.0以上版本 |
| owner | module.owner | string | 可选 | | 服务治理 | 模块负责人，用于服务治理，请填写负责人公司邮箱前缀 | 2.2.0以上版本 |
| organization | module.organization | string | 可选 | | 服务治理 | 组织名称(BU或部门)，用于注册中心区分服务来源，此配置项建议不要使用autoconfig，直接写死在配置中，比如china,intl,itu,crm,asc,dw,aliexpress等 | 2.2.0以上版本 |
| background | background | boolean | 可选 | | 性能调优 | 是否开启后台启动模式。如果开启，无需等待spring ContextRefreshedEvent事件完成 | 3.0.0以上版本 |
| referAsync | referAsync | boolean | 可选 | | 性能调优 | 消费端是否开启异步调用 | 3.0.0以上版本 |
| referThreadNum | referThreadNum | int | 可选 | | 性能调优 | 异步调用线程池大小 | 3.0.0以上版本 |
| exportAsync | exportAsync | boolean | 可选 | | 性能调优 | 服务端是否开启导出 | 3.0.0以上版本 |
| exportThreadNum | exportThreadNum | int | 可选 | | 异步导出线程池大小 | | 3.0.0以上版本 |

### monitor

监控中心配置。对应的配置类： `org.apache.dubbo.config.MonitorConfig`

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| protocol | protocol | string | 可选 | dubbo | 服务治理 | 监控中心协议，如果为protocol="registry"，表示从注册中心发现监控中心地址，否则直连监控中心。 | 2.0.9以上版本 |
| address | &lt;url&gt; | string | 可选 | | 服务治理 | 直连监控中心服务器地址，address="10.20.130.230:12080" | 1.0.16以上版本 |
| username | username | string | 可选 | | 服务治理 | 监控中心用户名 | 2.0.9以上版本 |
| password | password | string | 可选 | | 服务治理 | 监控中心密码 | 2.0.9以上版本 |
| group | group | string | 可选 | | 服务治理 | 分组 | 2.0.9以上版本 |
| version | version | string | 可选 | | 服务治理 | 版本号 | 2.0.9以上版本 |
| interval | interval | string | 可选 | | 服务治理 | 间隔时间 | 2.0.9以上版本 |
| parameters | parameters | Map<string, string> | 可选 |  | 自定义参数 | 2.0.0以上版本 |

### method

方法级配置。对应的配置类： `org.apache.dubbo.config.MethodConfig`。同时该标签为 `service` 或 `reference` 的子标签，用于控制到方法级。

比如:

```xml
<dubbo:reference interface="com.xxx.XxxService">
   <dubbo:method name="findXxx" timeout="3000" retries="2" />
</dubbo:reference>
```

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| name | | string | <b>必填</b> | | 标识 | 方法名 | 1.0.8以上版本 |
| timeout | &lt;methodName&gt;.timeout | int | 可选 | 缺省为的timeout | 性能调优 | 方法调用超时时间(毫秒) | 1.0.8以上版本 |
| retries | &lt;methodName&gt;.retries | int | 可选 | 缺省为&lt;dubbo:reference&gt;的retries | 性能调优 | 远程服务调用重试次数，不包括第一次调用，不需要重试请设为0 | 2.0.0以上版本 |
| loadbalance | &lt;methodName&gt;.loadbalance | string | 可选 | 缺省为的loadbalance | 性能调优 | 负载均衡策略，可选值：<br/>* random - 随机; <br/>* roundrobin - 轮询; <br/>* leastactive - 最少活跃调用; <br/>* consistenthash - 哈希一致 (2.1.0以上版本); <br/>* shortestresponse - 最短响应 (2.7.7以上版本); | 2.0.0以上版本 |
| async | &lt;methodName&gt;.async | boolean | 可选 | 缺省为&lt;dubbo:reference&gt;的async | 性能调优 | 是否异步执行，不可靠异步，只是忽略返回值，不阻塞执行线程 | 1.0.9以上版本 |
| sent | &lt;methodName&gt;.sent | boolean | 可选 | true | 性能调优 | 异步调用时，标记sent=true时，表示网络已发出数据 | 2.0.6以上版本 |
| actives | &lt;methodName&gt;.actives | int | 可选 | 0 | 性能调优 | 每服务消费者最大并发调用限制 | 2.0.5以上版本 |
| executes | &lt;methodName&gt;.executes | int | 可选 | 0 | 性能调优 | 每服务每方法最大使用线程数限制&#45; &#45;，此属性只在&lt;dubbo:method&gt;作为&lt;dubbo:service&gt;子标签时有效 | 2.0.5以上版本 |
| deprecated | &lt;methodName&gt;.deprecated | boolean | 可选 | false | 服务治理 | 服务方法是否过时，此属性只在&lt;dubbo:method&gt;作为&lt;dubbo:service&gt;子标签时有效 | 2.0.5以上版本 |
| sticky | &lt;methodName&gt;.sticky | boolean | 可选 | false | 服务治理 | 设置true 该接口上的所有方法使用同一个provider.如果需要更复杂的规则，请使用路由 | 2.0.6以上版本 |
| return | &lt;methodName&gt;.return | boolean | 可选 | true | 性能调优 | 方法调用是否需要返回值,async设置为true时才生效，如果设置为true，则返回future，或回调onreturn等方法，如果设置为false，则请求发送成功后直接返回Null | 2.0.6以上版本 |
| oninvoke | attribute属性，不在URL中体现 | String | 可选 | | 性能调优 | 实例执行前拦截 | 2.0.6以上版本 |
| onreturn | attribute属性，不在URL中体现 | String | 可选 | | 性能调优 | 实例执行返回后拦截 | 2.0.6以上版本 |
| onthrow | attribute属性，不在URL中体现 | String | 可选 | | 性能调优 | 实例执行有异常拦截 | 2.0.6以上版本 |
| oninvokeMethod | attribute属性，不在URL中体现 | String | 可选 | | 性能调优 | 方法执行前拦截 | 2.0.6以上版本 |
| onreturnMethod | attribute属性，不在URL中体现 | String | 可选 | | 性能调优 | 方法执行返回后拦截 | 2.0.6以上版本 |
| onthrowMethod | attribute属性，不在URL中体现 | String | 可选 | | 性能调优 | 方法执行有异常拦截 | 2.0.6以上版本 |
| cache | &lt;methodName&gt;.cache | string/boolean | 可选 | | 服务治理 | 以调用参数为key，缓存返回结果，可选：lru, threadlocal, jcache等 | 2.1.0以上版本 |
| validation | &lt;methodName&gt;.validation | boolean | 可选 | | 服务治理 | 是否启用JSR303标准注解验证，如果启用，将对方法参数上的注解进行校验 | 2.1.0以上版本 |

### argument

方法参数配置。对应的配置类： `org.apache.dubbo.config.ArgumentConfig`。该标签为 `method` 的子标签，用于方法参数的特征描述，比如 XML 格式：

```xml
<dubbo:method name="findXxx" timeout="3000" retries="2">
   <dubbo:argument index="0" callback="true" />
</dubbo:method>
```

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| index | | int | <b>必填</b> | | 标识 | 参数索引 | 2.0.6以上版本 |
| type | | String | 与index二选一 | | 标识 | 通过参数类型查找参数的index | 2.0.6以上版本 |
| callback | &lt;metodName&gt;&lt;index&gt;.callback | boolean | 可选 | | 服务治理 | 参数是否为callback接口，如果为callback，服务提供方将生成反向代理，可以从服务提供方反向调用消费方，通常用于事件推送. | 2.0.6以上版本 |

### parameter

选项参数配置。对应的配置类：`java.util.Map`。同时该标签为 `protocol` 或 `service` 或 `provider` 或 `reference` 或 `consumer` 或 `monitor` 或 `registry` 或 `metadata-config` 或 `config-center` 的子标签，用于配置自定义参数，该配置项将作为扩展点设置自定义参数使用。

比如：

```xml
<dubbo:protocol name="napoli">
   <dubbo:parameter key="http://10.20.160.198/wiki/display/dubbo/napoli.queue.name" value="xxx" />
</dubbo:protocol>
```

也可以：

```xml
<dubbo:protocol name="jms" p:queue="xxx" />
```

| 属性 | 对应URL参数 | 类型 | 是否必填 | 缺省值 | 作用 | 描述 | 兼容性 |
| --- | --- | ---- | --- | --- | --- | --- | --- |
| key | key | string | <b>必填</b> | | 服务治理 | 路由参数键 | 2.0.0以上版本 |
| value | value | string | <b>必填</b> | | 服务治理 | 路由参数值 | 2.0.0以上版本 |

### 环境变量
支持的 key 有以下两个：

1. `dubbo.labels`，指定一些列配置到 URL 中的键值对，通常通过 JVM -D 或系统环境变量指定。

   增加以下配置：

    ```properties
    # JVM
    -Ddubbo.labels = "tag1=value1; tag2=value2"
    # 环境变量
    DUBBO_LABELS = "tag1=value1; tag2=value2"
    ```

   最终生成的 URL 会包含 tag1、tag2 两个 key: `dubbo://xxx?tag1=value1&tag2=value2`

2. `dubbo.env.keys`，指定环境变量 key 值，Dubbo 会尝试从环境变量加载每个 key

    ```properties
    # JVM
    -Ddubbo.env.keys = "DUBBO_TAG1, DUBBO_TAG2"
    # 环境变量
    DUBBO_ENV_KEYS = "DUBBO_TAG1, DUBBO_TAG2"
    ```

   最终生成的 URL 会包含 DUBBO_TAG1、DUBBO_TAG2 两个 key: `dubbo://xxx?DUBBO_TAG1=value1&DUBBO_TAG2=value2`
### 其他配置
#### config-mode
**背景**

在每个dubbo应用中某些种类的配置类实例只能出现一次（比如`ApplicationConfig`、`MonitorConfig`、`MetricsConfig`、`SslConfig`、`ModuleConfig`），有些能出现多次（比如`RegistryConfig`、`ProtocolConfig`等）。

如果应用程序意外的扫描到了多个唯一配置类实例（比如用户在一个dubbo应用中错误了配置了两个`ApplicationConfig`），应该以哪种策略来处理这种情况呢？是直接抛异常？是保留前者忽略后者？是忽略前者保留后者？还是允许某一种形式的并存（比如后者的属性覆盖到前者上）？

目前dubbo中的唯一配置类类型和以及某唯一配置类型找到多个实例允许的配置模式/策略如下。

**唯一配置类类型**

`ApplicationConfig`、`MonitorConfig`、`MetricsConfig`、`SslConfig`、`ModuleConfig`。

前四个属于应用级别的，最后一个属于模块级别的。

**配置模式**

- `strict`：严格模式。直接抛异常。
- `override`：覆盖模式。忽略前者保留后者。
- `ignore`：忽略模式。忽略后者保留前者。
- `override_all`：属性覆盖模式。不管前者的属性值是否为空，都将后者的属性覆盖/设置到前者上。
- `override_if_absent`：若不存在则属性覆盖模式。只有前者对应属性值为空，才将后者的属性覆盖/设置到前者上。

注：后两种还影响配置实例的属性覆盖。因为dubbo有多种配置方式，即存在多个配置源，配置源也有优先级。比如通过xml方式配置了一个`ServiceConfig`且指定属性`version=1.0.0`，同时我们又在外部配置(配置中心)中配置了`dubbo.service.{interface}.version=2.0.0`，在没有引入`config-mode`配置项之前，按照原有的配置源优先级，最终实例的`version=2.0.0`。但是引入了`config-mode`配置项之后，配置优先级规则也不再那么严格，即如果指定`config-mode为override_all`则为`version=2.0.0`，如果`config-mode为override_if_absent`则为`version=1.0.0`，`config-mode`为其他值则遵循原有配置优先级进行属性设值/覆盖。

**配置方式**

配置的key为`dubbo.config.mode`，配置的值为如上描述的几种，默认的策略值为`strict`。下面展示了配置示例

```properties
# JVM -D
-Ddubbo.config.mode=strict

# 环境变量
dubbo.config.mode=strict

# 外部配置(配置中心)、Spring应用的Environment、dubbo.properties
dubbo.config.mode=strict
```
