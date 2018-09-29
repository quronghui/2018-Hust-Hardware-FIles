# 电容和电感作用
## 1、电容作用
1. 电容的购买，需要这个类型C0G (NPO填充介质)；NPO电容器是电容量和介质损耗最稳定的电容器.
### 1.1 电容功能
1. 旁路：为尽量减少阻抗，旁路电容要尽量靠近负载器件的供电电源管脚和地管脚。 这能够很好地防止输入值过大而导致的地电位抬高和噪声。地电位是地连接处在通过大电流毛刺时的电压降。根据谐振频率一般取0.1μF、0.01μF。
2. 去耦：去耦合电容的容量一般较大，可能是10μF 或者更大。
3. **旁路：把输入信号中的干扰作为滤除对象；去耦：输出信号的干扰作为滤除对象，防止干扰信号返回电源。**
4. 电容隔直流通交流：串联——在一定信号频率下是隔直流通交流；并联于电源——大电容是作为存储能量的，小电容是滤波用的；并联于信号——则是滤波。
5. 滤波：具体用在滤波中,大电容（1000μF）滤低频（通低频），小电容（20pF）滤高频（通高频

### 1.2 接地
1. 模拟地和数字地相连：电源地上的大电容_VBUS，以这个电容的地为交汇点，数字地和模拟地接到这个电容的地的这个脚上。
2. 对于地的分开，主要是从布线的角度看的，减少不同电路之间地的干扰，而电源的地不能看成模拟地，信号地也不能看成数字地。
3. [数字地和模拟地](https://blog.csdn.net/Dwylin/article/details/39525511)
## 2.电路设计相关知识
### 2.1 电源噪声
- 减少阻抗
+ 提供一个完整的电源平面和地平面，稳压电源输出首先接入电源平面，供电电流流经电源平面，到达负载电源引脚。
### 2.2 尖峰电流的抑制方法
+ 电源入口处：一个1uF～10uF的去耦电容，滤除低频噪声
+ 电路板内：每一个有源器件的电源和地之间放置一个0.01uF～0.1uF的去耦电容，用于滤除高频噪声
+ 去耦电容的选取可按C=1/F计算
### 2.3 静电防护
+ CMOS器件在使用时应注意防静电。其一是输入引脚不能悬空。输入引脚与电源或地之间接入一个负载电阻（1～10KΩ）
### 2.4 [模拟电源和数字电源的分开](https://blog.csdn.net/gtkknd/article/details/39493923)
+ AVDD: 采用电感（形成高阻抗，降低电源中的噪声）+ 1R电阻进行
- 除每个电源管脚的一个电容外; 两个域因该有一个大电容--10uF左右;
- 数组域：C=100nF; 模拟域：C=10nF
## 3. 电感
### 3.1 [电感和磁珠](http://bbs.elecfans.com/jishu_303284_1_1.html)
|类别|区别/用途|类别|区别/用途|
|:-:|:-:|:-:|:-:|
|磁珠|主要用于高频隔离，抑制差模噪声等|电感|是储能组件，而磁珠是能量转换（消耗）器件
||多用于信号回路||电源滤波回路|
||EMC-->主要用于抑制电磁辐射干扰||EMC-->侧重于抑制传导性干扰|
||吸收超高频信号，一些RF电路，PLL--回路，振荡电路，含超高频存储器电路（DDR SDRAM，RAMBUS等）都需要在电源输入部分加磁珠||一种蓄能组件，用在LC振荡电路，中低频的滤波电路等，其应用频率范围很少超过50MHZ|
||地的连接一般用电感，电源的连接也用电感||对信号线则采用磁珠
|叠层电感|散热性更好，ESR值更小。但耐电流较绕线小|绕线|ESR值更高，但耐电流会更大
## 4/[张飞实战电子](http://mp.sohu.com/profile?xpt=ZmNzZGUtc2hAc29odS5jb20=&_f=index_pagemp_2)
+ 搜狐的账号：13638698124--quronghui,7