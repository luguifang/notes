# 设计模式
## 1、面向对象设计原则
### 1.1、单一职责原则
    单一职责原则(Single Responsibility Principle, SRP)：一个类只负责一个功能领域中的相应职责，或者可以定义为：就一个类而言，
    应该只有一个引起它变化的原因。
### 1.2、开闭原则
    开闭原则(Open-Closed Principle, OCP)：一个软件实体应当对扩展开放，对修改关闭。
    即软件实体应尽量在不修改原有代码的情况下进行扩展。
### 1.3、里氏代换原则
    里氏代换原则(Liskov Substitution Principle, LSP)：所有引用基类（父类）的地方必须能透明地使用其子类的对象。
### 1.4、依赖倒转原则
    依赖倒转原则(Dependency Inversion  Principle, DIP)：抽象不应该依赖于细节，细节应当依赖于抽象。
    换言之，要针对接口编程，而不是针对实现编程。
### 1.5、接口隔离原则
    接口隔离原则(Interface  Segregation Principle, ISP)：使用多个专门的接口，而不使用单一的总接口，
    即客户端不应该依赖那些它不需要的接口。
### 1.6、合成复用原则
    合成复用原则(Composite Reuse Principle, CRP)：尽量使用对象组合，而不是继承来达到复用的目的。
### 1.7、迪米特法则
    迪米特法则(Law of  Demeter, LoD)：一个软件实体应当尽可能少地与其他实体发生相互作用。

## 2、设计模式分类
### 2.1、组件协作
#### 2.1.1、模板方法-Template Method================================

 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Template%20Method%20Pattern.png)
 
#### 2.1.2、策略模式-Strategy=======================================

 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Strategy%20Pattern.png)
 
### 2.1.3、观察者-Observer/Event===================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Observer%20Pattern.png)

## 2.2、单一职责
### 2.2.1 装饰器模式-Decorator=====================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Decorator%20Pattern.png)
 
### 2.2.2 桥模式-Bridge============================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Bridge%20Pattern.png)
## 2.3、对象创建
### 2.3.1 简单工厂-Simple Factory=================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Simple%20Factory%20Pattern.png)
 
### 2.3.2 工厂方法-Factory Method=================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Factory%20Method%20Pattern.png)
 
### 2.3.3 抽象工厂-Abstract Factory===============================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Abstract%20%20Factory%20Pattern.png)
 
### 2.3.4 原型模式-Prototype======================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Prototype%20Pattern.png)
 
### 2.3.5 创建者-Builder==========================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Builder%20Pattern.png)

## 2.4、对象性能
### 2.4.1、单列模式-Singleton=====================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Singleton%20Pattern.png)
 
### 2.4.2、享元模式-Flyweight=====================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Flyweight%20Pattern.png)

## 2.5、接口隔离
### 2.5.1、门面/外观模式-Facade===================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Facade%20Pattern.png)
 
### 2.5.2、代理模式-Proxy=========================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Proxy%20Pattern.png)
 
### 2.5.3、中介者-Mediator========================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Mediator%20Pattern.png)
 
### 2.5.4、适配器-Adapter========================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Adapter%20Pattern.png)
 
## 2.6、状态变化
### 2.6.1、备忘录-Memento========================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Memento%20Pattern.png)
 
### 2.6.2、状态模式-State========================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/State%20Pattern.png)

## 2.7、数据结构
### 2.7.1、组合模式-Composite===================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Composite%20Pattern.png)
 
### 2.7.2、迭代器-Iterator=====================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Iterator%20Pattern.png)
 
### 2.7.3、职责链-Chain-of-Responsibility======================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Chain%20of%20Responsibility%20Pattern.png)

## 2.8、行为变化
### 2.8.1、命令模式-Command=====================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Command%20Pattern.png)

### 2.8.2、访问者-Visitor======================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Visitor%20Pattern.png)

## 2.9、领域问题
### 2.9.1、解释器-Interpreter==================================
 ![image](https://github.com/luguifang/notes/blob/main/Refactor/image/Interpreter%20Pattern.png)
 
# 3、 什么时候不适合用模式
        * 代码可读性很差时
        * 需求理解还很浅时
        * 变化没有显现时
        * 不是系统的关键依赖点
        * 项目没有复用价值
        * 项目将要发布时

# 4、由于技术变化 不怎么使用的设计模式
        * 建造者
        * 中介者
        * 备忘录
        * 适配器
        * 职责链
        * 命令模式
        * 访问者
        * 解释器
    
