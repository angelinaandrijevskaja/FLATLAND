# FLATLAND
Project: Flatland
Task is slightly inspired by the book Flatland. You will have to classify images by ‘calculating’ a number of corners a figure in that image has using deep learning.
Train set contains pictures of the following shapes: circles, triangles, squares, pentagons, and hexagons.
Tain set - DOWNLOAD (https://github.com/trokas/ai_primer/blob/master/flatland_train.npz). Just download it and upload it to Colab. 
! Don’t use curl since it manages to mess up zipped files!
For your submission create a new github repo and upload code/notebooks and the final model (.h5 file).

Clone the Repository to Your Local Machine:

    1) Open your git Bash terminal or command prompt.
    2) git clone https://github.com/your-username/your-repository.git
(use the following command to clone your newly created repository to your local machine and replace "your-username" with your GitHub username and "your-repository" with the name of your repository.)

Organize Your Project Files:

    1) Move your code, notebooks, and the final model (.h5 file) into the local repository folder that was created when you cloned the repository.
    
 Add, Commit, and Push Changes:

    1) cd your-repository (navigate to your local repository folder using the terminal or command prompt).
    2) git add .
       git commit -m "Initial commit"
       git push origin main
       (use the following commands to add, commit, and push your changes to GitHub)

Next, try to go to the link flatland evaluation and you should see the message ‘Welcome to Flatland!’. This means that the evaluation service is running and you can submit your own model by calling https://us-central1-aiprimer.cloudfunctions.net/flatland?model_link=[PATH TO YOUR .h5] (be patient, it can take a while).

Evaluation script and corrects labels as follows:
  import numpy as np

  data = np.load('flatland_train.npz')
  X = data['X']
  y = data['y']

  y[y != 0] -= 2    # Correct labels so that triangle is mapped to class 1
  X = X / 255.      # Scale down to range [0, 1]

  # Construct and train your model (don't forget train/test split and other tricks)
  model = ...

  # Save the model and upload it to git
  model.save('model.h5')

For faster training you can use colab, just change it to GPU mode by setting it at Edit -> Notebook settings -> Hardware accelerator.
