# Springboot 开发网页【idea】

### 一、创建Springboot项目

- File->new->project->Spring Initializr(java 8)->

  [<u>lombok、spring web、mybatis、mysql</u>]

- 选择maven，点击工具图标

### 二、创建MySQL数据库

### 三、项目结构

- com.example.hellospring

  - <u>controller：控制器层</u>【控制器作用：通过控制器接收用户的注册请求，当接收到请求后，控制器自身并不实现插入数据的操作，而是调用持久层对象来完成插入数据，最后，将结果响应给客户端】

    - basecontroller：控制器的基类，SUCCESS
    - studentcontroller：处理学生相关请求的控制器类
      - 引入model.studententity
      - 引入service.IStudentService
      - 引入util.ResponseResult
      - 引入BaseController.SUCCESS
      - 执行查询，返回ResponseResult

  - <u>mapper：持久层</u>

    - studentmapper：处理学生数据的持久层**接口**interface
      - 引入model.studententity
      - 获取所有学生列表并返回

  - <u>model/entity：实体层</u>

    - studententity

      - serialVersionUID【implements Serializable】

      - 定义id,name,age,gender

  - <u>service：业务层</u>

    - ex：Exception类

    - impl：implement实现业务接口类

      - studentservicelmpl：实现业务接口处理学生数据的业务层**接口**interface
        - 引入model.studententity
        - 引入mapper.studentmapper
        - 引入service.Istudentservice
        - 实现Istudentservice中的抽象方法，返回studentmapper中的获取列表

    - Istudentservice：创建业务接口类，添加抽象方法

      - 引入model.studententity

      - 抽象方法获取学生列表

  - <u>util：工具类</u>

    - responseresult：响应JSON结果的类

  - config：配置类

  - interceptor：拦截器配置

  - <u>HellospringApplication：启动类</u>

- resources

  - mapper：配置抽象方法匹配的映射，编写SQL语句
    - studentmapper.xml：获取所有学生信息列表（select语句）
  - static：静态资源
    - js
    - web
      - test.html
      - student.html：导入jquery【先】和bootstrap【后】
      - webjars (应放在templates下？)
        - jquery
        - bootstrap
  - templates
  - **application.properties**
    - 端口
    - 数据库连接参数
    - Mybatis配置
    - 去除CONDITIONS EVALUATION REPORT启动信息：logging:level:org:springframework: boot:autoconfigure:logging: info

- test：测试main中的类

  - com.example.hellospring
    - mapper
      - studentmapperTest
        - 引入model.studententity
    - service
      - studentserviceTest
        - 引入model.studententity
    - hellospringapplicationTest

- **pom.xml**

- 运行启动类，访问localhost:8082/hellospring/student

### 四、整合前端界面

springboot整合ajax前端

- rescources/static/web/student.html
- 运行启动类，访问：localhost:8082/web/student.html