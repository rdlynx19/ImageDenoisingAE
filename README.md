# Image Denoising AutoEncoder

## Dataset
Model was trained on MNIST dataset.
![](https://i.imgur.com/YOePi3w.png)


## Model Architecture
The model is a convolutional neural network (CNN) consisting of 6 layers.

Conv2d(input_channels,output_channels,kernel_size,padding,stride) <br>
tConv2d(input_channels,output_channels,kernel_size,padding,stride,output-padding) <br>

### Encoding Layers
Layer 1: Conv2d(1,32,3,p=1,s=2) <br>
Layer 2: Conv2d(32,64,3,p=1,s=2) <br>
Layer 3: Conv2d(64,128,5) <br>

### Decoding Layers
Layer 4: tConv2d(128,64,5) <br>
Layer 5: tConv2d(64,32,3,p=1,s=2,op=1) <br>
Layer 6: tConv2d(32,1,3,p=1,s=2,op=1) <br>

## Loss Function and Optimization
Loss function used was Mean Squared Error. <br>
For optimization, Adam was used with a learning rate of 1e^-3. <br>

## Noise
Gaussian noise was added via torch.randn() with a tunable noise factor variable.

## Result
![](https://i.imgur.com/3mYUerl.png)  

![](https://i.imgur.com/Ls7YK7T.png)  

![](https://i.imgur.com/euMZGeX.png)



