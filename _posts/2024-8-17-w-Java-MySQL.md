---

layout: post

title: "W-Java-MySQL"

date: 2024-8-17

tags: [java,MySQL]

comments: true

author: hyc

---



# 填空题

1. collection接口总，可以重复的接口是List，不可以重复的是Set

2. 什么是SQL：结构化查询语言

3. 查询英语成绩不为空的学院的sql语句：

   ```
   SELECT DISTINCT college
   FROM students
   WHERE english_score IS NOT NULL;
   ```

   

4. 模糊查询姓名第二个字是化的sql语句：

   ```
   SELECT *
   FROM students
   WHERE name LIKE '_化%';
   ```

   

5. 英语成绩升序排列的sql语句：

   ```
   SELECT *
   FROM students
   ORDER BY english_score ASC;
   
   ```

# ArrayList和LinkedList区别已经数组和集合区别？HashMap和HashTable区别？

 [W-Java – Nonsense's blog (huyaochao.github.io)](https://huyaochao.github.io/hyc.github.io/w-JavaBasic/) 

# java中什么是插箱和装箱

在 Java 中，**装箱（Boxing）** 和 **拆箱（Unboxing）** 是自动将基本数据类型与它们对应的包装类之间相互转换的过程。这些机制简化了基本数据类型和对象之间的操作，使得 Java 编程更加灵活。

### 1. 装箱（Boxing）
装箱是将 **基本数据类型** 转换为其对应的 **包装类** 对象的过程。

#### 基本数据类型和对应的包装类
- `byte` -> `Byte`
- `short` -> `Short`
- `int` -> `Integer`
- `long` -> `Long`
- `float` -> `Float`
- `double` -> `Double`
- `char` -> `Character`
- `boolean` -> `Boolean`

#### 举例说明
```java
int a = 10;
Integer aBoxed = a;  // 自动装箱，将int类型的a转换为Integer对象
```

在上面的例子中，变量 `a` 是一个基本类型 `int`，而 `aBoxed` 是一个 `Integer` 对象。Java 编译器在后台将基本类型 `int` 自动转换为其包装类 `Integer`，这是**自动装箱**的过程。

**手动装箱：**
```java
int a = 10;
Integer aBoxed = Integer.valueOf(a); // 手动装箱
```

### 2. 拆箱（Unboxing）
拆箱是将 **包装类对象** 转换为其对应的 **基本数据类型** 的过程。

#### 举例说明
```java
Integer aBoxed = 10;  // 自动装箱
int a = aBoxed;  // 自动拆箱，将Integer对象转换为int类型
```

在这个例子中，`aBoxed` 是 `Integer` 对象，而 `a` 是基本类型 `int`。Java 编译器自动将 `aBoxed` 拆箱为 `int`，这是**自动拆箱**的过程。

**手动拆箱：**
```java
Integer aBoxed = 10;
int a = aBoxed.intValue(); // 手动拆箱
```

### 3. 为什么需要装箱和拆箱？
- Java 中有两种类型：基本数据类型和引用类型。基本数据类型不能直接作为对象传递给方法，比如 `Collection` 类无法存储基本类型，只能存储对象。装箱使得我们可以将基本类型转换为对象，从而存储在集合类中。
- Java 5 引入了自动装箱和拆箱的特性，简化了代码编写。开发者无需显式调用转换方法，减少了冗余代码。

### 4. 注意事项
1. **性能问题**：装箱和拆箱会引入额外的性能开销，因为它们涉及到对象的创建和销毁。大量的装箱拆箱操作可能导致性能下降。
2. **空指针异常**：在自动拆箱时，如果对象为 `null`，会抛出 `NullPointerException`。
   ```java
   Integer aBoxed = null;
   int a = aBoxed;  // 这里会抛出 NullPointerException
   ```

### 5. 总结
- **装箱** 是将基本数据类型转换为其对应的包装类对象；
- **拆箱** 是将包装类对象转换为基本数据类型；
- 自动装箱和拆箱是 Java 5 之后的特性，简化了代码编写，但在性能和空值处理上需要注意。

# Overload和Override的区别



在 Java 中，**Overload（方法重载）** 和 **Override（方法重写）** 都是面向对象编程中的多态性实现方式，但它们的目的和使用场景不同。

### 1. **Overload（方法重载）**
**方法重载**指的是在**同一个类**中，定义多个方法，这些方法**具有相同的名称**，但**参数列表不同**（参数类型、数量或顺序不同）。返回类型可以相同或不同，但返回类型并不决定重载。

#### 特点
- 必须在同一个类中进行。
- 方法名相同，但参数列表必须不同（参数类型、数量、顺序）。
- 返回类型可以不同，但不会仅靠返回类型来区分方法。
- 可以应用于**构造方法**。



---

### 2. **Override（方法重写）**
**方法重写**指的是在**子类中**对**父类中的方法进行重新实现**，它允许子类根据自身的需求提供特定的实现，而不改变方法的签名（方法名称、参数类型和数量）。

#### 特点
- 必须在**继承关系**中使用（子类和父类）。
- 方法名、参数列表必须**与父类的方法相同**。
- 返回类型必须相同或是子类类型（Java 5 以后支持协变返回类型）。
- 访问修饰符不能比父类方法的更严格（例如，如果父类的方法是 `public`，子类不能将它改为 `protected`）。
- 可以使用 `@Override` 注解，帮助编译器检查是否正确重写了父类方法。

---

### 3. **Overload 和 Override 的区别**

| 特性           | **Overload（方法重载）**                       | **Override（方法重写）**             |
| -------------- | ---------------------------------------------- | ------------------------------------ |
| **发生位置**   | 同一个类中                                     | 子类与父类之间                       |
| **方法签名**   | 方法名相同，参数列表不同                       | 方法名、参数列表必须完全相同         |
| **返回类型**   | 可以相同或不同，但不能仅依赖返回类型来区分重载 | 必须相同或是子类类型（协变返回类型） |
| **访问修饰符** | 无严格要求                                     | 子类方法的修饰符不能比父类的更严格   |
| **注解**       | 通常不需要注解                                 | 建议使用 `@Override` 注解来显式声明  |
| **多态性**     | 静态多态性（编译时多态）                       | 动态多态性（运行时多态）             |
| **应用场景**   | 方法名相同但实现不同，提供不同的参数处理方式   | 子类提供对父类方法的不同实现         |

---

### 4. **总结**
- **方法重载**是在同一类中实现相同方法名但不同参数列表的功能，适用于不同参数类型或数量的操作。
- **方法重写**是子类提供对父类方法的不同实现，是实现动态多态的核心。

# WHERE和HAVING的区别

在 SQL 查询中，`WHERE` 和 `HAVING` 都用于对查询结果进行过滤，但它们在使用场景和作用对象上存在明显的区别。

### 1. **WHERE 子句**
`WHERE` 用于过滤**原始数据**，它作用于**从表中提取的记录**，对数据在**分组之前**进行过滤。

#### 特点
- `WHERE` 只能用于过滤表中的**原始行**，在数据进行分组操作（`GROUP BY`）之前执行。
- `WHERE` 子句不能用于聚合函数（如 `SUM()`、`COUNT()`、`AVG()` 等），因为在 `WHERE` 子句执行时，聚合操作尚未发生。
- 用于非聚合的条件过滤。

#### 语法
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

#### 举例说明
```sql
SELECT name, age
FROM employees
WHERE age > 30;
```
在这个查询中，`WHERE` 子句过滤所有 `age` 大于 30 的记录，查询结果将只包含符合条件的行。

---

### 2. **HAVING 子句**
`HAVING` 子句通常与**分组操作**（`GROUP BY`）一起使用，作用于**分组后的数据**，对聚合后的结果进行过滤。

#### 特点
- `HAVING` 用于过滤已经**分组后的结果**。
- `HAVING` 支持使用聚合函数（如 `SUM()`、`COUNT()`、`AVG()` 等），可以针对分组后的聚合结果进行过滤。
- 通常和 `GROUP BY` 搭配使用。

#### 语法
```sql
SELECT column1, aggregate_function(column2), ...
FROM table_name
GROUP BY column1
HAVING condition;
```

#### 举例说明
```sql
SELECT department, COUNT(*) AS employee_count
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```
在这个查询中，`HAVING` 子句过滤那些员工人数大于 5 的部门。这里 `COUNT(*) > 5` 是对**聚合结果**的过滤，而不是对原始数据的过滤。

---

### 3. **WHERE 和 HAVING 的主要区别**

| 特点               | **WHERE**                         | **HAVING**                             |
| ------------------ | --------------------------------- | -------------------------------------- |
| **作用阶段**       | 在**分组前**过滤数据              | 在**分组后**过滤数据                   |
| **适用于聚合函数** | 不能用于聚合函数                  | 可以与聚合函数一起使用                 |
| **使用场景**       | 用于过滤表中的原始数据            | 用于过滤聚合后的数据                   |
| **语法位置**       | 位于 `GROUP BY` 之前              | 位于 `GROUP BY` 之后                   |
| **应用示例**       | 过滤单行数据，如 `WHERE age > 30` | 过滤聚合数据，如 `HAVING COUNT(*) > 5` |

---

### 4. **综合实例：WHERE 和 HAVING 的联合使用**

有时，我们需要同时使用 `WHERE` 和 `HAVING` 来分别过滤原始数据和聚合后的结果。

```sql
SELECT department, AVG(salary) AS avg_salary
FROM employees
WHERE age > 30  -- 对原始数据进行过滤
GROUP BY department
HAVING AVG(salary) > 50000;  -- 对聚合结果进行过滤
```

- `WHERE age > 30`：先过滤出年龄大于 30 的员工。
- `HAVING AVG(salary) > 50000`：然后对分组后的结果过滤出平均工资大于 50000 的部门。

### 5. **总结**
- `WHERE` 在**分组前**过滤数据，不能用于聚合函数。
- `HAVING` 在**分组后**过滤数据，适用于聚合函数。
- 两者可以结合使用，先用 `WHERE` 过滤原始数据，再用 `HAVING` 过滤聚合后的结果。



# SQL练习

