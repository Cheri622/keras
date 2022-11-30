# A comparison of accuracy of 4 pre-trained models

## Explanation:<br />  
### a series of optional experiments for a comparison of accuracy of 4 pre-trained models:  vgg16, ResNet50, EfficientNetB7 and InceptionV3, all based on dataset of Cat and Dog Images (kaggle).<br />I optionally adopted StratifiedKFold for learning improvement and adopted ReduceLROnPlateau to reduce learning rate when a metric has stopped improving. Models often benefit from reducing the learning rate by a factor of 2-10 once learning stagnates.<br />The other important callback is ModelCheckpoint which is used for storing the weights of the model after training. I save only the best weights of the model by specifying save_best_only=True.<br />It is an on-going project, needs further organization.


experiment data gathered are as following:
basic setting: vgg16 + ReduceLROnPlateau + optimizer=Adam + 10 epochs
Epoch 10
625/625 [==============================] - 974s 2s/step - loss: 0.2726 - accuracy: 0.8808 - val_loss: 0.2409 - val_accuracy: 0.8990

vgg16 load_model, fit again -> best result
Epoch 4/10
625/625 [==============================] - 1084s 2s/step - loss: 0.2741 - accuracy: 0.8787 - val_loss: 0.2292 - val_accuracy: 0.9010
Epoch 10/10
625/625 [==============================] - 1013s 2s/step - loss: 0.2580 - accuracy: 0.8874 - val_loss: 0.2263 - val_accuracy: 0.9002

vgg16 being replaced with ResNet50 
Epoch 10/10
625/625 [==============================] - 679s 1s/step - loss: 0.6296 - accuracy: 0.6448 - val_loss: 0.6026 - val_accuracy: 0.6821

basic setting replaced by calling CyclicLR to adjust learning rate, optimizer=torch.optim.RMSprop 
Epoch 10/10
625/625 [==============================] - 976s 2s/step - loss: 0.2878 - accuracy: 0.8723 - val_loss: 0.2656 - val_accuracy: 0.8892

vgg16 being replaced with EfficientNetB7 - val_accuracy: 0.5016

InceptionV3 + ReduceLROnPlateau + optimizer=Adam + StratifiedKFold
Epoch 7/10
625/625 [==============================] - 831s 1s/step - loss: 0.1707 - accuracy: 0.9280 - val_loss: 0.1345 - val_accuracy: 0.9495

vgg16 + ReduceLROnPlateau + optimizer=Adam + StratifiedKFold - val_accuracy: 0.8868
