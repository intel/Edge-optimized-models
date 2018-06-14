# 5-Class Object detector

Detects and locates multiple instances of objects belonging to different classes. Trained to detect the following classes:

1. Bicycle
2. Bus
3. Car
4. Motorbike
5. Person

Utilizes an optimized version of [Squeezenet v1.0](https://github.com/DeepScale/SqueezeNet) [1] topology and [SSD](https://github.com/weiliu89/caffe/tree/ssd) [2] topology to achieve high throughput. This topology is optimized to yield high performance on Intel&reg; CPU, GPU, FPGA and Neural Compute Stick hardware platforms.

## Input
Blob with RGB image of 224x224 pixels resolution in format [B,C,H,W] format where B - batch size, C - number of color channels, H - image height fixed at 224 pixels and W - image width fixed at 224 pixels.

## Ouput
Blob of the shape [1,1,N,7] where N is the number of detected boxes and last dimension is a 7 field description in the format [image_id, label, conf, x_min, y_min, x_max, y_max] where:-

* image_id: the order of the image in the batch
* label: the id of the predictor class (1: Bicycle, 2: Bus, 3: Car, 4: Motorbike, 5: Person)
* conf: confidence of the predicted class
* (x_min, y_min): normalized co-ordinates of the top-left of the box
* (x_max, y_max): normalized co-ordinates of the bottom-right of the box

## SDK support
This model is supported by [Intel&reg; OpenVINO&trade; Toolkit ](https://software.seek.intel.com/openvino-toolkit) for deployment on Intel hardware platforms. Refer to Intel&reg; OpenVINO&trade; Toolkit documentation for usage details.

## References & Citations:
* [1] Forrest N. Iandola and Song Han and Matthew W. Moskewicz and Khalid Ashraf and William J. Dally and Kurt Keutzer, SqueezeNet: AlexNet-level accuracy with 50x fewer parameters and $<$0.5MB model size, arXiv:1602.07360, 2016

* [2] Liu, Wei and Anguelov, Dragomir and Erhan, Dumitru and Szegedy, Christian and Reed, Scott and Fu, Cheng-Yang and Berg, Alexander C.,  SSD: Single Shot MultiBox Detector}, ECCV, 2016
