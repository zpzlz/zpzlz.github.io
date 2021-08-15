# Springboot + Vue 前后端分离开发

### 一、Vue项目

- 创建与运行

  - cmd->vue ui
  - 创建项目->手动配置->选择Router和Vuex(取消Linter/Formatter代码校验)
  - idea里打开项目，idea内命令行运行cnpm run serve

- 报错

  - Module Error (from ./node_modules/eslint-loader/index.js):

    - 解决：

      module.exports={

    ​           lintOnSave: false,

    ​        }

  - Failed to load plugin 'html' declared in '.eslintrc.js'

    - 解决：

      cnpm install eslint-plugin-html

- Element UI后台管理系统主要的标签

  - el-container：构建整个页面框架
  - el-aside：构建左侧菜单栏
  - el-menu：左侧菜单内容
    - default-openeds：默认<u>展开</u>的菜单，通过菜单的index值来关联
    - default-active：默认<u>选中</u>的菜单，通过菜单的index值来关联
  - el-submenu：<u>可展开</u>的菜单，常用属性：
    - index：菜单的下标，文本类型，不能是数值类型
  - template：对应el-submenu的菜单名
  - i：设置菜单<u>图标</u>，通过class属性设置
    - el-icon-message
    - el-icon-menu
    - el-icon-config
  - el-menu-item：菜单的子节点，<u>不可再展开</u>，常用属性：
    - index：菜单的下标，文本类型，不能是数值类型

- vue router动态构建左侧菜单

  - 导航1
    - 页面1
    - 页面2
  - 导航2
    - 页面3
    - 页面4

- menu与router的绑定

  - 1.<el-menu>标签添加router属性
  - 2.在页面中添加<router-view>标签，它是一个容器，动态渲染你选择的router
  - 3.<el-menu-item>标签的index值就是要跳转的router

- mybatis分页插件pagehelper

  - 分页查询两种实现方式

    - 一、直接在sql中使用limit子句进行查询【未验证】
      - limit [offset,] rows
      - select * from tableA limit 5,5
      - Ps1：offset是相对于首行的偏移量(首行是0)，rows是返回条数
      - Ps2：mapper中可以传变量，即在实际使用的时候 “offset与rows”可以用变量替代
      - 信息需要自己写，太麻烦
    - 二、第三方库进行分页查询，如mybatis插件pagehelper

  - 不起作用：

    - 注意pom.xml应导入spring版本的依赖：pagehelper-spring-boot-starter

    - 配置properties文件：

      pagehelper.helper-dialect=mysql
      pagehelper.params=count=countSql
      pagehelper.reasonable=true
      pagehelper.support-methods-arguments=true

- Element UI表单数据校验

  - :model：绑定数据

    :rules：绑定校验规则

  - 定义rules对象，在rules对象中设置表单各个选项的校验规则

    - required:true，是否为必填项
    - message:'error'，提示信息
    - trigger:'blue'，触发事件
  
- 修改数据

  - $router：跳转页面

    $route：取参数

  - 取不到查询数据，要用data.data

### 二、SpringBoot项目

- 运行Application
- 插入数据
  - 若mybatis数据库设置主键自增，需在项目中配置
    - xml文件中的插入sql配置自增长主键(useGeneratedKeys="true" keyProperty="id")
  - postman中进行测试
    - 输入url：http://localhost:8082/demo/insertdata
    - 输入参数
  - 报错Error updating database.The error may involve defaultParameterMap
    - 修改变量名，变量名可能是关键字
    - @RequestBody注解
- 修改数据
  - 报错check the manual that corresponds to your MySQL server version for the right syntax to use near 
    - sql语句多了个逗号(多为语法问题)
- 删除数据
  - 505
    - 在拼装mysql链接的url时，为其加上allowMultiQueries参数，设置为true：允许多条查询

### 三、运行界面

- ![image-20210730170634592](C:\Users\p'z'l\AppData\Roaming\Typora\typora-user-images\image-20210730170634592.png)
- ![image-20210730170654625](C:\Users\p'z'l\AppData\Roaming\Typora\typora-user-images\image-20210730170654625.png)

- ![image-20210814190250580](C:\Users\p'z'l\AppData\Roaming\Typora\typora-user-images\image-20210814190250580.png)