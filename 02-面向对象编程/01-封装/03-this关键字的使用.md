### 一、`this` 的作用

**代表当前对象**

### 二、作用域

只能在构造器或方法内部使用

### 三、`this` 的应用场景

#### 1）用于重载（构造器重载或普通方法重载）

- 构造器重载
- 方法重载

#### 2）引用被局部作用域成员覆盖的同名变量或同名方法

在构造器中，使用 `this` 引用成员变量

```java
public class TestClass {
    private String name;
    
    public TestClass(String name) {
        this.name = name;
    }
}
```

在内部类中，引用外部类中同名的变量或方法

```java
public class ThisOuterClass {

  public void sayHello() {
    System.out.println("Hello From Outer Class");
  }

  public void shakeHands() {
    System.out.println("Shake Hands");
  }

  class InnerClass {
    public InnerClass() {
      // 调用的是当前类的sayHello()方法
      sayHello();
      // 与上面调用是等价的
      this.sayHello();
      // 调用的是外部类的sayHello()方法
      ThisOuterClass.this.sayHello();
      // 调用外部类的shakeHands()方法
      shakeHands();
    }
    public void sayHello() {
      System.out.println("Hello From Inner Class");
    }
  }
}
```

#### 3）Builder模式中用于构建链式方法

```java
TestClass instance = TestClass.builder().name("Xiaoming").age(30).build();
```

