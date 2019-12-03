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

# Define the model
from keras.layers import Activation, Flatten, Dense, Dropout, SeparableConv2D, GlobalAveragePooling2D

# Define the model
model = Sequential()

model.add(SeparableConv2D(32, 3, 3, border_mode='same', input_shape=(32, 32, 3), use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(SeparableConv2D(64, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.11))


model.add(SeparableConv2D(128, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(SeparableConv2D(128, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.15))


model.add(SeparableConv2D(128, 3, 3, border_mode='same', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(Activation('relu'))
model.add(MaxPooling2D(pool_size=(2, 2)))
model.add(Dropout(0.22))

model.add(SeparableConv2D(128, 1, 1, activation='relu', use_bias = False, kernel_initializer='he_uniform'))
model.add(BatchNormalization())
model.add(SeparableConv2D(20, 4, use_bias = False))
model.add(GlobalAveragePooling2D())
model.add(Activation('softmax'))





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
