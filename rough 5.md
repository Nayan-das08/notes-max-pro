## ques 21
![[Pasted image 20230521131915.png]]

The optimization objective of the Generator G in a Generative Adversarial Network (GAN) is to generate images that are able to deceive the Discriminator D into classifying them as real images. This is achieved by minimizing the following objective function:
$$\mathcal{L}= -ln(D(G(z)))$$
where:
- $G(z)$ represents the generated images by the Generator G from random noise input z.
- $D(G(z))$ represents the output of the Discriminator D when given the generated images as input.
- $ln(x)$ represents the natural logarithm of x.

The optimization objective for the Generator in a GAN is to minimize the negative log-probability of the Discriminator classifying the generated images as fake.

## ques 22
bohot difficult

## ques 23
1. CONVx-N:
    -  Output shape: ($H', W', N$)
        -  H' and W' can be calculated using the formula: (H - x + 2P)/S + 1, where H is the input height, x is the filter height, P is the padding, and S is the stride.
        -  The output volume will have N channels.
    -  Number of parameters: $(x \cdot x \cdot C \cdot N) + N$, where C is the number of input channels.

2. POOL-n:
    -  Output shape: ($\frac{H'}{n}, \frac{W'}{n}, C$)
        -  The height and width of the output volume are reduced by a factor of n due to max pooling.
        -  The number of channels remains the same.
    -  Number of parameters: 0 (pooling layers do not have learnable parameters).

3. FLATTEN:
    -  Output shape: ($H' \cdot W' \cdot C$)
        -  The output volume is flattened into a 1-dimensional vector.
        -  The height, width, and number of channels are combined into a single dimension.
    -  Number of parameters: 0 (flattening does not introduce additional parameters).

4. FC-N:
    -  Output shape: ($N,$)
        -  The output is a 1-dimensional vector of length N.
    -  Number of parameters: ($H' \cdot W' \cdot C \cdot N$) + N, where H', W', and C are the dimensions of the input volume.

| Layer               | Output Shape  | Number of Parameters |
|---------------------|--------------|---------------------|
| Input               | 32x32x3      | -                  |
| Conv3-8             | 30x30x8      | 224                 |
| Leaky ReLU          | 30x30x8      | -                  |
| Pool-2              | 15x15x8      | 0                   |
| Batch Normalization | 15x15x8      | 16                  |
| Conv3-16            | 13x13x16     | 1168                |
| Leaky ReLU          | 13x13x16     | -                  |
| Pool-2              | 6x6x16       | 0                   |
| Flatten             | 576          | -                  |
| FC-10               | 10           | 5770                |

## ques 24
| Layer     | Output Shape | Number of Parameters |
|-----------|--------------|----------------------|
| Input     | 32x32x1      | -                   |
| Conv5-10  | 28x28x10     | 260                  |
| Pool2     | 14x14x10     | 0                    |
| Conv5-10  | 10x10x10     | 2,510                |
| Pool2     | 5x5x10       | 0                    |
| FC-10     | 10           | 2,510                |

## ques 25
1. **Oversampling the minority class**
    - In this technique, we can create additional synthetic samples of the minority class (giraffe absent) to balance the class distribution. This can be done by randomly selecting samples from the giraffe absent class and applying data augmentation techniques such as rotation, translation, scaling, or flipping to generate new variations of the images.
    - By oversampling the minority class, we increase the number of examples, making the training set more balanced and providing the model with more instances to learn from. This helps prevent the model from being biased towards the majority class (giraffe present).

2. **Class-specific data augmentation**
    - In this technique, we can apply specific data augmentation techniques tailored to each class to enhance the diversity of samples and help the model generalize better.
    - For example, for the giraffe present class, we can apply random cropping, rotation, and scaling to capture different poses and perspectives of giraffes. On the other hand, for the giraffe absent class, we can apply noise addition, random occlusion, or background transformations to create variations of images without giraffes.
    - By applying class-specific data augmentation, we can generate more diverse samples for each class, which can improve the model's ability to discriminate between the two classes and reduce the bias towards the majority class.

## ques 26
- First layer: convolutional layer with ReLU activation function, with 50 convolutional kernels of shape 3 × 3. 
- Second layer: Max pooling layer with valid padding. This layer should take the 50 two dimensional arrays of shape 26 x 26 as input and transform them into the same number (50) of arrays, with dimensions half that of the original (i.e., from 26 × 26 to 13 × 13 pixels).
- Third layer: first this layer should convert the two-dimensional arrays of the previous layer into 1D array, then create a fully connected layer for the 50 entries using ReLU as the activation function. 
- Output layer: fully connected layer that provides the probability scores (with the softmax function) for each of the 10 output labels of the MNIST dataset. 
- Train the model using Adam optimizer with objective function sparse_categorical_crossentropy and 10 epochs. Evaluate the model and print the train and test losses and accuracies.

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

# Load and preprocess the MNIST dataset
(x_train, y_train), (x_test, y_test) = keras.datasets.mnist.load_data()
x_train = x_train.reshape(-1, 28, 28, 1) / 255.0
x_test = x_test.reshape(-1, 28, 28, 1) / 255.0

# Define the model architecture
model = keras.Sequential([
    layers.Conv2D(50, kernel_size=3, activation="relu", input_shape=(26, 26, 50)),
    layers.MaxPooling2D(pool_size=(2, 2)),
    layers.Flatten(),
    layers.Dense(50, activation="relu"),
    layers.Dense(10, activation="softmax")
])

# Compile the model
model.compile(optimizer="adam", loss="sparse_categorical_crossentropy", metrics=["accuracy"])

# Train the model
model.fit(x_train, y_train, epochs=10, batch_size=32, validation_data=(x_test, y_test))

# Evaluate the model
train_loss, train_acc = model.evaluate(x_train, y_train, verbose=2)
test_loss, test_acc = model.evaluate(x_test, y_test, verbose=2)

# Print the train and test losses and accuracies
print(f"Train Loss: {train_loss:.4f}")
print(f"Train Accuracy: {train_acc:.4f}")
print(f"Test Loss: {test_loss:.4f}")
print(f"Test Accuracy: {test_acc:.4f}")
```

## ques 27
- 3 convolution blocks. 
- Each convolutional block contains a Conv2D layer followed by a max pool layer. 
- The first convolutional block should have 16 filters, 
- the second one should have 32 filters, 
- the third one should have 64 filters. 
- All convolutional filters should be 3 x 3. 
- All max pool layers should have a pool_size of (2, 2). 
- After the 3 convolutional blocks you should have a flatten layer followed by a fully connected layer with 512 units. 
- The CNN should output class probabilities based on 5 classes which is done by the softmax activation function. All other layers should use a relu activation function. 
- You should also add Dropout layers with a probability of 20%, where appropriate.

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

#image_height, image_width, image_channels = appropriate values

# Define the CNN architecture
model = keras.Sequential([
    # Convolutional Block 1
    layers.Conv2D(16, kernel_size=(3, 3), activation="relu", input_shape=(image_height, image_width, image_channels)),
    layers.MaxPooling2D(pool_size=(2, 2)),
    
    # Convolutional Block 2
    layers.Conv2D(32, kernel_size=(3, 3), activation="relu"),
    layers.MaxPooling2D(pool_size=(2, 2)),
    
    # Convolutional Block 3
    layers.Conv2D(64, kernel_size=(3, 3), activation="relu"),
    layers.MaxPooling2D(pool_size=(2, 2)),
    
    # Flatten layer
    layers.Flatten(),
    
    # Fully connected layer
    layers.Dense(512, activation="relu"),
    
    # Dropout layer
    layers.Dropout(0.2),
    
    # Output layer
    layers.Dense(5, activation="softmax")
])

# Compile the model
model.compile(optimizer="adam", loss="categorical_crossentropy", metrics=["accuracy"])

# Print the model summary
model.summary()
```

## ques 28
predicting Celsius to Fahrenheit using dense model. Also describe the architecture and its blocks.

```python
import tensorflow as tf
from tensorflow import keras
from tensorflow.keras import layers

# Define the architecture of the model
model = keras.Sequential([
    # Input layer
    layers.Dense(64, activation='relu', input_shape=[1]),
    
    # Hidden layer
    layers.Dense(64, activation='relu'),
    
    # Output layer
    layers.Dense(1)
])

# Compile the model
model.compile(optimizer='adam', loss='mse')

# Prepare the training data
celsius = [-40, -10, 0, 8, 15, 22, 38]
fahrenheit = [-40, 14, 32, 46, 59, 72, 100]

# Train the model
model.fit(celsius, fahrenheit, epochs=500, verbose=0)

# Test the model
celsius_test = [0, 100]
fahrenheit_pred = model.predict(celsius_test)

# Print the predicted Fahrenheit values
for c, f in zip(celsius_test, fahrenheit_pred):
    print(f"Celsius: {c:.1f}\tPredicted Fahrenheit: {f[0]:.1f}")
```

The architecture of the model consists of three dense (fully connected) layers. Here's a breakdown of the model's blocks:
1. Input layer:
    - The input layer is a single dense layer with 64 units and the ReLU activation function.
    - The input shape is defined as [1] since we are dealing with a single feature (Celsius temperature).
2. Hidden layer:
    - The hidden layer is another dense layer with 64 units and the ReLU activation function.
    - This layer helps the model learn complex relationships between the input and output.
3. Output layer:
    - The output layer is a single dense layer with no activation function.
    - Since we are predicting a continuous value (Fahrenheit temperature), no activation function is applied to the output.

## ques 29
The main difference between a standard RNN (Recurrent Neural Network) and an LSTM (Long Short-Term Memory) is how they handle and propagate information over time.

In a standard RNN, the hidden state at each time step is calculated based on the current input and the previous hidden state. However, standard RNNs suffer from the vanishing gradient problem, where the gradients can exponentially decrease as they propagate back through time. This problem arises when the network needs to remember information over long sequences, making it difficult for the RNN to capture long-term dependencies.

LSTMs were specifically designed to address the vanishing gradient problem by introducing a memory cell and various gating mechanisms. An LSTM cell consists of three main components: the input gate, the forget gate, and the output gate. These gates control the flow of information within the cell, allowing LSTMs to selectively remember or forget information over time.

Here's how an LSTM cell prevents the vanishing gradient problem:

1. Memory Cell:
    -  An LSTM cell has a memory cell that serves as a long-term memory storage. It can maintain and pass information across multiple time steps without being affected by the vanishing gradients.
    
2. Input Gate:
    -  The input gate of an LSTM cell determines which information to let into the memory cell.
    -  It uses a sigmoid activation function to generate a value between 0 and 1 for each input, indicating how much of the input should be stored in the memory cell.
    -  The input gate helps the LSTM to control the flow of information and mitigate the vanishing gradient problem by allowing relevant information to enter the memory cell.
    
3. Forget Gate:
    -  The forget gate of an LSTM cell decides which information to discard from the memory cell.
    -  It uses a sigmoid activation function to generate a value between 0 and 1 for each memory cell element, indicating how much of the information should be forgotten.
    -  The forget gate allows the LSTM to selectively retain important information and discard irrelevant or redundant information.
    
4. Output Gate:
    -  The output gate of an LSTM cell determines the output of the cell.
    -  It uses a sigmoid activation function to decide how much of the memory cell state should be output.
    -  The output gate allows the LSTM to control the information flow from the memory cell to the output, providing relevant information while filtering out unnecessary details.

By incorporating these mechanisms, LSTM cells can selectively retain and propagate information over long sequences, effectively mitigating the vanishing gradient problem. This enables LSTMs to capture long-term dependencies in the data and make them suitable for tasks that involve processing sequential data.

## ques 30
LSTM (Long Short-Term Memory) is a type of recurrent neural network (RNN) architecture that is particularly effective in capturing long-term dependencies in sequential data. One suitable application of LSTM is in natural language processing tasks, such as language translation, sentiment analysis, and text generation.

LSTMs excel in language processing tasks because they can effectively capture dependencies between words or characters that are spread far apart in a sentence. This is crucial for understanding the context and meaning of the text, as meaning often relies on the relationships between words across longer distances.

For example, in machine translation, LSTM models can learn to associate words in the source language with their corresponding translations in the target language, considering the full context of the sentence or even multiple sentences. LSTMs are capable of retaining relevant information over longer sequences, allowing the model to produce accurate translations that preserve the meaning and nuances of the original text.

Now, let's discuss the difference between an LSTM and a GRU (Gated Recurrent Unit) in terms of their gating mechanisms.

While LSTM and GRU are both designed to address the vanishing gradient problem in RNNs, they differ in the number and type of gating mechanisms they employ.

LSTM has three gates: the input gate, the forget gate, and the output gate. These gates control the flow of information within the LSTM cell, allowing it to selectively remember or forget information over time.

On the other hand, GRU has two gates: the update gate and the reset gate. The update gate controls how much of the previous hidden state should be passed along to the current time step, while the reset gate determines how much of the previous hidden state should be ignored and updated with new information.

Compared to LSTM, GRU has a simpler architecture with fewer gates, making it computationally more efficient. However, this simplicity comes at the cost of potentially reduced expressive power compared to LSTM.

In terms of performance, LSTM and GRU have shown similar capabilities in capturing long-term dependencies in sequential data. The choice between LSTM and GRU often depends on the specific task, the size of the dataset, and the computational resources available.

In summary, both LSTM and GRU are powerful architectures for handling sequential data, with LSTM being more complex but capable of capturing longer-term dependencies. Depending on the task and resource constraints, one can choose between LSTM and GRU based on their specific requirements and trade-offs.