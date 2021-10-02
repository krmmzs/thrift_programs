# 食用文档
首先进行clone

---

## 首先配置thrift
详细见[]()

---

## 部署
本项目match_server和save_client是在一台服务器上的, 所以以下编译和链接的内容是以在一台服务器上使用的, 如果要使用不同的服务器, 原理是差不多的, game是在第二台服务器,save_server在第三台服务器上, 这个本项目没有提供, 由你自己使用数据库保证使用thrift的接口即可

---

## 实现业务和修改服务器ip
需要修改的文件是main.cpp和client.py

---

### client.py:
transport = TSocket.TSocket('localhost', 9090)

在# Specific business code233下实现逻辑

---

### main.cpp

std::shared_ptr<TTransport> socket(new TSocket("123.57.47.211", 9090)); // Fill in the IPadress you need

其他自行修改即可

---

## 编译链接
其中py源代码是直接用python3就可以解释了

c++的源代码需要编译

执行`g++ -c main.cpp match_server/*.cpp save_client/*.cpp`
主文件是`main.cpp`, 需要用到`match_server`和`save_client`中的各种`cpp`, 其中`.h`文件不需要编译

编译完后会在执行该命令的目录下产生6个`.o`文件

再执行`g++ *.o -o main -lthrift -pthread`

## 运行
在match-server端`./main`运行程序实现对game端的监听和处理数据存储

在game端`python3 client.py`运行程序实现游戏指令发送

---

**joy the joy of the program~~~**
