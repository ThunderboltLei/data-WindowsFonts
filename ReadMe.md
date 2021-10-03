1、下载字体simhei.ttf，并放在该目录下
SimHei.ttf 在百度网盘里

/anaconda3/lib/python3.6/site-packages/matplotlib/mpl-data/fonts/ttf
目录查看：
import matplotlib
matplotlib.matplotlib_fname()
>>> .../site-packages/matplotlib/mpl-data/matplotlibrc （配置文件）

2、删除缓存字体
rm -rf ~/.matplotlib/*.cache

3、复制文件
（1）找到matplotlib字体文件夹，例如：/opt/developments/anaconda/anaconda3/lib/python3.7/matplotlib/mpl-data/fonts/ttf/，将SimHei.ttf拷贝到ttf
（2）再复制到/Library/Fonts/

4、修改配置文件matplotlibrc 同样在matplotlib/mpl-data/fonts目录下面，修改下面三项配置
font.family : sans-serif
font.sans-serif : SimHei, Bitstream Vera Sans, Lucida Grande, Verdana, Geneva, Lucid, Arial, Helvetica, Avant Garde, sans-serif
axes.unicode_minus:False，#作用就是解决负号'-'显示为方块的问题
假如你只做到了这里，那要小心喽，代码里面还是会报错，画图还是会显示方块，就问你气不气。。。。

5、最重要的一步来了，上面的几步我很快就弄好了，就这最后一步死活中文就是显示方块，气死我了，原因是改了配置之后并不会生效，需要重新加载字体，在Python中运行如下代码即可：
from matplotlib.font_manager import _rebuild
_rebuild()     #reload一下
