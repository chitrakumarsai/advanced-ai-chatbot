# Advanced AI Chatbot

This project is an advanced AI chatbot built using PyTorch. The chatbot can be trained on custom intents and can execute specific functions based on the user's input.

## Features

- Tokenization and lemmatization of input text
- Bag-of-words model for text representation
- Neural network for intent classification
- Customizable function mappings for specific intents
- Save and load trained models

## Requirements

- Python 3.x
- PyTorch
- NLTK
- NumPy

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/chitrakumarsai/advanced-ai-chatbot.git
    cd advanced-ai-chatbot
    ```

2. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

3. Download NLTK data:
    ```python
    import nltk
    nltk.download('punkt')
    nltk.download('wordnet')
    ```

## Usage

1. Prepare your `intents.json` file with the desired intents and patterns.

2. Train the model:
    ```python
    from main import ChatbotAssistant

    assistant = ChatbotAssistant('intents.json')
    assistant.parse_intents()
    assistant.prepare_data()
    assistant.train_model(batch_size=8, lr=0.001, epochs=100)
    assistant.save_model('chatbot_model.pth', 'dimensions.json')
    ```

3. Load the trained model and start chatting:
    ```python
    from main import ChatbotAssistant, get_stocks

    assistant = ChatbotAssistant('intents.json', function_mappings={'stocks': get_stocks})
    assistant.parse_intents()
    assistant.load_model('chatbot_model.pth', 'dimensions.json')

    while True:
        message = input('Enter your message:')
        if message == '/quit':
            break
        print(assistant.process_message(message))
    ```

## Custom Function Mappings

You can define custom functions and map them to specific intents. For example:
```python
def get_weather():
    print("Fetching weather information...")

assistant = ChatbotAssistant('intents.json', function_mappings={'weather': get_weather})
```

## License

This project is licensed under the MIT License.