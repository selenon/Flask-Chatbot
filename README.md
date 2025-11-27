
# Flask Chatbot

A pattern-based chatbot implementation using Python, Flask, and TensorFlow. The bot classifies user input against predefined intents and returns appropriate responses.

## Overview

This chatbot uses a simple neural network trained on an intents file to match user messages to predefined categories. It serves responses through a Flask web interface.

## Project Structure

```
flask-chatbot/
├── app.py              # Flask application and web routes
├── train.py            # Model training script
├── intents.json        # Training data and response patterns
├── chatbot_model.h5    # Trained model (generated)
├── words.pkl           # Vocabulary data (generated)
├── classes.pkl         # Intent classes (generated)
├── templates/          # HTML templates
└── static/             # CSS and client-side assets
```

## Setup

### Prerequisites

- Python 3.7+
- TensorFlow
- Flask

### Installation

1. **Clone and setup environment**
```bash
git clone https://github.com/selenon/flask-chatbot.git
cd flask-chatbot
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

2. **Install dependencies**
```bash
pip install tensorflow flask nltk
```

## Usage

1. **Train the model** (generates `chatbot_model.h5`)
```bash
python train.py
```

2. **Start the Flask server**
```bash
python app.py
```

3. **Access the chatbot** at `http://127.0.0.1:5000/`

## Configuration

### Adding Custom Responses

Edit `intents.json` to add new conversation patterns:

```json
{
  "tag": "custom_topic",
  "patterns": ["user input examples"],
  "responses": ["bot response options"]
}
```

After modifying intents, retrain the model by running `train.py` again.

### Ngrok Setup (Optional)

To expose the bot publicly:

1. Install ngrok: `pip install flask-ngrok`
2. Uncomment `run_with_ngrok(app)` in `app.py`
3. Configure ngrok credentials

## Model Details

- Uses TensorFlow/Keras with embedding layers
- NLTK for text preprocessing
- Pattern matching based on trained intents

