# deep_learning_on_tif

#Experimented on various combinations of bands,
RGB alone didn't worked well.
Band which is showing infrared information will just add noise.
RGB with RED_edge 3 band performed well with 95% Train accuracy and 93% val accuracy with loss around 1.3%

All 3 bands stacked on 3rd axis.
tif images were extracted using gdal library
and getRasterBand used to extract the values of the band and array constructed.

Data set is normalized using subtracting dataset by mean and dividing by standard deviation

Dataset is shuffled and divided into train and test data with 70:30 ratio.

Used Keras library:
Few Key points observed while training.

1. Started with one convolution layer and one maximum pooling layer, at last densily connected network with softmax function in the end.

2. Observed the model behaviour while training it upto 10 epochs.

3. When accracy of training becoming stable at low levels, then increased the layers,. also with increased in more pairs of xonv and maxpool, batch normalization was also added after each convolution layer.

4. Model was expected to show overfitting problem, therefore, batch normalization used. But, this process was not helpful, it was making the test accuracy to fluctuate heavily after every 5-6 epochs.

Note: Sometimes people ask to add batch normalization if model is behaving as mentioned, but removing the batch normalization decreased these fluctuations.

5. After epoch of 50, model accraucy got stable at 90% and test accuracy at 91%, there added l2 regularization and dropout layers in dense network.

6. Issue of overfitting problem as mentioned above solved, then comes to improve accuracy of model, bias added to convolution layers, which improved the test and train accuracy by 93% and 95%, more improvement is expected with epochs=150.

7. optimizer used is adam and minimum square error as loss function. 

Note, if your accuracy is moving around the a figure and showing less improvement, try decreasing learning rate, here, learning rate tested started from 0.1 to 0.0001. 
