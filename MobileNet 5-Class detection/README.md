# 5-Class Object detector

Detects and locates multiple instances of objects belonging to different classes in an input image with low latency. Trained to detect the following classes:

1. Bicycle
2. Bus
3. Car
4. Motorbike
5. Person

Utilizes an optimized version of MobileNet [1] topology and [SSD](https://github.com/weiliu89/caffe/tree/ssd) [2] topology to achieve high throughput. 

## Input
Blob with RGB image of 224x224 pixels resolution in format [B,C,H,W] format where B - batch size, C - number of color channels, H - image height fixed at 224 pixels and W - image width fixed at 224 pixels.

The image pixels from all channels must be mean-subtracted and scaled before input using the below formula:-

    new_pixel_value = (original_pixel_value - 127.5)*0.007843

## Ouput
Blob of the shape [1,1,N,7] where N is the number of detected boxes and last dimension is a 7 field description in the format [image_id, label, conf, x_min, y_min, x_max, y_max] where:-

* image_id: the order of the image in the batch
* label: the id of the predictor class (1: Bicycle, 2: Bus, 3: Car, 4: Motorbike, 5: Person)
* conf: confidence of the predicted class
* (x_min, y_min): normalized co-ordinates of the top-left of the box
* (x_max, y_max): normalized co-ordinates of the bottom-right of the box


## References & Citations:
* [1] Howard, Andrew G. and Zhu, Menglong and Chen, Bo and Kalenichenko, Dmitry and Wang, Weijun and Weyand, Tobias and Andreetto, Marco and Adam, Hartwig, MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications,  	arXiv:1704.04861, 2017

* [2] Liu, Wei and Anguelov, Dragomir and Erhan, Dumitru and Szegedy, Christian and Reed, Scott and Fu, Cheng-Yang and Berg, Alexander C.,  SSD: Single Shot MultiBox Detector, ECCV, 2016
