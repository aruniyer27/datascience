# EIP4 Assignment 3
## Base Network Accuracy # 83.11

Epoch 40/50
390/390 [==============================] - 20s 52ms/step - loss: 0.3506 - acc: 0.8801 - val_loss: 0.5739 - val_acc: 0.8222

Epoch 41/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3482 - acc: 0.8820 - val_loss: 0.5654 - val_acc: 0.8243

Epoch 42/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3455 - acc: 0.8828 - val_loss: 0.5918 - val_acc: 0.8274

Epoch 43/50
390/390 [==============================] - 20s 52ms/step - loss: 0.3554 - acc: 0.8817 - val_loss: 0.5635 - val_acc: 0.8278

Epoch 44/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3412 - acc: 0.8847 - val_loss: 0.5688 - val_acc: 0.8307

Epoch 45/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3407 - acc: 0.8880 - val_loss: 0.5710 - val_acc: 0.8288

Epoch 46/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3487 - acc: 0.8835 - val_loss: 0.5763 - val_acc: 0.8199

Epoch 47/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3373 - acc: 0.8866 - val_loss: 0.5765 - val_acc: 0.8185

Epoch 48/50
390/390 [==============================] - 20s 52ms/step - loss: 0.3295 - acc: 0.8904 - val_loss: 0.5747 - val_acc: 0.8267

Epoch 49/50
390/390 [==============================] - 20s 52ms/step - loss: 0.3325 - acc: 0.8885 - val_loss: 0.5942 - val_acc: 0.8244

Epoch 50/50
390/390 [==============================] - 20s 52ms/step - loss: 0.3359 - acc: 0.8900 - val_loss: 0.5675 - val_acc: 0.8311

Model took 1016.24 seconds to train

Accuracy on test data is: 83.11

## Model Definition
from keras.layers import Activation, Flatten, Dense, Dropout, SeparableConv2D, GlobalAveragePooling2D
from keras.optimizers import Adam

model = Sequential()

model.add(SeparableConv2D(32, 3, 3, border_mode='same', input_shape=(32, 32, 3), use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(SeparableConv2D(64, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.2))


model.add(SeparableConv2D(128, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(SeparableConv2D(178, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.2))


model.add(SeparableConv2D(178, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.22))

model.add(SeparableConv2D(168, 1, 1, activation='relu', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(SeparableConv2D(10, 4, use_bias = False))
model.add(GlobalAveragePooling2D())
model.add(Activation('softmax'))

model.summary()

model.compile(optimizer=Adam(lr=.005), loss='categorical_crossentropy', metrics=['accuracy'])

Total params: 105,891
Trainable params: 104,395
Non-trainable params: 1,496

## 50 Epochs Log - Highest Validation Accuracy - 83.71


Epoch 1/50
390/390 [==============================] - 24s 62ms/step - loss: 1.2640 - acc: 0.5443 - val_loss: 2.3102 - val_acc: 0.4742

Epoch 2/50
390/390 [==============================] - 20s 51ms/step - loss: 0.9054 - acc: 0.6808 - val_loss: 1.0242 - val_acc: 0.6582

Epoch 3/50
390/390 [==============================] - 20s 51ms/step - loss: 0.7884 - acc: 0.7231 - val_loss: 0.8278 - val_acc: 0.7202

Epoch 4/50
390/390 [==============================] - 20s 51ms/step - loss: 0.7085 - acc: 0.7531 - val_loss: 0.7204 - val_acc: 0.7575

Epoch 5/50
390/390 [==============================] - 20s 51ms/step - loss: 0.6568 - acc: 0.7701 - val_loss: 0.7528 - val_acc: 0.7523

Epoch 6/50
390/390 [==============================] - 20s 51ms/step - loss: 0.6164 - acc: 0.7838 - val_loss: 0.6730 - val_acc: 0.7711

Epoch 7/50
390/390 [==============================] - 20s 51ms/step - loss: 0.5801 - acc: 0.7972 - val_loss: 0.6738 - val_acc: 0.7693

Epoch 8/50
390/390 [==============================] - 20s 52ms/step - loss: 0.5524 - acc: 0.8057 - val_loss: 1.0115 - val_acc: 0.6761

Epoch 9/50
390/390 [==============================] - 20s 51ms/step - loss: 0.5401 - acc: 0.8101 - val_loss: 0.7248 - val_acc: 0.7588

Epoch 10/50
390/390 [==============================] - 20s 51ms/step - loss: 0.5153 - acc: 0.8188 - val_loss: 0.7831 - val_acc: 0.7555

Epoch 11/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4952 - acc: 0.8255 - val_loss: 0.5664 - val_acc: 0.8069

Epoch 12/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4789 - acc: 0.8336 - val_loss: 0.6866 - val_acc: 0.7795

Epoch 13/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4606 - acc: 0.8396 - val_loss: 0.6140 - val_acc: 0.7987

Epoch 14/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4528 - acc: 0.8411 - val_loss: 0.5841 - val_acc: 0.8101

Epoch 15/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4402 - acc: 0.8450 - val_loss: 0.6272 - val_acc: 0.7954

Epoch 16/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4279 - acc: 0.8482 - val_loss: 0.6092 - val_acc: 0.8061

Epoch 17/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4184 - acc: 0.8538 - val_loss: 0.6818 - val_acc: 0.7737

Epoch 18/50
390/390 [==============================] - 20s 51ms/step - loss: 0.4173 - acc: 0.8530 - val_loss: 0.5547 - val_acc: 0.8214

Epoch 19/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3956 - acc: 0.8601 - val_loss: 0.6615 - val_acc: 0.7888

Epoch 20/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3891 - acc: 0.8610 - val_loss: 0.6147 - val_acc: 0.8025

Epoch 21/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3843 - acc: 0.8632 - val_loss: 0.5897 - val_acc: 0.8098

Epoch 22/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3719 - acc: 0.8677 - val_loss: 0.5731 - val_acc: 0.8173

Epoch 23/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3721 - acc: 0.8684 - val_loss: 0.6000 - val_acc: 0.8114

Epoch 24/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3643 - acc: 0.8713 - val_loss: 0.5982 - val_acc: 0.8070

Epoch 25/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3579 - acc: 0.8724 - val_loss: 0.5590 - val_acc: 0.8250

Epoch 26/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3444 - acc: 0.8779 - val_loss: 0.5871 - val_acc: 0.8140

Epoch 27/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3480 - acc: 0.8754 - val_loss: 0.5767 - val_acc: 0.8139

Epoch 28/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3406 - acc: 0.8774 - val_loss: 0.5582 - val_acc: 0.8251

Epoch 29/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3324 - acc: 0.8812 - val_loss: 0.6969 - val_acc: 0.7928

Epoch 30/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3299 - acc: 0.8821 - val_loss: 0.5360 - val_acc: 0.8260

Epoch 31/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3284 - acc: 0.8823 - val_loss: 0.5815 - val_acc: 0.8217

Epoch 32/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3136 - acc: 0.8876 - val_loss: 0.5742 - val_acc: 0.8233

Epoch 33/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3158 - acc: 0.8870 - val_loss: 0.5816 - val_acc: 0.8216

Epoch 34/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3101 - acc: 0.8897 - val_loss: 0.8123 - val_acc: 0.7603

Epoch 35/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3102 - acc: 0.8900 - val_loss: 0.5687 - val_acc: 0.8224

Epoch 36/50
390/390 [==============================] - 20s 51ms/step - loss: 0.3015 - acc: 0.8921 - val_loss: 0.5750 - val_acc: 0.8236

Epoch 37/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2964 - acc: 0.8948 - val_loss: 0.5311 - val_acc: 0.8379

Epoch 38/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2940 - acc: 0.8953 - val_loss: 0.5587 - val_acc: 0.8275

Epoch 39/50
390/390 [==============================] - 20s 52ms/step - loss: 0.2958 - acc: 0.8926 - val_loss: 0.5653 - val_acc: 0.8323

Epoch 40/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2882 - acc: 0.8966 - val_loss: 0.5822 - val_acc: 0.8216

Epoch 41/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2920 - acc: 0.8945 - val_loss: 0.5393 - val_acc: 0.8353

Epoch 42/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2789 - acc: 0.8994 - val_loss: 0.5215 - val_acc: 0.8350

Epoch 43/50
390/390 [==============================] - 20s 52ms/step - loss: 0.2819 - acc: 0.9000 - val_loss: 0.5681 - val_acc: 0.8267

Epoch 44/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2781 - acc: 0.9004 - val_loss: 0.5311 - val_acc: 0.8371

Epoch 45/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2722 - acc: 0.9026 - val_loss: 0.7083 - val_acc: 0.7981

Epoch 46/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2742 - acc: 0.9017 - val_loss: 0.5668 - val_acc: 0.8346

Epoch 47/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2655 - acc: 0.9052 - val_loss: 0.6714 - val_acc: 0.8076

Epoch 48/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2692 - acc: 0.9043 - val_loss: 0.5950 - val_acc: 0.8348

Epoch 49/50
390/390 [==============================] - 20s 51ms/step - loss: 0.2697 - acc: 0.9033 - val_loss: 0.5658 - val_acc: 0.8316

Epoch 50/50
390/390 [==============================] - 20s 52ms/step - loss: 0.2559 - acc: 0.9066 - val_loss: 0.6046 - val_acc: 0.8263

Model took 1004.24 seconds to train

Accuracy on test data is: 82.63






# EIP4 Assignment 1
print(score)

[0.029554922466222478, 0.9923]

# EIP4 Assignment 2
Train on 60000 samples, validate on 10000 samples
Epoch 1/20

Epoch 00001: LearningRateScheduler setting learning rate to 0.003.
60000/60000 [==============================] - 12s 205us/step - loss: 0.5566 - acc: 0.8441 - val_loss: 0.0964 - val_acc: 0.9811
Epoch 2/20

Epoch 00002: LearningRateScheduler setting learning rate to 0.0022744503.
60000/60000 [==============================] - 10s 165us/step - loss: 0.2603 - acc: 0.9235 - val_loss: 0.0605 - val_acc: 0.9878
Epoch 3/20

Epoch 00003: LearningRateScheduler setting learning rate to 0.0018315018.
60000/60000 [==============================] - 10s 165us/step - loss: 0.2003 - acc: 0.9404 - val_loss: 0.0429 - val_acc: 0.9892
Epoch 4/20

Epoch 00004: LearningRateScheduler setting learning rate to 0.0015329586.
60000/60000 [==============================] - 10s 162us/step - loss: 0.1729 - acc: 0.9471 - val_loss: 0.0394 - val_acc: 0.9916
Epoch 5/20

Epoch 00005: LearningRateScheduler setting learning rate to 0.0013181019.
60000/60000 [==============================] - 10s 163us/step - loss: 0.1515 - acc: 0.9502 - val_loss: 0.0320 - val_acc: 0.9913
Epoch 6/20

Epoch 00006: LearningRateScheduler setting learning rate to 0.0011560694.
60000/60000 [==============================] - 10s 162us/step - loss: 0.1422 - acc: 0.9506 - val_loss: 0.0302 - val_acc: 0.9922
Epoch 7/20

Epoch 00007: LearningRateScheduler setting learning rate to 0.0010295127.
60000/60000 [==============================] - 10s 163us/step - loss: 0.1302 - acc: 0.9537 - val_loss: 0.0302 - val_acc: 0.9911
Epoch 8/20

Epoch 00008: LearningRateScheduler setting learning rate to 0.0009279307.
60000/60000 [==============================] - 10s 163us/step - loss: 0.1262 - acc: 0.9528 - val_loss: 0.0270 - val_acc: 0.9928
Epoch 9/20

Epoch 00009: LearningRateScheduler setting learning rate to 0.0008445946.
60000/60000 [==============================] - 10s 164us/step - loss: 0.1190 - acc: 0.9553 - val_loss: 0.0272 - val_acc: 0.9922
Epoch 10/20

Epoch 00010: LearningRateScheduler setting learning rate to 0.0007749935.
60000/60000 [==============================] - 10s 164us/step - loss: 0.1113 - acc: 0.9554 - val_loss: 0.0233 - val_acc: 0.9934
Epoch 11/20

Epoch 00011: LearningRateScheduler setting learning rate to 0.0007159905.
60000/60000 [==============================] - 10s 163us/step - loss: 0.1096 - acc: 0.9558 - val_loss: 0.0218 - val_acc: 0.9940
Epoch 12/20

Epoch 00012: LearningRateScheduler setting learning rate to 0.000665336.
60000/60000 [==============================] - 10s 163us/step - loss: 0.1058 - acc: 0.9563 - val_loss: 0.0253 - val_acc: 0.9929
Epoch 13/20

Epoch 00013: LearningRateScheduler setting learning rate to 0.0006213753.
60000/60000 [==============================] - 10s 163us/step - loss: 0.1030 - acc: 0.9565 - val_loss: 0.0222 - val_acc: 0.9932
Epoch 14/20

Epoch 00014: LearningRateScheduler setting learning rate to 0.0005828638.
60000/60000 [==============================] - 10s 162us/step - loss: 0.1009 - acc: 0.9564 - val_loss: 0.0217 - val_acc: 0.9941
Epoch 15/20

Epoch 00015: LearningRateScheduler setting learning rate to 0.0005488474.
60000/60000 [==============================] - 10s 165us/step - loss: 0.1000 - acc: 0.9560 - val_loss: 0.0209 - val_acc: 0.9948
Epoch 16/20

Epoch 00016: LearningRateScheduler setting learning rate to 0.0005185825.
60000/60000 [==============================] - 10s 162us/step - loss: 0.0964 - acc: 0.9581 - val_loss: 0.0213 - val_acc: 0.9941
Epoch 17/20

Epoch 00017: LearningRateScheduler setting learning rate to 0.000491481.
60000/60000 [==============================] - 10s 163us/step - loss: 0.0990 - acc: 0.9561 - val_loss: 0.0191 - val_acc: 0.9952
Epoch 18/20

Epoch 00018: LearningRateScheduler setting learning rate to 0.0004670715.
60000/60000 [==============================] - 10s 163us/step - loss: 0.0964 - acc: 0.9575 - val_loss: 0.0193 - val_acc: 0.9941
Epoch 19/20

Epoch 00019: LearningRateScheduler setting learning rate to 0.0004449718.
60000/60000 [==============================] - 10s 163us/step - loss: 0.0930 - acc: 0.9580 - val_loss: 0.0208 - val_acc: 0.9938
Epoch 20/20

Epoch 00020: LearningRateScheduler setting learning rate to 0.000424869.
60000/60000 [==============================] - 10s 163us/step - loss: 0.0921 - acc: 0.9577 - val_loss: 0.0198 - val_acc: 0.9947

<keras.callbacks.History at 0x7f4e25849390>

score = model.evaluate(X_test, Y_test, verbose=0)
print(score)
[0.01982875217284309, 0.9947]


## Strategy
Added dropout and batch normalization at every layer. Tried to optimize the learning rate, conu layer. Also set the bias to false on all convulutional layers
