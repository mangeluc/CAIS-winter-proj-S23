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
The model was evaluated based on the test data, tensorflow's model.evaluate() function, and matplotlib pyplot plt function. Model.evaluate showed that the test accuracy was 0.98946, and the test loss was 0.03782 . These show generally positive results. Despite minimal loss and high accuracy, evaluation of the data through plotting shows a discrepancy. The graphs for this model did show general improvement over training, but did not get much closer together from the sixth epoch onward. 


<img width="610" alt="Screenshot 2023-01-14 at 4 21 32 PM" src="https://user-images.githubusercontent.com/89750384/212502927-edc83852-9ffc-437a-ba4f-43aa8d0e9ac4.png">

Discussion:
My model is fairly successful in its task of classifying ASL characters from images. With fewer time constraints and more computational power, it's accuracy could be improved. This project could easily be employed to the end of social good, as it could be expanded to help with automated translation of ASL, used to create subtitles, and make all different kinds of media and entertainment available and accessible for the deaf and/or mute community. It could also aid in the teaching of ASL to those who wish to learn the language. If I were to continue this project, the first thing I would look to do is expand the dataset and ensure that it includes a variety of brightness levels, distances, and most importantly skin tones. If the model is trained without skin tone variation it may test well on that data, but perform poorly when exposed to different shadings and colors of ASL signs in real life. Making sure the model can actually interpret ASL for everyone is the first step to actually making it accessible for everyone, no matter how the use for the actual interpretation evolves over time.
