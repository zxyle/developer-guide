

大于号 <![CDATA[ > ]]>



| 说明       | 符号 | 字段     | 释义                  |
| ---------- | ---- | -------- | --------------------- |
| 大于号     | >    | `&gt;`   | Greater than          |
| 大于等于号 | >=   | `&gt;=`  | Greater than or equal |
| 小于号     | <    | `&lt;`   | less than             |
| 小于等于号 | <=   | `&lt;=`  | less than or equal    |
| 与         | &    | `&amp;`  | ampersand             |
| 单引号     | '    | `&apos;` | apostrophe            |
| 双引号     | "    | `&quot;` | quotation             |



## resultType

输出参数对象



## paramterType

输入参数对象



### OGNL表达式

```xml
<if test="username == 'admin'">
```



### IN 查询

```xml
<select id="selectPostIn" resultType="domain.blog.Post">
 SELECT * FROM POST P
 WHERE ID in
 <foreach item="item" index="index" collection="list"  open="(" separator="," close=")">
    #{item, jdbcType=BIGINT}
 </foreach>
</select>
```



### 判断集合是否为空

```xml
<if test="deviceKinds!=null and deviceKinds.size() > 0">

</if>
```



### 判断数组是否为空

```xml
<if test="deviceKinds!=null and deviceKinds.length > 0">

</if>
```



### `$` 和`#`区别

美元符不会转义

井号会转义



### resultMap

自定义映射

```xml

<resultMap id="empResultMap" type="Emp">
  <id property="主键属性名" column="主键字段名"></id>
  <result property="属性名" column="字段名"></result>
  <result property="dept.did" column="did"></result>
  <result property="dept.deptName" column="dept_name"></result>
  <association property="" javaType="Dept">
    <id></id>
    <result></result>
  
  </association>
  <collection
</resultMap>
```

