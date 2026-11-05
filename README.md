# INGE LEAN Customer Service Chatbot

Customer-service chatbot built in **Python** during the **2025 Hackathon** for the company INGE LEAN. It answers questions about the company's services through a menu of options and free-text conversation using the OpenAI API, and can run in the console or as a Telegram bot.

## Objective

Build a working chatbot prototype in a short time, keeping the business logic separate from external services so that the AI provider or the channel (console, Telegram) can be replaced.

## Technologies

- Python 3.12
- OpenAI API (`openai`, model `gpt-3.5-turbo`)
- `python-telegram-bot`
- pandas (service quotations read from an Excel file)
- SQLite (record of users and requested services)
- `python-dotenv` for configuration

## Main features

- Menu with 11 options: services, quotations, coverage, project status, meetings, support, FAQ, human advisor, locations, email and others
- Price quotation based on `datasets/servicios_ingelean.xlsx`
- Free-text answers generated with the OpenAI API
- Storage of users and requested services in SQLite
- Two channels: console and Telegram

## Architecture

The project follows a ports-and-adapters (hexagonal) structure:

```text
domain/      # ChatbotService and menu options (business logic)
ports/       # Interfaces: GPT port, NLP interface, output/repository ports
adapters/    # OpenAI, console, Telegram and SQLite implementations
datasets/    # Services spreadsheet and SQLite database
main.py      # Console entry point
crear_base_datos.py  # Creates the SQLite database
```

## Requirements

- Python 3.10 or later
- An OpenAI API key and, for Telegram, a bot token from @BotFather

## Installation

```bash
git clone https://github.com/leandro-ortegon/ChatBot-inge-lean-proyecto.git
cd ChatBot-inge-lean-proyecto
pip install openai python-dotenv python-telegram-bot pandas openpyxl matplotlib
```

Create a `.env` file in the project root (it is ignored by Git):

```env
OPENAI_API_KEY=your_openai_key
TELEGRAM_TOKEN=your_telegram_bot_token
```

## Running

```bash
python crear_base_datos.py           # create the SQLite database (first time)
python main.py                       # console version
python -m adapters.telegram_adapter  # Telegram bot
```

## Project status

Hackathon prototype (July 2025). Not maintained.
