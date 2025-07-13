Key Features

Server (server.cpp):

Accepts exactly 3 client connections
Manages the complete trivia game flow
Sends questions simultaneously to all clients
Waits for all answers before proceeding
Evaluates answers and updates scores
Sends round results and final leaderboard


Client (client.cpp):

Connects to server with player name
Receives and displays questions nicely formatted
Sends answers to server
Displays results and final rankings


Communication Protocol:

WELCOME: Game start notification
QUESTION: Question with options
ANSWER: Client response format
RESULT: Round results with scores
FINAL: Final leaderboard



How to Build and Run

Compile:
bashmake all
# or manually:
# g++ -std=c++17 -pthread -o server server.cpp
# g++ -std=c++17 -pthread -o client client.cpp

Run:

Start server: ./server
Start 3 clients in separate terminals: ./client



Game Flow

Server waits for exactly 3 players to connect
Each player enters their name
Server sends welcome message and starts the game
For each round:

Server sends question to all clients
Clients display question and wait for user input
Server waits for all 3 answers
Server evaluates answers and updates scores
Server sends results to all clients


After all rounds, server sends final leaderboard

Key Design Decisions

Synchronous gameplay: Server waits for all players before proceeding
Thread-per-client: Each client connection handled by separate thread
Message-based protocol: Simple pipe-delimited messages
Graceful error handling: Handles disconnections and invalid inputs
Filipino theme: Maintains the original Filipino trivia questions

The system is robust and handles multiple clients simultaneously while maintaining the synchronous trivia game experience. The server manages all game state and ensures fair gameplay by waiting for all players before moving to the next round.
