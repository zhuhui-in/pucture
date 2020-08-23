## 安装conda

mkdir miniconda3

cd miniconda3

wget -c https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh

```bash
chmod 777 Miniconda3-latest-Linux-x86_64.sh #给执行权限
bash Miniconda3-latest-Linux-x86_64.sh #运行
```

此时命令行前面出现（base）说明**默认**进入了conda的基础环境

vim ~/.bashrc

最后添加

conda deactivate

## 创建conda环境

conda create -n torchani python=3.8.5

conda info --env

pip list ##查看已经安装好的包

pip install numpy

## 安装pytorch

https://pytorch.org/  根据有无cuda等选择合适的版本

cuda-gdb##查看cuda版本

hzhu02@z55 k210 cuda 9.2

https://github.com/zhuhui-in/pucture/blob/master/image-20200818090633262.png![图片3](README.assets/%E5%9B%BE%E7%89%873.png)

## 安装torchani

pip install torchani

## test example

python torchani/example/vibration_analysis.py 

缺什么模块 就pip 安装

## 代码修改

tools目录下面有一个默认的comp6.py的脚本，其中line22:ani1x = torchani.models.ANI1x().to(parser.device)

说明可以直接用这个程序测试COMP6在ANI1X上的performance.

如果需要测试COMP6在其它模型上performance，只需要将comp6.py 第22行改为：

ani1x = torchani.models.ANI1ccx().to(parser.device)

或者

ani1x = torchani.models.ANI12x().to(parser.device)

即可运行不同模型的COMP6结果



## 代码运行

conda activate torchani #进入指定conda环境

运行comp6测试集综合结果：

python comp6.py comp6路径 > intergrate.txt

分别运行comp6测试集中单个文件的结果

python comp6.py comp6/GDB10-13 > GDB10-13.txt

或者批量执行

ls comp6 | while read id; do(nohup python comp6/$id 1>$id.txt 2>stderr.txt & );done



