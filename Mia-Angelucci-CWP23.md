# ASL Alphabet Classification

Mia Angelucci
Mangeluc@usc.edu

There are 29 different signs that make up the American Sign Language (ASL) alphabet: the 26 letters in the english alphabet, and three extra signs for nothing, delete, and space. This project classifies images of ASL into these 29 classes, and has been trained on Kaggle's ASL dataset, which contains 87,000 200x200 pixel images, each labeled with their corresponding ASL class.


Dataset: 
For this project I used the provided ASL dataset from Kaggle. As described above, it contains 87,000 200x200 pixel images, each labeled with their corresponding ASL class. For preprocessing, I converted the data into numpy arrays and normalized the values by dividing the pixel values of the image by 255. This ensures that each input parameter (pixel, in this case) has a similar data distribution.


Model Development and Training:
The data was split into training and testing in a 70:30 ratio. I chose a ratio with a larger testing dataset, to ensure that after training my model was able to correctly classify images with different qualities (image brightness, image darkness, skin tone, etc). 
For the model itself, I used a keras sequential model (https://keras.io/guides/sequential_model/ used as reference). It is a CNN with four layers, utilizing batch normalization functions and dropout layers to avoid overfitting. Max pooling was also applied (based on the keras.io implementation). The activation function used was softmax, as the model deals with 29 classes. I used the keras Adam optimizer with .001 as the learning rate, and categorical cross-entropy as the loss function for the same reason I used softmax as the activation function- this model is doing a multiclass classification. For training, I used an 80:20 validation split.


Model Evaluation/results:
The model was evaluated based on the test data, tensorflow's model.evaluate() function, and matplotlib pyplot plt function. Model.evaluate showed that the test accuracy was 0.98946, and the test loss was 0.03782 . These show generally positive results. The graphs for this model did show general improvement over training but 


<img width="610" alt="Screenshot 2023-01-14 at 4 21 32 PM" src="https://user-images.githubusercontent.com/89750384/212502927-edc83852-9ffc-437a-ba4f-43aa8d0e9ac4.png">
