![Darknet Logo](http://pjreddie.com/media/files/darknet-black-small.png)

#Darknet#
Darknet is an open source neural network framework written in C and CUDA. It is fast, easy to install, and supports CPU and GPU computation.

For more information see the [Darknet project website](http://pjreddie.com/darknet).

For questions or issues please use the [Google Group](https://groups.google.com/forum/#!forum/darknet).


#############################
# Late Lee #
环境：
物理机ubuntu 16.04 64bit，显卡GTX1070(算力6.1)
## 编译过程：
1、安装cuda、cudnn
2、安装opencv
3、修改Makefile
GPU=1
CUDNN=1
OPENCV=1
OPENMP=1

根据实际情况添加显示的gencode：
      -gencode arch=compute_52,code=[sm_52,compute_52] \
	  -gencode arch=compute_60,code=sm_60 \
	  -gencode arch=compute_61,code=sm_61 \
	  -gencode arch=compute_61,code=compute_61

导出opencv的路径：
$ export PKG_CONFIG_PATH=/opt/dp/opencv_3.2.0_x64/lib/pkgconfig/:$PKG_CONFIG_PATH
(注：因为我安装的opencv不在/usr目录)

编译：
$ make -j4
之后在当前目录生成darknet文件。

## 测试过程
1、先下载作者预训练的文件yolo.weights：https://pjreddie.com/media/files/yolo.weights
2、运行程序：
./darknet detect cfg/yolo.cfg yolo.weights data/dog.jpg

即可在当前目录下看到predictions.jpg文件。如果不是在图形界面运行，则无法显示图片（会提示错误，但不影响效果）
手动指定输出图片文件示例：
./darknet detect cfg/yolo.cfg yolo.weights testimg/pic3.jpg -out testimg/pic3_p.jpg

=============================================================

log：
2017-8-24
批处理目录所有图片，将结果保存成result目录。另外将框出来的车辆保存到result_car目录。


