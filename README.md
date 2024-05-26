# Flask Chat Room Application

This is a Flask-based chat room application that allows users to create or join chat rooms and communicate with each other in real-time using WebSockets via Flask-SocketIO.

## Features

- **Create Chat Rooms**: Users can create new chat rooms with unique codes.
- **Join Chat Rooms**: Users can join existing chat rooms by entering a room code.
- **Real-time Messaging**: Messages are sent and received in real-time using WebSockets.
- **Session Management**: User sessions are managed to keep track of the current room and user.
- **Dynamic Room Management**: Rooms are dynamically created and removed based on user activity.

## Prerequisites

- Python 3.x
- Flask
- Flask-SocketIO

## Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/flask-chat-room.git
cd flask-chat-room
```

2. Create and activate a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

3. Install the required packages:

```bash
pip install -r requirements.txt
```

## Running the Application

1. Set the `SECRET_KEY` for Flask sessions:

```python
app.config["SECRET_KEY"] = "your_secret_key"
```

2. Run the Flask application:

```bash
python app.py
```

3. Open a web browser and navigate to `http://127.0.0.1:5000`.

## File Structure

- `app.py`: Main application file containing the Flask routes and WebSocket event handlers.
- `templates/`: Directory containing HTML templates.
  - `home.html`: Template for the home page where users can create or join rooms.
  - `room.html`: Template for the chat room page where users can send and receive messages.
- `static/`: Directory for static files (CSS, JavaScript, etc.).

## Routes

- `/`: Home route where users can create or join a chat room.
- `/room`: Route for the chat room page. Accessible only if the user has joined a room.

## WebSocket Events

- `connect`: Event fired when a user connects to the WebSocket.
- `message`: Event fired when a user sends a message.
- `disconnect`: Event fired when a user disconnects from the WebSocket.

## Session Management

User sessions are managed using Flask's `session` object. The following session keys are used:

- `room`: Stores the current room code.
- `name`: Stores the user's name.

## Room Management

Rooms are managed using the `rooms` dictionary. Each room has the following structure:

```python
rooms = {
    "room_code": {
        "members": 0,
        "messages": []
    }
}
```

## Functions

### `generate_room_code(length: int, existing_codes: list[str]) -> str`

Generates a unique room code of the specified length. Ensures the code is not in the list of existing codes.

### `home()`

Handles the home route (`/`). Manages the logic for creating and joining chat rooms.

### `room()`

Handles the room route (`/room`). Renders the chat room template.

### WebSocket Event Handlers

- `handle_connect()`: Handles user connection to the WebSocket.
- `handle_message(payload)`: Handles incoming messages from users.
- `handle_disconnect()`: Handles user disconnection from the WebSocket.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgements

This project uses the following open-source libraries:

- Flask
- Flask-SocketIO

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

