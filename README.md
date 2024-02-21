# LSTM Text Prediction

This project uses a Long Short-Term Memory (LSTM) neural network to predict the next word(s) in a sequence of text. It employs TensorFlow and Keras for model building and training.

## Project Overview

The project consists of the following steps:

1. **Tokenization**: The text data is tokenized, and each word is assigned an index for easy identification by the model.

2. **Input Sequence Generation**: Input sequences of varying lengths are generated by iterating over the tokenized text.

3. **Padding**: Since input sequences have different lengths, they are padded with zeros to make them of equal length.

4. **X-Y Split**: The input-output pairs are created, where X is the sequence of words up to the second-to-last word in each input sequence, and Y is the last word in each input sequence.

5. **Model Building**: A sequential LSTM model is built using TensorFlow and Keras. The model architecture includes an embedding layer, multiple LSTM layers, and a dense output layer with softmax activation.

6. **Model Training**: The model is trained on the input-output pairs.

7. **Text Prediction**: The trained model is used to predict the next word(s) in a given input text sequence.

## Usage

1. **Training the Model**:

    ```python
    model.fit(X, Y, epochs=100)
    ```

2. **Text Prediction**:

    ```python
    text = "I am writing"
    for i in range(5):
        token_text = tokenizer.texts_to_sequences([text])[0]
        padded_token_text = pad_sequences([token_text], maxlen=33, padding='pre')
        pos = np.argmax(model.predict(padded_token_text))
        for word, index in tokenizer.word_index.items():
            if index == pos:
                text += " " + word
    ```

## Dependencies

- TensorFlow: Machine learning framework.
- Keras: High-level neural networks API.
- NumPy: Numerical computing library.

## Improvements

To improve the model's performance, you can consider the following:

- **More Data**: Training the model on a larger dataset can improve its predictive capabilities.
- **Hyperparameter Tuning**: Experiment with different hyperparameters such as the number of LSTM units, learning rate, and batch size.
- **Advanced Architectures**: Explore advanced architectures like stacked LSTMs, bidirectional LSTMs, or transformer models.

## Contributing

Contributions are welcome! If you find any bugs or have suggestions for improvement, please open an issue or submit a pull request.

