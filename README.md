# 入职考核的一个动态表格

## 需求

- 表头能自定义编辑
- 数据可编辑
- 多行表头
- 数据量很大的展示优化
- 面向对象编程
- * 封装可复用
- * 表格显示控制, 哪一些数据需要显示
- * 可编辑，不可编辑的权限
- * 需要用户直接设计模型 OR 用户编辑表格，模型就构建好了。 这是一个如何初始化的问题
- * 表头排序问题

## 表头设计

假如含有子表头就渲染为二级的 colspan = 2,否则就 rowspam = children.length;

### 逻辑: 编辑表头 

    1、统一界面编辑
    2、原界面编辑

#### 表头的操作

    
    1. 增加列
    2. 增加子列
    3. 编辑列名
    4. 删除列 （用户删除列之后就数据库删除该行数据）
    
    操作完都要更新页面


#### 数据的操作

    1. 增加行  （增加按钮，弹窗添加，表格是根据表头生成）
    2. 删除行   (可以多选删除， 删除是需要用户确认)
    3. 编辑行  （只能编辑单行，编辑完就保存）

#### 做法

    组件封装的流程， 利用easy UI 赋能

#### 用户操作流程

    - 创建表格
    - 编辑列
    - 编辑数据

#### 数据库设计

    - 字段映射表 （ID、Name、Perant(假如是一级的标签，那么parent是root, 否则就是二级表头)、描述、order ）
    - 数据表  

####  疑问

    - 数据库设计
    - 应用场景
    - 新增数据时的数据校验，所以新增列是否要添加值校验的校验器; 简单的设置一下校验器
    - 是否要不可删改的字段配置
    - 并不需要封装， 只需要一个配置转换就好了，还有一些交互
    - 创建后是否可以修改
    - 复用场景： 同一个页面的复用, 不同页面的复用，代码封装好久可以了

#### 目标 明日出一个demo

##### 表现形式

    1. 自定义美化
    2. 组件封装 感觉不能成为一个组件

    可配置，

##### 总结，表格的更新与data的关系；
    - 删除行 ，编辑行 data 会更新
    - 新增行不会更新
    - $('#tg').treegrid('getData')

##### bug 
    - 考虑一下只有一维的情况
    - 假如需求变成是三列呢