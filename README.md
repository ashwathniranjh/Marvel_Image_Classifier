# Marvel_Image_Classifier

Problem Statement: To implement a CNN image classifier to find the marvel Superhero.

## How to use: 
Run app.py in terminal, and enjoy :)



## Approach:
Computer vision and neural networks are the hot new IT of machine learning techniques. With advances of neural networks and an ability to read images as pixel density numbers, numerous companies are relying on this technique for more data. For example, speed camera uses computer vision to take pictures of license plate of cars who are going above the speeding limit and match the license plate number with their known database to send the ticket to. Although this is more related to Object Character Recognition than Image Classification, both uses computer vision and neural networks as a base to work.
Keras framework was used to tackle the above given problem. 
Chrome extensions were used to download images in bulk and the dataset was created. The images were traversed through and the RGB data was collected, resized, and stored in an array of objects where each object stored the RGB data and the index of the character whose information is being stored, obtained from a predefined array of strings. The RGB data was then normalized such that each value is a number between 0 and 1. The array is then shuffled to randomize the inputs to the model and then stored into a pkl file using the pickle package. The pkl files for the features and labels are then imported into another notebook for the model training and testing with the dataset. The required packages (TensorFlow, keras) are downloaded. 
The model is then defined using the sequential function. The model in use has 4 activation layers with relu being the activation function in all 4 of them. In all the 4 activation layers used, the grid used for the activation is a 3x3 grid. 4 max pooling layers have been used, where the size of the layer is a 2x2 grid.
The model is then flattened and passed through 3 dense layers where the activation function in use is relu and finally passed through a dense layer with activation function as softmax because softmax as we are working with 5 labels, thus the problem becoming a multinomial probability distribution.Then the model is compiled using the adam optimizer, where the loss is set to sparse categorical crossentropy as we have feature vectors with integer targets(index).
Finally, the model is trained for 10 epochs, where the 10% of the dataset is allocated for validation testing of the model.
The following results were obtained:

 

![image](https://user-images.githubusercontent.com/63347503/123410356-dc3d9480-d5cc-11eb-9d8a-1ad9afefa07c.png)



Finally, the above model was saved, and its weights were saved into a h5 file such that they could be deployed using a flask app.
Initially, in the flask app, the required modules and model are imported, and the flask app is initialized.
The flask app contains of two routes, one GET request to retrieve the landing page and the next is a POST request to obtain the image frontend and format the image such that it is compatible with the model and pass it into the model to obtain a prediction. This prediction is then mapped to its original array to obtain the name of the superhero in the picture. This string retrieved from the mapping and the prediction result template is rendered with the superhero data passed to the front end.
