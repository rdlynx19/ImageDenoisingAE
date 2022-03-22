# Image Denoising AutoEncoder

## Dataset
Model was trained on MNIST dataset containing <em>60000</em> training images and <em>10000</em> test images.
![](https://i.imgur.com/YOePi3w.png)


## Model Architecture
The model is a convolutional neural network (CNN) consisting of 6 layers.

<em>Conv2d(input_channels,output_channels,kernel_size,padding,stride)</em> <br>
<em>tConv2d(input_channels,output_channels,kernel_size,padding,stride,output-padding)</em> <br>

### Encoding Layers
    Layer 1: Conv2d(1,32,3,p=1,s=2)
    Layer 2: Conv2d(32,64,3,p=1,s=2) 
    Layer 3: Conv2d(64,128,5) 

### Decoding Layers
    Layer 4: tConv2d(128,64,5) 
    Layer 5: tConv2d(64,32,3,p=1,s=2,op=1) 
    Layer 6: tConv2d(32,1,3,p=1,s=2,op=1) 

## Loss Function and Optimization
Loss function used was Mean Squared Error. <br>
For optimization, Adam was used with a learning rate of 1e^-3. <br>
Loss plot for 10 epochs. <br>
![lossgraph](https://user-images.githubusercontent.com/78100512/136921243-5072d0f7-1fb3-486a-99c1-8adac55ce72e.png)


## Noise
Gaussian noise was added via torch.randn() with a tunable noise factor variable.<br>
```
def add_noise(inputs,noise_factor=0.3):  
  noisy = inputs + (torch.randn_like(inputs) * noise_factor)  
  noisy = torch.clip(noisy,0.,1.)  
  return noisy 
```  
   

## Result
![](https://i.imgur.com/3mYUerl.png)  

![](https://i.imgur.com/Ls7YK7T.png)  

![](https://i.imgur.com/euMZGeX.png)

This project was built as a part of IvLabs Summer Internship 2021. You can refer to the IvLabs repostiory [here](https://github.com/IvLabs/Summer-Projects/tree/main/Summer%202021/Image%20Denoising)



