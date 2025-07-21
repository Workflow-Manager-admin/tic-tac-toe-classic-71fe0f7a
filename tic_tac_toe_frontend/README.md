# Tic Tac Toe Frontend (Flutter)

This is the Flutter-based frontend for the classic Tic Tac Toe game. It provides the full user interface, local two-player game logic, responsive design, and sleek, modern minimalistic theming.

## Overview

This frontend is a standalone mobile application for two players to play Tic Tac Toe locally on the same device. All game state, turn management, UI updates, and rules enforcement are handled entirely within the app—no backend interaction is necessary for local play.

The backend service is currently used for health check only; future releases may extend its use for features like remote multiplayer, persistence of game histories, or user profiles.

## Project Structure

```
lib/
  main.dart              # App entry point, applies theming and handles home page layout.
  game_logic.dart        # Contains all game rules, turn logic, win/draw detection, and state.
  ui/
    board.dart           # Renders the interactive 3x3 board, passes user input to logic.
    status_bar.dart      # Displays current turn, win or draw messages.
test/
  widget_test.dart       # Basic widget tests.
android/, ios/, ...      # Platform folders from Flutter tooling.
assets/                  # (Unused/no assets currently)
```

## Game Logic (Local Two-Player Play)

- The entirety of Tic Tac Toe logic (move validation, turn alternation, determining winner/draw) resides in `lib/game_logic.dart`.
- A `GameLogic` object manages the board state, current player, game-over condition, and winner.
- Moves are triggered by tapping cells in the rendered board (`ui/board.dart`). The app can be instantly reset at any time.
- This architecture allows for simple extension to support AI, networked play, or time tracking in the future.

## UI & Theming

- The app uses a light, modern minimalistic design, featuring a centered 3x3 grid, clear game status bar, and a tactile restart button.
- Theme colors are:
  - Primary: `#0288D1` (blue)
  - Secondary: `#FFC107` (amber)
  - Accent: `#D32F2F` (red)
- The UI adapts to different device sizes: the board is always square and padded, and text/components scale gracefully.
- Flutter's Material 3 system is leveraged for best practices.

## Responsiveness & Style

- Layout leverages `LayoutBuilder` so the board is always well-sized for mobile devices.
- Button and text styles use bold fonts, high contrast, and spacing for clarity and accessibility.
- All interactions provide instant UI updates for both players.

## Division of Responsibilities

- **Frontend (This Container)**: All gameplay, rules, and UI. No network/API dependency required for basic play.
- **Backend**: Provides a health API and a placeholder for future features.

## Extensibility Notes

- The local game logic is modular, so it can be adapted to:
  - Add AI/bot player support (just insert logic into the `GameLogic` class).
  - Enable online play or match history by syncing moves with a server.
  - Store historical games locally or remotely.
- The theme and styles can easily be customized in `main.dart` for branding or accessibility improvements.

## Interaction with Backend

Currently, the only backend endpoint of interest is a health check for system monitoring and deployment readiness. No gameplay calls are made in this version. For the future:
- Game results or move history might be sent to the backend for analysis or leaderboards.
- Multiplayer matchmaking or chat could be introduced.

## Running & Developing Locally

1. Ensure Flutter is installed and set up.
2. Run `flutter pub get` in this directory.
3. Launch the app on an emulator or real device with:

   ```
   flutter run
   ```

4. To run tests:

   ```
   flutter test
   ```

No additional assets or backend dependencies are required at this stage for local play.

----

For deeper details, review inline code comments in `game_logic.dart`, `main.dart`, and `ui/board.dart`.
