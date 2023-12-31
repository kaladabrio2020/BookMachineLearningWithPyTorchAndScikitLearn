Antes de discutirmos o perceptron e algoritmos relacionados com mais detalhes, vamos fazer um breve tour pelos primórdios do ML. Tentando entender como funciona o cérebro biológico para projetar uma IA.

Warrn McCulloch e Pitts publicaram o primeiro conceito de uma célula cerebral simplificada, o chamado neurônio, em 1943.
Os neurônios biológicos são células nervosas interconectadas no cérebro que estão envolvidas no processamento e transmissão de sinais químicos e elétricos.

McCulloch e Pitts descreveram essas células nervosas como uma porta lógica simples com saídas binárias; múltiplos sinais chegam aos dendritos, eles são então integrados ao corpo celular e, se os sinais acumulados excederem um determinado limite; é gerado um sinal de saída que será transmitido pelo axônio.

Apenas alguns anos depois, rosenblatt publicou o primeiro conceito da regra de aprendizagem perceptron baseada no modelo perceptron MCP. com sua regra do perceptron, Rosenblatt propôs um algoritmo que aprenderia automaticamente os coeficientes de peso ideais que seriam então multiplicados pelos recursos de entrada para tomar a decisão se um neurônio dispara ou não.

More fomally,we can put the idea behind artificial neuron into the context of a binary classification task with two classes : 0 and 1.
We can then define a decision function , o(z), that takes a linear combination of certain input values x, and a corresponding weight vector w, where  is the so called net input.
Now, if the net input of a particular example x, is greater than a defined threshold ,0, we predict class 1 and class 0 otherwise


he whole idea behind the MCP neuron and thresholded perceptron model is to use a reductionist approach to mimic how a single neuron in the brain works: it either fires or it doesn't. Thus rosenblatt classic perceptron rule is fairly simple, and the perceptron algortihm can be summarized by the following steps.

Initailize the weights and bias unit to 0 or small random numbers;
for each training exxample ;
compute output value ;
Note that unlike the vies , each weight wi correspondt to feature, xj in dataset, which is involved in determining the update values Aw, defined above. Furthermore, eta is a learning rate y is the true class label fo the ith training example, and y is the predicted class label. It is important to note that the vies and all weights in the weight vector are being updated simultaneously, which means the we dont recompute predicted label yi , before the vies and all weights are updated via the respective update values ,Awj nad Ab .
It is important to note that the convergence of the perceptron is only guaranteed if the two classes are linearly separable,which means the that the two classes can be perfectly separated by a linear decision function boundary.
If the two class cant bt separeted by a linear decision boundary , we can set a maximum number of passes over the training dataset (epochs) and/or a threshold for the number of tolerated misclassificatio- the perceptron would never stop updating the weigths otherwise.
the preceding diagram illustrates how the perceptron receives the inputs of an example x and combines them with the bias and weights to comput the net input.

using this perceptron implementation, we can now initialize new perceptron object with a given learning rate, and the number of epochs.
VIa the fit method, we initialize the vies b to an initial value 0 and weights in b to a vecto,where m stands for the number of dimensions in the dataset.
technically, we could initialize the weight to zero. However, if we did that , then the learning rate would have no effect on the decision boundary. If all the weights are initialized to zero, the learning rate parameter, eta, affects only the scale of the weght vecto , not the direction. If you are familiar with trigonometry , consider a vector.
here np.arccos is the trigonometry inverse cosine , and np.linalg.norm is a function that computes the length of a vector. 
as an optimal exercise after reading this chapter , you change self.wb and. you will obseve that the decision boundary does not change.


In this two dimensional feature subspace, we can see that a linear decision boundary should be sufficient to separate setosa from versicolor flowers. thus, a linear classifier such as the perceptron should be able to classfy the flowers in this dataset perfecty.
Now, it's time to train our perceptron algortihm on the iris data subset that we just extracted. also,we will plot the misclassification error for each epoch to check whether the algorithm conveged and found a decision boundary that separetes the two iris flowers classes.
Note that the number of misclassication errors and the number of updates is the same, since the perceptron weights and vies are updated each time if misclassifies an example. After executing the preceding code, we should see the plot of the misclassification errors versus the number of epochs.
As we can see 2.7,our perceptron converged after the sixth epoch and should now be able to classify the training examples perfectly.


### Adaptive linear neurons and the convergence of learning
In this section, we will take a look at another type of single layer neural network: Adaptive linear neuron(ADALINE). Adaline was publishe by Bernard and his doctoral sdudent tedd hoff only a few after Rosenblatt perceptron algorithm , and it can be considered an improvement on the latter.
The Adaline algorithm is particularly interesting because it illustrates the key concepts of defining and minimizing continuous loss functions.
This lays the groundwork for undestanding other machine learning algorithms for classification, such as logistic regression ,svm,and multilayer neural networks, as well as linear regression models, which we will  discuss in future chapters.
The keys difference between the adaline rule and perceptron is the the weights are updated based on a linear activation function rather than a unit step function like in the perceptron. In adaline this linear activation function o(z) is simply the identity on function of the net input so that o(z)=z;

Minimizing loss functions with gradient descent
One of the key ingredients of supervised machine learning algorithms is a defined objective function
that is to be optimized during the learning process. This objective function is often a loss or cost function
that we want to minimize. In the case of Adaline, we can define the loss function, L, to learn the model
parameters as the mean squared error (MSE) between the calculated outcome and the true class label: