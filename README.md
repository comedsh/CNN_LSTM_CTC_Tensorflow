# CNN_LSTM_CTC_Tensorflow

CNN+LSTM+CTC based OCR(Optical Character Recognition) implemented in tensorflow. 

I use the code in this repository and get 99.75% accuracy on test dataset(200k images) in the [competition](http://meizu.baiducloud.top).


## Structure

The image is first processed by a CNN to extract features, then these features is feed into a LSTM.

The CNN is just 'Convolution + Convolution + Max pooling' for simplicity, and the LSTM is a 2 layer stacked LSTM, you can try out Bidirectional LSTM.

You can play with the network architecture and see what will happen. Have a look at [CNN part](https://github.com/watsonyanghx/CNN_LSTM_CTC_Tensorflow/blob/master/cnn_lstm_otc_ocr.py#L32) and [LSTM part](https://github.com/watsonyanghx/CNN_LSTM_CTC_Tensorflow/blob/master/cnn_lstm_otc_ocr.py#L57).


## Prerequisite

1. TensorFlow 1.2

2. Opecv3 (Not a must, used to read images.)

3. Numpy


## How to run

There are many other parameters with which you can play with, have a look at [utils.py](https://github.com/watsonyanghx/CNN_LSTM_CTC_Tensorflow/blob/master/utils.py#L11).

**Note** that the [num_classes](https://github.com/watsonyanghx/CNN_LSTM_CTC_Tensorflow/blob/master/utils.py#L6) is not added to parameters talked above for clarification.


``` shell
# Train the model.
python ./main.py --train_dir=./imgs/train/ \
                 --val_dir=./imgs/val/ \
                 --image_height=60 \
                 --image_width=180 \
                 --image_channel=1 \
                 --max_stepsize=64 \
                 --num_hidden=128 \
                 --log_dir=./log/train \
                 --num_gpus=0 \
                 --mode=train

# Inference
python ./main.py --infer_dir=./imgs/infer/ \
                 --checkpoint_dir=./checkpoint/ \
                 --num_gpus=0 \
                 --mode=infer

```


## Run with your own data.

1. prepare your data so that it is named in format: id_label.jpg

``` shell

python helper.py
```

2. Run following [How to run](https://github.com/watsonyanghx/CNN_LSTM_CTC_Tensorflow/edit/master/README.md#24)

