XML和XML解析
=======
XML:eXtensible Markup Language 可扩展标记语言 version="1.0"
1. 可扩展：所有的标签都是自定义的
2. 功能：数据存储   
* 配置文件
* 数据传输
3. html与xml区别：
* html语法松散，xml语法严格
* html做页面展示，xml做数据存储
* html所有标签都是预定义的，xml所有标签都是自定义的   预定义 W3C:word wide web consortiem 万维网联盟
4. XML语法
* 文档声明：
  * 必须写在xml文档的第一行 
  * 写法：`<?xml version="1.0"?>`
  * 属性：
   * version:版本号 固定值 1.0
   * encoding:指定文档的码表。默认值为 iso-8859-1
   * standalone:指定文档是否独立 yes or no
 * 元素：xml文档中的标签
   * 文档中必须有且只能有一个根元素
   * 元素需要正确闭合。<book></book>
   * 元素名称要遵守：
     * 元素名称区分大小写
     * 数字不能开头
 * 文本：
   * 转移符:&get；
   * CDATA:里面的数据会原样显示 <![CDATA[数据内容]]>
 * 属性：
   * 属性值必须用引号括起来。单双引号都可以。
 * 注释 `<!---->`
 * 处理指令：现在基本不用 <?xml-stylesheet type="text/css" href="1.css"?>
 * xml约束：	约束就是xml的书写规则
 * 约束的分类：
   * dtd分类：
   1. 内部dtd：在xml内部定义dtd
   2. 外部dtd：在外部文件中定义dtd
   3. 本地dtd文件：<!DOCTYPE students SYSTEM  "student.dtd">
   4. 网络dtd文件：<!DOCTYPE students PUBLIC "名称空间"  "student.dtd">
   * schema：导入xsd约束文挡
   1. 编写根标签
   2. 引入实例名称空间 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   3. 引入名称空间 xsi:schemaLocation="http://www.itcast.cn/xml student.xsd"	
   4. 引入默认的名称空间


