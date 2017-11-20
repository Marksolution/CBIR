![MIT](https://badges.frapsoft.com/os/mit/mit.svg?v=102)

# CBIR 
__This repo implements a CBIR (content-based image retrieval) system__
<img align='center' style="border-color:gray;border-width:2px;border-style:dashed"   src='https://github.com/brianhuang1019/CBIR/blob/img/CBIR.png' padding='5px' height="400px"></img>
<a href='https://winstonhsu.info/2017f-mmai/'>Image src</a>


## Part1: feature extraction

Implement several popular image features:
- color-based
  - [RGB histogram](https://github.com/brianhuang1019/CBIR/blob/master/src/color.py)
- texture-based
  - [gabor filter](https://github.com/brianhuang1019/CBIR/blob/master/src/gabor.py)
- shape-based
  - [daisy](https://github.com/brianhuang1019/CBIR/blob/master/src/daisy.py)
  - [edge histogram](https://github.com/brianhuang1019/CBIR/blob/master/src/edge.py)
  - [HOG (histogram of gradient)](https://github.com/brianhuang1019/CBIR/blob/master/src/HOG.py)
- deep methods
  - [VGG net](https://github.com/brianhuang1019/CBIR/blob/master/src/vggnet.py)
  - [Residual net](https://github.com/brianhuang1019/CBIR/blob/master/src/resnet.py)

##### *all features are modulized*

### Feature Fusion
Some features are not robust enough, and turn to feature fusion
- [fusion.py](https://github.com/brianhuang1019/CBIR/blob/master/src/fusion.py)

### Dimension Reduction
The curse of dimensionality told that vectors in high dimension will sometime lose distance property
- [Random Projection](https://github.com/brianhuang1019/CBIR/blob/master/src/random_projection.py)


## Part2: evaluation

CBIR system retrieval k images based on features similarity (L1 distance)

Robustness of system is evaluated by MMAP (mean MAP)

- image AP   : mean of precision at each hit
- class1 MAP = (class1.img[0].AP + class1.img[1].AP + ... + class1.img[M].AP) / M
- MMAP       = (class1.MAP + class2.MAP + ... + classN.MAP) / N

<img align='center' style="border-color:gray;border-width:2px;border-style:dashed"   src='https://github.com/brianhuang1019/CBIR/blob/img/AP.png' padding='5px' height="380px"></img>
<a href='http://web.stanford.edu/class/cs276/handouts/EvaluationNew-handout-1-per.pdf'>Image src</a>

<img align='center' style="border-color:gray;border-width:2px;border-style:dashed"   src='https://github.com/brianhuang1019/CBIR/blob/img/MAP.png' padding='5px' height="380px"></img>
<a href='http://web.stanford.edu/class/cs276/handouts/EvaluationNew-handout-1-per.pdf'>Image src</a>

my database contains 25 classes, each class with 20 images

Method | color | daisy | edge | gabor | HOG | vgg19 | resnet152
--- | --- | --- | --- |--- |--- |--- |---
Mean MAP (depth=10) | 0.614 | 0.468 | 0.301 | 0.346 | 0.450 | 0.914 | 0.944

implementation of this part can found at [evaluate.py](https://github.com/brianhuang1019/CBIR/blob/master/src/evaluate.py)


## Part3: image retrieval
### query1 - women dress
#### query <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1.jpg' padding='5px' height="80px"></img>
#### color <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-color.jpg' padding='5px' height="80px"></img>
#### daisy <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-daisy.jpg' padding='5px' height="80px"></img>
#### edge <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-edge.jpg' padding='5px' height="80px"></img>
#### gabor <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-gabor.jpg' padding='5px' height="80px"></img>
#### HOG <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-hog.jpg' padding='5px' height="80px"></img>
#### VGG19 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-vgg.jpg' padding='5px' height="80px"></img>
#### Resnet152 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query1-women_dress/query1-res.jpg' padding='5px' height="80px"></img>

### query2 - orange
#### query <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2.jpg' padding='5px' height="80px"></img>
#### color <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-color.jpg' padding='5px' height="80px"></img>
#### daisy <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-daisy.jpg' padding='5px' height="80px"></img>
#### edge <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-edge.jpg' padding='5px' height="80px"></img>
#### gabor <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-gabor.jpg' padding='5px' height="80px"></img>
#### HOG <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-hog.jpg' padding='5px' height="80px"></img>
#### VGG19 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-vgg.jpg' padding='5px' height="80px"></img>
#### Resnet152 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query2-orange/query2-res.jpg' padding='5px' height="80px"></img>

### query3 - NBA jersey
#### query <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3.jpg' padding='5px' height="80px"></img>
#### color <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-color.jpg' padding='5px' height="80px"></img>
#### daisy <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-daisy.jpg' padding='5px' height="80px"></img>
#### edge <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-edge.jpg' padding='5px' height="80px"></img>
#### gabor <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-gabor.jpg' padding='5px' height="80px"></img>
#### HOG <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-hog.jpg' padding='5px' height="80px"></img>
#### VGG19 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-vgg.jpg' padding='5px' height="80px"></img>
#### Resnet152 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query3-nba_jersey/query3-res.jpg' padding='5px' height="80px"></img>

### query4 - snack
#### query <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4.jpg' padding='5px' height="80px"></img>
#### color <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-color.jpg' padding='5px' height="80px"></img>
#### daisy <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-daisy.jpg' padding='5px' height="80px"></img>
#### edge <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-edge.jpg' padding='5px' height="80px"></img>
#### gabor <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-gabor.jpg' padding='5px' height="80px"></img>
#### HOG <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-hog.jpg' padding='5px' height="80px"></img>
#### VGG19 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-vgg.jpg' padding='5px' height="80px"></img>
#### Resnet152 <img align='center' style="border-color:gray;border-width:2px;border-style:dashed" src='retrieval_result/query4-snack/query4-res.jpg' padding='5px' height="80px"></img>
