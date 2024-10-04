THWS University Chatbot
This project is a chatbot assistant designed to answer questions related to THWS University. The chatbot is powered by a fine-tuned BART model for question-answering, with predefined responses for frequently asked questions. Additionally, it features a web interface using Flask and supports real-time interaction via a chat window.

The THWS University Chatbot is a conversational agent capable of answering queries about the university, such as general information, events, and frequently asked questions. It also provides predefined responses for certain key topics (e.g., greetings, gratitude, and who created the bot). If the chatbot cannot generate a relevant response, it prompts users to share their questions for future improvement.

The backend is powered by a fine-tuned BART model, while the frontend uses Flask and Bootstrap for a simple and user-friendly chat interface.

Features
Text-Based Question Answering: The bot uses a fine-tuned version of BART to answer questions based on a trained dataset.
Predefined Responses: It handles greetings, common phrases, and fallback responses using predefined responses.
Feedback Mechanism: When the bot cannot answer a question, users are prompted to share their questions to improve the model.
Real-Time Chat Interface: Provides a chat interface using HTML, Bootstrap, and Flask to allow real-time interaction with the chatbot.
Installation
Prerequisites
Python 3.7 or higher
Flask
PyTorch
Transformers (HuggingFace library)
Setup

Clone the repository:

git clone https://github.com/Izdibayev23/uni-chatbot.git
cd thws-chatbot

Install the required dependencies:

pip install -r requirements.txt
Download the pre-trained model and tokenizer: The project uses a fine-tuned BART model. Make sure you have it saved in a folder named fine_tuned_bart in the root directory.

# Example for loading the model and tokenizer

from transformers import BartTokenizer, BartForConditionalGeneration
model = BartForConditionalGeneration.from_pretrained('fine_tuned_bart')
tokenizer = BartTokenizer.from_pretrained('fine_tuned_bart')


Run the Flask app:

python chatbot_app_server.py
The app will run locally at http://localhost:5000.

Access the web interface: Open your browser and navigate to http://localhost:5000 to interact with the chatbot.

Usage
Chat Interface
Ask a question: Type your question in the input field and press Enter or click "Send."
Predefined Responses: The bot can handle greetings like "Hello" or "Hi," and predefined responses such as "Who created you?" will trigger specific answers.
Feedback: When the bot cannot answer a question, it will prompt you to share your question to help improve the model.

Example Commands

Greetings: "Hello" or "Hi"
About the Bot: "Who are you?" or "Who created you?"
Thanks: "Thank you" or "Thanks"

Project Structure
.
├── static/
│   └── thws.png                # University logo for the web interface
├── templates/
│   └── index.html              # HTML template for the chat interface
├── chatbot_app_server.py       # Flask server for handling chat logic
├── fine_tuned_bart/            # Folder containing the fine-tuned model and tokenizer
├── updated_merged.csv          # CSV file used for fine-tuning the BART model
├── unanswered_questions.json   # JSON file to log unanswered questions for model improvement
└── README.md                   # Project README file

Model Fine-tuning
The chatbot uses a fine-tuned BART model for answering questions. The model was trained on a custom dataset that contains pairs of questions and answers. Here's how to fine-tune the model:

Create the dataset: The dataset is expected in the CSV format  with columns question and answer.

Preprocess and tokenize: The dataset is tokenized using the BART tokenizer, where questions and answers are processed and mapped to input/output sequences.

Train the model:
trainer.train()

Save the fine-tuned model:
model.save_pretrained('./fine_tuned_bart')
tokenizer.save_pretrained('./fine_tuned_bart')

Deploy the model using the chatbot server (chatbot_app_server.py).

Web Interface
The web interface uses Flask and HTML to create a simple chat window that allows users to interact with the chatbot in real time.

Home page: Displays the chat window and allows users to ask questions.
Real-time answers: Responses are displayed in the chat box, along with options to share feedback if the bot cannot answer.
Frontend Structure
index.html: Contains the chat interface (input field, chat display, and feedback options).
chatbox.js: Handles AJAX requests to send questions and receive answers.

Contributing
If you'd like to contribute to this project, feel free to submit a pull request or report issues. We welcome contributions such as improving the model, adding new features, or refining the web interface.

