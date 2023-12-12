# rotated_object_detection



1. Label Rotated Rect On Images: [**roLabelImg**](https://github.com/cgvict/roLabelImg); [Video](https://www.bilibili.com/video/av628207628/?vd_source=95214b5fabd854c278a19fd16812861c);
2. [Package the tool roLabelImg as exe file in the Win10](https://zhuanlan.zhihu.com/p/566654678);
3. [Transform annotations from rolabelImg style to DOTA](https://github.com/Luo-Z13/Annotations_Tool);
4. 







+ [yolov5_obb作者hukaixuan19970627的答复](https://github.com/hukaixuan19970627/yolov5_obb/issues/427#issuecomment-1210125531)：

```
其实ciou+角度分类是我“个人认为”的目前最好的旋转检测方案，我在yolov5上的实验是发现ciou+角度分类方案收敛速度起码要比RIoU Loss系列方案快个30%~50%的感觉，而且精度表现甚至和KLD、R-CIoU差不多，而且更关键的问题是RIoU 系列Loss实际上是比较难调的，我可能部分Loss权重没设置好，网络的精度就会一直上不去。

之所以毕业论文搞RIoU系列，是因为CSL DCL这些都是别人的东西
```

