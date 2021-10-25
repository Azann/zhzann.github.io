# Windows下安装pycocotools
pip install pycocotools-windows
  
以前使用上述命令可以直接在windows下安装成功，现在试已经不行了
## 解决方法
1.安装Cython

2.下载支持windows的改写版pycocotools
支持windows的改写版本的Github项目地址：https://github.com/philferriere/cocoapi

3.修改cocoeval.py文件
  对比原始文件，507、508、517、518行分别少了int()操作
  
4.cd进PythonAPI文件夹内，运行
  python setup.py build_ext install
进行安装

出现错误：
  error:Unable to find vcvarsall.bat 
需要下载visual c++ build tools

下载地址：
  http://go.microsoft.com/fwlink/?LinkId=691126
  
参考：
  https://www.cnblogs.com/wildgoose/p/12905200.html
  
  https://blog.csdn.net/benzhujie1245com/article/details/82686973
  
  https://blog.csdn.net/qq_34289157/article/details/89952092
  
  # 也可能是由于开了代理的原因 #

# 安装opencv-python
  pip install opencv-python  -i https://pypi.tuna.tsinghua.edu.cn/simple
  使用清华镜像成功安装
