# fast-style-transfer-master-with-ckpt
fast-style-transfer-master with ckpt!!!
看看“后来人的解释.txt”吧，很重要的，反而里面的README是前辈留下来的，已经没有什么快速解决课设的意义了。
也可以参考b站视频的讲解：https://www.bilibili.com/video/BV1i64y1B72P?p=10&vd_source=a38677c765eaceef84e6779567e2f92e 的p10部分
但是买他的课就不必要了，毕竟他也只是跑了这个案例而已，而且ckpt6个模型也都找到了，居然想卖19块钱。。。

fast-style-transfer-master文件夹里面的重要文件
显然，能够看到这个“后来人的解释.txt"，当然还有前辈的解释：README.md。最重要的是：evaluate.py和ckpt文件夹，evaluate是我们要运行的文件，ckpt文件夹里面有6个ckpt后缀的文件，对应了6个风格模型，在最后运行的时候我们就可以进行不同风格的迁移。


重要流程：(注意，以下操作前，不要挂梯子！！）
1.下载并安装anaconda或者miniconda，为了后续的创建虚拟环境

2.windows搜索栏搜索anaconda prompt进入命令行

3.换源：其实就是不用外国的下载网址，我们换到清华源
在命令行里面输入：(直接CTRL CV就行)
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

4.搭建虚拟环境
命令行输入：
conda create -n s-t python=3.8    （这里的s-t其实就是自己命名的环境名字，然后规定了python版本为3.8，因为我在3.7尝试的时候总会出现某库与python版本不匹配，所以一气之下就选择了直接用3.8版本）（遇到Proceed（[y]/n）就输入y就行，只是在问询你是否确定下载并安装库而已）

activate s-t  （激活刚刚创建好的环境s-t)

pip install tensorflow moviepy   (安装tensorflow和moviepy，他会自动安装当前python合适的最高版本的tensorflow和moviepy）

conda install scipy pillow（同理，安装scipy和pillow，自动安装最适合版本）

5.运行evaluate.py文件
这里提供两种做法
5.1一就是继续刚刚的步骤后，
5.1.1 在命令行输入：
cd 。。。。。（这里的。。。。。就是你把这个fast-style-transfer-master文件夹放在了哪里的路径，
比如我的fast-style-transfer-master文件夹路径为C:\Users\vvvv\Desktop\fast-style-transfer-master
那么我就输入：cd C:\Users\vvvv\Desktop\fast-style-transfer-master ，意思是转到这个文件夹，再进行下一步操作

5.1.2接下来就可以输入：
python evaluate.py --checkpoint ckpt/xxxx.ckpt --in-path examples/content/yyyy.jpg --out-path output/zzzz.jpg
示例：python evaluate.py --checkpoint ckpt/la_muse.ckpt --in-path examples/content/stata.jpg --out-path output/sta.jpg
意思是：
通过python运行evaluate文件，
输入了参数checkpoint为ckpt文件夹下的la_muse.ckpt风格模型路径，
输入了--in-path参数为examples文件夹下的content文件夹下的state.jpg相片路径，
输入了--out-path参数为output文件夹下的zzzz.jpg路径（就是最终完成风格迁移后的文件保存路径）

正常的话就能在output文件夹看到结果啦


5.2法二，如果5.1的方法行不通，就可以尝试
在4的步骤完成后，在命令行输入：
jupyter notebook
这之后就会自动打开默认浏览器，到达jupyter notebook,
在该网站的偏右上的位置有New按钮，点击并选择Terminal，即命令行，他会自动创建新的页面进入命令行
在notebook的命令行里面，进行5.1.1的操作进入文件夹，然后再进行5.1.2的操作，

然后就应该能够正常进行风格迁移了。
