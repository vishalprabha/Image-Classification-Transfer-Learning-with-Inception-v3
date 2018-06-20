

## Transfer learning using Tensorflow on Inception-V3 model

#### Overview:

The image recognition model called Inception-v3 consists of two parts:

  - Feature extraction part with a convolutional neural network.
  - Classification part with fully-connected and softmax layers.

In transfer learning, when you build a new model to classify your original dataset, you reuse the feature extraction part and
re-train the classification part with your dataset. Since you don't have to train the feature extraction part
(which is the most complex part of the model), you can train the model with less computational resources and training time.

#### Getting started

First we need to download the model from TensorFlow Repository, so run the below command :
`$python classify.py`

This will download the model if it doesn't exist already and will test the downloaded model with a Panda image and will print_function

```
giant panda, panda, panda bear, coon bear, Ailuropoda melanoleuca (score = 0.88493)
indri, indris, Indri indri, Indri brevicaudatus (score = 0.00878)
lesser panda, red panda, panda, bear cat, cat bear, Ailurus fulgens (score = 0.00317)
custard apple (score = 0.00149)
earthstar (score = 0.00127)
```

To test the above model run :
`python classify.py --image_file <filename>.png`


#### Transfer learning

>If your tensorflow is not up-to-date use the following command to update.

`$pip install --upgrade tensorflow`

We will train the Inception-V3 model with our own set of images present in tf_files folder.

The folder flower_photos contains the images of 5 types of flowers:
  1. daisy  
  2. dandelion
  3. roses
  4. sunflower
  5. tulips

Execute the following command in your terminal to retrain the model

`
$ python retrain.py --output_graph=tf_files/retrained_graph.pb --output_labels=tf_files/retrained_labels.txt --image_dir=tf_files/flower_photos
`
>it will start training and complete around 4000 steps

Test the retrained model with the images :
  1. dan.jpeg
  2. sun.jpeg
  with the following command :

`$ python label.py --image dan.jpeg`

```
Evaluation time (1-image): 1.387s

dandelion (score=0.99877)
daisy (score=0.00097)
tulips (score=0.00018)
sunflowers (score=0.00007)
roses (score=0.00001)
```

`$ python label.py --image sun.jpeg`

```
Evaluation time (1-image): 1.231s

sunflowers (score=0.93991)
dandelion (score=0.03731)
daisy (score=0.01330)
tulips (score=0.00671)
roses (score=0.00277)
```
