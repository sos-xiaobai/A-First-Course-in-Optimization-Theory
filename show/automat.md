<!-- TOC -->

- [状态机](#状态机)
  - [1. 什么是状态机](#1-什么是状态机)
    - [1.1 状态机的基本定义](#11-状态机的基本定义)
    - [1.2 举个栗子](#12-举个栗子)
    - [1.3 总结一下](#13-总结一下)
  - [2. 状态机](#2-状态机)
    - [2.1 状态机的四大概念](#21-状态机的四大概念)
    - [2.2 举个栗子](#22-举个栗子)
    - [2.3 总结一下](#23-总结一下)
  - [3. 状态机各行业的应用](#3-状态机各行业的应用)
  - [4. 状态机对电控程序的帮助](#4-状态机对电控程序的帮助)
    - [4.1 为我所用的东西](#41-为我所用的东西)
  - [5. 伪代码实现](#5-伪代码实现)
  - [6. 参考资料](#6-参考资料)

<!-- /TOC -->
# 状态机

## 1. 什么是状态机
### 1.1 状态机的基本定义
>状态机是有限状态自动机的简称，是现实事物运行规则抽象而成的一个数学模型。
### 1.2 举个栗子
先来解释什么是“状态”（ State ）。现实事物是有不同状态的，例如一个自动门，就有 open 和 closed 两种状态。我们通常所说的状态机是有限状态机，也就是被描述的事物的状态的数量是有限个，例如自动门的状态就是两个 open 和 closed 。

状态机，也就是 State Machine ，不是指一台实际机器，而是指一个数学模型。说白了，一般就是指一张状态转换图。例如，根据自动门的运行规则，我们可以抽象出下面这么一个图。

![](https://github.com/sos-xiaobai/A-First-Course-in-Optimization-Theory/blob/main/images/v2-6592767bc90a8c71b2743e8fedaa6b00_r.jpg?raw=true)

自动门有两个状态，open 和 closed ，closed 状态下，如果读取开门信号，那么状态就会切换为 open 。open 状态下如果读取关门信号，状态就会切换为 closed 。
### 1.3 总结一下
>状态机的全称是有限状态自动机，是现实事物运行规则抽象而成的一个数学模型，给定一个状态机，同时给定它的当前状态以及输入，那么输出状态时可以明确的运算出来的。
## 2. 状态机
### 2.1 状态机的四大概念

- **State ，状态**。一个状态机至少要包含两个状态。例如上面自动门的例子，有 open 和 closed 两个状态。  
- **Event ，事件**。事件就是执行某个操作的触发条件或者口令。对于自动门，“按下开门按钮”就是一个事件。  
- **Action ，动作**。事件发生以后要执行动作。例如事件是“按开门按钮”，动作是“开门”。编程的时候，一个 Action 一般就对应一个函数。  
- **Transition ，变换**。也就是从一个状态变化为另一个状态。例如“开门过程”就是一个变换。
### 2.2 举个栗子
这幅图就是一个**状态机**  
![](https://github.com/sos-xiaobai/A-First-Course-in-Optimization-Theory/blob/main/images/v2-d969ec28d841bde7c135db2720a03a8b_r.png?raw=true)
### 2.3 总结一下
>满足**状态，事件，动作，变换**这四个要求的系统就叫做状态机
## 3. 状态机各行业的应用
有限状态机在很多不同领域被广泛应用，包括**电子工程、语言学、计算机科学、哲学、生物学、数学和逻辑学。** 在计算机科学中，有限状态机被广泛用于**建模 、 硬件电路系统设计 、 软件工程 ，编译器 、 网络协议 、和 计算与语言**的研究。
## 4. 状态机对电控程序的帮助
如果输出函数依赖于状态和输入()，则定义的是mealy状态机；如果输出函数仅仅依赖于状态()，那么定义的是moore状态机。如果，有限状态机没有输出函数这一项，那么可以称作transition system(转移系统) 。很多应用程序用到的有限状态机并没有输出序列，仅仅用到了状态机的转移过程和动作，其实可以称为转移系统。
### 4.1 为我所用的东西
 - **状态**  
 - **状态转移函数**    

*首先自定义系统状态，接着编写触发事件和状态转移函数（动作+变换）*  
下面是云台状态简单的有向图展示  
![](https://github.com/sos-xiaobai/A-First-Course-in-Optimization-Theory/blob/main/images/graph.png?raw=true)

## 5. 伪代码实现
    class FiniteStateMachine:
        def __init__(self):
            # 初始状态为停火状态
            self.current_state = '停火'
            # 初始状态标志位
            self.fire_flag = False
            # 初始状态卡弹标志位
            self.jam_flag = True

        def transition_to_fire(self):
            # 从停火状态转移到开机状态的条件是停火标志位为True
            if self.fire_flag:
                self.current_state = '开机'
                print("从停火状态转到开机状态")
            else:
                print("停火标志位未触发，无法转到开机状态")

        def transition_to_jam(self):
            # 从停火状态转移到卡弹状态的条件是检测到卡弹
            if self.jam_flag:
                self.current_state = '卡弹'
                print("从停火状态转到卡弹状态")
            else:
                print("未检测到卡弹，无法转到卡弹状态")

        def transition_to_fire_from_jam(self):
            # 从卡弹状态转移到开机状态的条件是不卡弹
            if not self.jam_flag:
                self.current_state = '开机'
                print("从卡弹状态转到开机状态")
            else:
                print("仍然卡弹，无法转到开机状态")

        //创建有限自动机实例
        fsm = FiniteStateMachine()

        //模拟状态转移
        fsm.transition_to_fire()  # 停火状态转到开机状态（条件满足）
        fsm.transition_to_jam()   # 无法从开机状态转到卡弹状态（条件不满足）
        fsm.transition_to_fire_from_jam()  # 无法从卡弹状态转到开机状态（条件不满足）

        //更新标志位
        fsm.jam_flag = False
        
        //再次模拟状态转移
        fsm.transition_to_fire_from_jam()  # 从卡弹状态转到开机状态（条件满足）
## 6. 参考资料  
[1][ 状态机：史上最棒的机制][1]  
[2][ 什么是状态机？][2]  
[3][ 编程——有限自动机][3]  
[4][ 有限自动机][4]

 
[1]:https://zhuanlan.zhihu.com/p/47434856
[2]:https://zhuanlan.zhihu.com/p/34639172
[3]:https://zhuanlan.zhihu.com/p/651128045
[4]:https://zhuanlan.zhihu.com/p/58738364