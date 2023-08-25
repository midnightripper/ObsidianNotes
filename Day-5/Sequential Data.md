Sequential data refers to a type of data where the order of elements matters. It represents a series of values or observations arranged in a specific sequence. This data format is commonly encountered in various fields, including time series analysis, natural language processing, genomics, and more.

In sequential data, the relationship between elements is often temporal or contextual. Each element's position in the sequence can hold valuable information, and analyzing sequential patterns is crucial for understanding trends, making predictions, and extracting meaningful insights from the data. Techniques like recurrent neural networks (RNNs) and transformers are commonly used to handle and process sequential data effectively.
![[Pasted image 20230818151347.png]]
Name Entity Recognition
![[Pasted image 20230818152536.png]]

Why not just use normal neural network for NLP?
Using a Recurrent Neural Network (RNN) over a traditional feedforward neural network for Natural Language Processing (NLP) tasks addresses several deficiencies that arise due to the sequential and contextual nature of language. Here are some key shortcomings of using a regular feedforward network for NLP and how RNNs overcome them:

1. **Variable-Length Input:** Traditional networks require fixed input sizes, making them unsuitable for handling variable-length sequences like sentences. RNNs, on the other hand, can process sequences of varying lengths, making them well-suited for NLP tasks where input length varies.
    
2. **Contextual Information:** Feedforward networks treat inputs independently, disregarding the contextual dependencies between words in sentences. RNNs are designed to capture sequential dependencies, allowing them to understand the contextual relationship between words, which is crucial for language understanding.
    
3. **Parameter Sharing:** In feedforward networks, parameters are not shared across different time steps or positions in the sequence. RNNs use shared weights across time steps, which enables them to capture patterns that repeat throughout the sequence.
    
4. **Short-Term Memory:** Traditional networks have limited short-term memory, which makes them inadequate for tasks that involve maintaining and using context over longer sequences. RNNs have an inherent memory mechanism that enables them to remember information from previous time steps and use it for making predictions.
    
5. **Vanishing Gradient Problem:** When training deep networks with many layers, the gradient can become too small, leading to slow or stalled learning. RNNs are designed with mechanisms like LSTM (Long Short-Term Memory) and GRU (Gated Recurrent Unit) cells that mitigate the vanishing gradient problem, allowing for more effective training of deep architectures.
    
6. **Sequential Data Processing:** Traditional networks process input data all at once, treating it as a fixed input. RNNs process sequential data step by step, allowing them to maintain memory of previous steps' computations and make decisions based on cumulative context.
    
7. **Sequential Output Generation:** NLP tasks often involve generating sequences of output, such as in language translation or text generation. RNNs are well-suited for this due to their ability to produce one element at a time while considering previous outputs.


RNN PIPELINE
![[Pasted image 20230818155106.png]]

![[Pasted image 20230818190404.png]]

GRU
![[Pasted image 20230818202819.png]]
At its core, a GRU is a type of recurrent neural network (RNN) designed to capture and model sequences of data, such as sentences in natural language or time series data. GRUs are particularly effective in handling long-range dependencies within sequences, making them suitable for tasks like language modeling, machine translation, and more.

Here's a simplified explanation of how a GRU works:

1. **Introduction to Recurrent Neural Networks (RNNs):** Imagine you're processing a sentence word by word. An RNN processes each word in the sentence one at a time and maintains an internal state (also known as hidden state) that captures information from previous words. This state is updated and passed along as new words are input.
    
2. **Problem of Vanishing and Exploding Gradients:** Traditional RNNs have an issue with vanishing and exploding gradients, which means that the information from earlier words can either fade away or grow excessively as it's passed through the network. This can lead to difficulties in capturing long-range dependencies.
    
3. **Introducing GRU:** A GRU is an improvement over traditional RNNs that helps address the vanishing gradient problem and improve the learning of long-range dependencies. It does this through the use of two mechanisms: an update gate and a reset gate.
    
4. **Update Gate:** The update gate decides how much of the previous internal state should be mixed with the current input to compute the new internal state. It considers the previous hidden state and the current input to generate a value between 0 and 1. This value determines the balance between keeping the old information and incorporating new information.
    
5. **Reset Gate:** The reset gate determines how much of the previous internal state should be forgotten or "reset" when computing the new internal state. It also considers the previous hidden state and the current input to produce a value between 0 and 1.
    
6. **Calculating New Hidden State:** Using the update and reset gates, the GRU calculates a new internal state that balances old information, new input, and what to forget from the previous state. This new internal state is then passed to the next time step.
    
7. **Output Generation:** The new internal state can also be used to generate the output of the current time step, which can be used for various tasks such as predicting the next word in a sentence.


LSTM
![[Pasted image 20230818211600.png]]

Bi-Directional RNN
![[Pasted image 20230818223631.png]]


##  Long Short-Term Memory (LSTM) Network
![[Pasted image 20230819000506.png]]
### Overview of gates and states

#### Forget gate 𝚪𝑓

In an LSTM (Long Short-Term Memory) network, the forget gate plays a crucial role in determining what information from the previous cell state should be retained or discarded for the current time step. It helps the model "forget" outdated or irrelevant information, such as when transitioning from singular to plural subjects in language processing.

The forget gate is a tensor with values between 0 and 1. These values control how much of the previous cell state should be forgotten (set to 0) or remembered (set to 1). The forget gate's behavior is determined by weights (𝐖𝑓) and is influenced by the previous hidden state and the current input (𝑥𝑡).

##### Equation
![[Pasted image 20230819000559.png]]

#### Candidate value 𝐜̃ ⟨𝑡⟩

The candidate value represents the information that could potentially be added to the cell state for the current time step. It captures the current input's influence on the cell state. The candidate value's range is between -1 and 1, and it's created using the tanh function to ensure it stays within this range.
##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000639.png]]

#### Update gate 𝚪𝑖

The update gate helps decide what parts of the candidate value should be incorporated into the new cell state. It's another tensor with values between 0 and 1, controlled by weights (𝐖𝑖). If a unit's value is close to 1, it allows the corresponding value in the candidate value to be passed onto the cell state; if it's close to 0, that value is excluded.

##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000703.png]]

#### Cell state 𝐜⟨𝑡⟩

The cell state maintains the memory of past information and is updated based on the forget gate and the update gate. The previous cell state is adjusted by the forget gate, while the candidate value is adjusted by the update gate. The resulting new cell state is a combination of these two influences.

##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000729.png]]

#### Output gate 𝚪𝑜��[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Output-gate-$\mathbf{\Gamma}_{o}$)

The output gate determines what portion of the cell state should be used to calculate the hidden state, which will then influence the prediction. The output gate's values, like other gates, are between 0 and 1.

##### Equation

![[Pasted image 20230819000757.png]]

#### Hidden state 𝐚⟨𝑡⟩�⟨�⟩[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Hidden-state-$\mathbf{a}^{\langle-t-\rangle}$)

The hidden state is the memory that gets passed to the next LSTM time step. It's determined by the current cell state, influenced by the output gate, and used to calculate the three gates of the next time step.

![[Pasted image 20230819000814.png]]

#### Prediction 𝐲⟨𝑡⟩𝑝𝑟𝑒𝑑

- In the context of classification, the prediction is obtained using a softmax function applied to the weighted sum of the hidden state (𝐚⟨𝑡⟩) and a bias (𝐛𝑦). The softmax function converts these values into probabilities, providing the final prediction for the current time step.