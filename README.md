# 实验名称
sm3长度扩展攻击

# 实验过程
长度扩展攻击的图解如下

![Screenshot 2022-07-31 054733](https://user-images.githubusercontent.com/104854836/181997181-e0ec000e-8cfd-4275-9564-2c3487ada9e7.jpg)

步骤如下：

1.首先得到消息M的hash值H_M和长度L后，先对消息进行为填充，得到M2=M||000...000||L

2.将H_M作为IV向量

3.选择任意消息m，对m进行填充，但是消息长度改为m的长度加上M2的长度

4.对m进行hash

# 实验结果
首先我加密的信息为"abc", bit长度为24，得到的hash为：

H=66 C7 F0 F4 62 EE ED D9 D1 F2 D4 6B DC 10 E4 E2 41 67 C4 87 5C F2 F7 A2 29 7D A0 2B 8F 4B A8 E0

然后我们对abc进行扩展为 M=abc||000...000||0x18||abc

对M进行hash后得到的hash为：

AC CF 73 FF C1 4F 32 53 5D 88 14 37 7C F8 CA D2 23 8C 90 5F BD B5 05 28 03 6F 5B EF 72 05 26 39

对H和3进行长度扩展攻击，将iv设置为H并且将abc的长度设置为0x218，得到的hash为：

AC CF 73 FF C1 4F 32 53 5D 88 14 37 7C F8 CA D2 23 8C 90 5F BD B5 05 28 03 6F 5B EF 72 05 26 39

![Screenshot 2022-07-31 060519](https://user-images.githubusercontent.com/104854836/182001727-1ac22969-f741-47f6-a896-b7f2f77a8f91.jpg)

