### Plasma Protein Binding Prediction using Graph Neural Network
  
Introduction
  
 Human Plasma Protein Binding measures the proportion of drug that is bounded reversibly to some specific proteins(i.e albumin and alpha-acid glycoprotein in blood). Knowing the amount that is unbounded is crucial because it is that amount that can diffuse or actively taken up into tissues to exert it’s pharmacological activity.


1) Dataset collection
     
   To obtain a diverse and comprehensive dataset, we collected this PPB data from Online Chemical Database, 3857 drug compounds with binding information were extracted. To further  improve the quality and reliability of the data, several pretreatment steps were applied: 
 I) Removing drug compounds that without explicit description for PPB.
 II) Removing duplication of SMILES.
 III) Removing drug compounds which have more than 40 atoms in their compound.
   
   After these operations, a PPB dataset consisting of 1758 drug compounds was finally decided for further study. In this study, 1758 drug compounds were divided into a training set and a test set. And then, we obtained a training set consists of 1406 drug compounds (80%) and a test set consists of 352 drug compounds (20%). The training set was used to construct the prediction model and the test set was further used to assess the predictive ability of the model.

  
 2) Data Processing
     
       Step I:- Defined features of every atoms of molecule and then applied OneHotEncoder on the defined features. This creates a binary column for each feature and returns a sparse matrix.
 
   
       Step II:-  With the help of RDKit, encoded the molecular graph into AdjacencyMatrix. 
       
       
       Step III:- With the help of PyTorch Geometric library, converted  
     the input data into graph object. It simplifies the implementation and working with Graph Neural Networks(GNNs)

3) Building the  Model Architecture

      Here, we defined the model of PPB Prediction with two convolution layers and three layers of fully connected nodes. We have also used the batch normalization for scaling the weights.
In brief, I used a Root Mean Square Error Loss Function, and an Adam optimizer to learn the network parameters. Then the model is trained for a specified number of epochs where the Loss is calculated for each training example and the error is backpropagated using loss.backward(). Then network parameters are updated by optimizer.step().
