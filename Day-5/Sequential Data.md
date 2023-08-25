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

- Let's assume you are reading words in a piece of text, and plan to use an LSTM to keep track of grammatical structures, such as whether the subject is singular ("puppy") or plural ("puppies").
- If the subject changes its state (from a singular word to a plural word), the memory of the previous state becomes outdated, so you'll "forget" that outdated state.
- The "forget gate" is a tensor containing values between 0 and 1.
    - If a unit in the forget gate has a value close to 0, the LSTM will "forget" the stored state in the corresponding unit of the previous cell state.
    - If a unit in the forget gate has a value close to 1, the LSTM will mostly remember the corresponding value in the stored state.

##### Equation
![[Pasted image 20230819000559.png]]
##### Explanation of the equation:

- 𝐖𝐟�� contains weights that govern the forget gate's behavior.
- The previous time step's hidden state [𝑎⟨𝑡−1⟩[�⟨�−1⟩ and current time step's input 𝑥⟨𝑡⟩]�⟨�⟩] are concatenated together and multiplied by 𝐖𝐟��.
- A sigmoid function is used to make each of the gate tensor's values 𝚪⟨𝑡⟩𝑓��⟨�⟩ range from 0 to 1.
- The forget gate 𝚪⟨𝑡⟩𝑓��⟨�⟩ has the same dimensions as the previous cell state 𝑐⟨𝑡−1⟩�⟨�−1⟩.
- This means that the two can be multiplied together, element-wise.
- Multiplying the tensors 𝚪⟨𝑡⟩𝑓∗𝐜⟨𝑡−1⟩��⟨�⟩∗�⟨�−1⟩ is like applying a mask over the previous cell state.
- If a single value in 𝚪⟨𝑡⟩𝑓��⟨�⟩ is 0 or close to 0, then the product is close to 0.
    - This keeps the information stored in the corresponding unit in 𝐜⟨𝑡−1⟩�⟨�−1⟩ from being remembered for the next time step.
- Similarly, if one value is close to 1, the product is close to the original value in the previous cell state.
    - The LSTM will keep the information from the corresponding unit of 𝐜⟨𝑡−1⟩�⟨�−1⟩, to be used in the next time step.

##### Variable names in the code
The variable names in the code are similar to the equations, with slight differences.

- `Wf`: forget gate weight 𝐖𝑓
- `bf`: forget gate bias 𝐛𝑓
- `ft`: forget gate Γ⟨𝑡⟩𝑓Γ

#### Candidate value 𝐜̃ ⟨𝑡⟩

- The candidate value is a tensor containing information from the current time step that **may** be stored in the current cell state 𝐜⟨𝑡⟩�⟨�⟩.
- The parts of the candidate value that get passed on depend on the update gate.
- The candidate value is a tensor containing values that range from -1 to 1.
- The tilde "~" is used to differentiate the candidate 𝐜̃ ⟨𝑡⟩�~⟨�⟩ from the cell state 𝐜⟨𝑡⟩

##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000639.png]]
##### Explanation of the equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Explanation-of-the-equation)

- The _tanh_ function produces values between -1 and 1.

##### Variable names in the code

- `cct`: candidate value 𝐜̃ ⟨𝑡⟩

#### Update gate 𝚪𝑖

- You use the update gate to decide what aspects of the candidate 𝐜̃ ⟨𝑡⟩�~⟨�⟩ to add to the cell state 𝑐⟨𝑡⟩�⟨�⟩.
- The update gate decides what parts of a "candidate" tensor 𝐜̃ ⟨𝑡⟩�~⟨�⟩ are passed onto the cell state 𝐜⟨𝑡⟩�⟨�⟩.
- The update gate is a tensor containing values between 0 and 1.
    - When a unit in the update gate is close to 1, it allows the value of the candidate 𝐜̃ ⟨𝑡⟩�~⟨�⟩ to be passed onto the hidden state 𝐜⟨𝑡⟩�⟨�⟩
    - When a unit in the update gate is close to 0, it prevents the corresponding value in the candidate from being passed onto the hidden state.
- Notice that the subscript "i" is used and not "u", to follow the convention used in the literature.

##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000703.png]]
##### Explanation of the equation

- Similar to the forget gate, here 𝚪⟨𝑡⟩𝑖��⟨�⟩, the sigmoid produces values between 0 and 1.
- The update gate is multiplied element-wise with the candidate, and this product (𝚪⟨𝑡⟩𝑖∗𝑐̃ ⟨𝑡⟩��⟨�⟩∗�~⟨�⟩) is used in determining the cell state 𝐜⟨𝑡⟩�⟨�⟩.

##### Variable names in code (Please note that they're different than the equations)[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Variable-names-in-code-(Please-note-that-they're-different-than-the-equations))

In the code, you'll use the variable names found in the academic literature. These variables don't use "u" to denote "update".

- `Wi` is the update gate weight 𝐖𝑖�� (not "Wu")
- `bi` is the update gate bias 𝐛𝑖�� (not "bu")
- `it` is the update gate 𝚪⟨𝑡⟩𝑖��⟨�⟩ (not "ut")

#### Cell state 𝐜⟨𝑡⟩

- The cell state is the "memory" that gets passed onto future time steps.
- The new cell state 𝐜⟨𝑡⟩�⟨�⟩ is a combination of the previous cell state and the candidate value.

##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000729.png]]
##### Explanation of equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Explanation-of-equation)

- The previous cell state 𝐜⟨𝑡−1⟩�⟨�−1⟩ is adjusted (weighted) by the forget gate 𝚪⟨𝑡⟩𝑓��⟨�⟩
- and the candidate value 𝐜̃ ⟨𝑡⟩�~⟨�⟩, adjusted (weighted) by the update gate 𝚪⟨𝑡⟩𝑖��⟨�⟩

##### Variable names and shapes in the code[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Variable-names-and-shapes-in-the-code)

- `c`: cell state, including all time steps, 𝐜� shape (𝑛𝑎,𝑚,𝑇𝑥)
- `c_next`: new (next) cell state, 𝐜⟨𝑡⟩�⟨�⟩ shape (𝑛𝑎,𝑚)
- `c_prev`: previous cell state, 𝐜⟨𝑡−1⟩�⟨�−1⟩, shape (𝑛𝑎,𝑚)

#### Output gate 𝚪𝑜��[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Output-gate-$\mathbf{\Gamma}_{o}$)

- The output gate decides what gets sent as the prediction (output) of the time step.
- The output gate is like the other gates, in that it contains values that range from 0 to 1.

##### Equation

![[Pasted image 20230819000757.png]]
##### Explanation of the equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Explanation-of-the-equation)

- The output gate is determined by the previous hidden state 𝐚⟨𝑡−1⟩�⟨�−1⟩ and the current input 𝐱⟨𝑡⟩�⟨�⟩
- The sigmoid makes the gate range from 0 to 1.

##### Variable names in the code[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Variable-names-in-the-code)

- `Wo`: output gate weight, 𝐖𝐨��
- `bo`: output gate bias, 𝐛𝐨��
- `ot`: output gate, 𝚪⟨𝑡⟩𝑜��⟨�⟩

#### Hidden state 𝐚⟨𝑡⟩�⟨�⟩[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Hidden-state-$\mathbf{a}^{\langle-t-\rangle}$)

- The hidden state gets passed to the LSTM cell's next time step.
- It is used to determine the three gates (𝚪𝑓,𝚪𝑢,𝚪𝑜��,��,��) of the next time step.
- The hidden state is also used for the prediction 𝑦⟨𝑡⟩�⟨�⟩.

##### Equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Equation)

![[Pasted image 20230819000814.png]]
##### Explanation of equation[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Explanation-of-equation)

- The hidden state 𝐚⟨𝑡⟩�⟨�⟩ is determined by the cell state 𝐜⟨𝑡⟩�⟨�⟩ in combination with the output gate 𝚪𝑜��.
- The cell state state is passed through the `tanh` function to rescale values between -1 and 1.
- The output gate acts like a "mask" that either preserves the values of tanh(𝐜⟨𝑡⟩)tanh⁡(�⟨�⟩) or keeps those values from being included in the hidden state 𝐚⟨𝑡⟩�⟨�⟩

##### Variable names and shapes in the code[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Variable-names--and-shapes-in-the-code)

- `a`: hidden state, including time steps. 𝐚� has shape (𝑛𝑎,𝑚,𝑇𝑥)(��,�,��)
- `a_prev`: hidden state from previous time step. 𝐚⟨𝑡−1⟩�⟨�−1⟩ has shape (𝑛𝑎,𝑚)(��,�)
- `a_next`: hidden state for next time step. 𝐚⟨𝑡⟩�⟨�⟩ has shape (𝑛𝑎,𝑚)(��,�)

#### Prediction 𝐲⟨𝑡⟩𝑝𝑟𝑒𝑑

- The prediction in this use case is a classification, so you'll use a softmax.

The equation is:

𝐲⟨𝑡⟩𝑝𝑟𝑒𝑑=softmax(𝐖𝑦𝐚⟨𝑡⟩+𝐛𝑦)�����⟨�⟩=softmax(���⟨�⟩+��)

##### Variable names and shapes in the code[](https://useaapvuptka.labs.coursera.org/notebooks/W1A1/Building_a_Recurrent_Neural_Network_Step_by_Step.ipynb#Variable-names-and-shapes-in-the-code)

- `y_pred`: prediction, including all time steps. 𝐲𝑝𝑟𝑒𝑑����� has shape (𝑛𝑦,𝑚,𝑇𝑥)(��,�,��). Note that (𝑇𝑦=𝑇𝑥)(��=��) for this example.
- `yt_pred`: prediction for the current time step 𝑡�. 𝐲⟨𝑡⟩𝑝𝑟𝑒𝑑�����⟨�⟩ has shape (𝑛𝑦,𝑚)