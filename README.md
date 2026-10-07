ChronoRoom — Compatibility Matchmaking Bot

A Telegram bot for finding people with similar interests, preferences and communication styles.

Users complete one of six compatibility tests and enter a matchmaking queue. When enough participants are available, the bot forms a group based on similarity between their answers and provides pairwise compatibility statistics.

The project uses Python, "python-telegram-bot" and SQLite.

✨ Features

- 🧠 6 compatibility tests
- 🔎 Matchmaking based on test answers
- 👥 Groups of 7 participants
- 📊 Pairwise compatibility percentages
- 💾 Persistent data storage with SQLite
- 📋 Separate matchmaking queues for each test
- 🔗 Group invitation flow
- 📢 Telegram channel subscription check
- 🧹 Automatic cleanup of previous bot messages
- ⏳ Temporary match state with expiration
- 🔐 Configuration through environment variables
- 🧩 Separate modules for bot logic, database access and matchmaking

🧪 Compatibility Tests

🏠 Basic Test

Questions about everyday habits, leisure, learning, problem solving, social preferences and lifestyle.

💼 Career Test

Questions about work style, teamwork, motivation, communication and professional preferences.

🏰 Dream Castle

A creative personality-style test built around an imaginary castle and symbolic choices.

🚀 Force Test

Questions about entertainment and interests, including TV series, games, music and online content.

❤️ Relationships Test

Questions about communication, friendship, care, conflict resolution and new acquaintances.

🧠 Philosophical Test

Abstract and imaginative questions about the future, consciousness, values and hypothetical situations.

Each test contains 7 questions with 4 possible answers.

🔄 How It Works

1. The user starts the bot with "/start".
2. The bot checks the user's channel subscription.
3. The user chooses one of the six tests.
4. Questions are presented one at a time using inline buttons.
5. Answers are saved after each selection.
6. After completing the test, the user can enter the matchmaking queue.
7. The user is placed into a queue corresponding to the selected test.
8. When 7 participants are available, the matchmaking algorithm selects a group.
9. The selected users receive the list of participants and compatibility statistics.
10. One participant can provide the Telegram group invite link.
11. The link is then sent to the matched participants.

🧮 Matchmaking

The matchmaking algorithm compares participants' answers question by question.

For two users:

compatibility =
matching answers / compared questions

The result is represented as a percentage.

When forming a group, the algorithm starts with the first available participant and iteratively selects candidates with the highest combined compatibility with the users already selected.

The default group size is:

7 participants

The resulting group also receives pairwise compatibility statistics, with the highest-scoring matches displayed first.

🗄️ Database

The project uses SQLite for persistent storage.

"users"

Stores:

- Telegram user ID
- username
- first name
- test answers
- selected test type
- creation timestamp

Answers are serialized as JSON.

"match_queue"

Stores users currently waiting for matchmaking:

- user ID
- test type
- queue status
- join timestamp

An index is created for efficient lookup by test type and queue time.

"matches"

Stores created matches:

- match ID
- participant IDs
- test type
- group information
- invitation link
- creation timestamp
- active status

🧩 Project Structure

ChronoRoom-Bot1/
│
├── bot.py
├── config.py
├── database.py
├── matcher.py
├── subscription.py
│
├── basic_test_questions.py
├── career_test_questions.py
├── castle_test_questions.py
├── force_test_questions.py
├── relationships_test_questions.py
├── philosophical_test_questions.py
│
├── requirements.txt
├── screenshots/
│   └── demo.jpg
│
└── README.md

Module Responsibilities

File| Purpose
"bot.py"| Telegram handlers, test flow, matchmaking flow and group invitations
"database.py"| SQLite database access and persistence
"matcher.py"| Compatibility calculation and group selection
"subscription.py"| Telegram channel subscription verification
"config.py"| Environment-based configuration
"*_test_questions.py"| Question sets for the six compatibility tests

⚙️ Configuration

The bot reads its configuration from environment variables.

Variable| Description
"BOT_TOKEN"| Telegram bot token
"OWNER_ID"| Telegram user ID of the bot owner
"CHANNEL_ID"| Telegram channel ID used for subscription checks
"CHANNEL_USERNAME"| Channel username used when displaying the subscription link

Example:

export BOT_TOKEN="your_bot_token"
export OWNER_ID="123456789"
export CHANNEL_ID="-1001234567890"
export CHANNEL_USERNAME="@your_channel"

Do not commit real credentials or tokens to the repository.

🚀 Installation

Clone the repository:

git clone https://github.com/IuliaBurl/ChronoRoom-Bot1.git
cd ChronoRoom-Bot1

Create a virtual environment:

python -m venv .venv

Activate it:

Linux / macOS

source .venv/bin/activate

Windows

.venv\Scripts\activate

Install dependencies:

pip install -r requirements.txt

Configure the required environment variables and run:

python bot.py

The SQLite database is created automatically when the application starts.

📸 Demo

"ChronoRoom Bot Demo" (screenshots/demo.jpg)

🛠️ Tech Stack

- Python
- python-telegram-bot
- SQLite
- JSON
- async Telegram handlers
- Environment-based configuration

📌 Project Notes

ChronoRoom was originally developed as a standalone Telegram project rather than as a portfolio exercise.

The repository contains the bot's matchmaking logic, persistence layer, compatibility calculation and user interaction flow as separate components.

The project is no longer actively operated, but the source code is preserved as a reference for the implementation and development process.

📄 License

No license is currently specified for this repository.
