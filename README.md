---
title: quiz-cli
description: An interactive terminal-based quiz game for learning JavaScript, Node.js, and general programming concepts.
---

# quiz-cli

`quiz-cli` is an interactive command-line quiz application built with Node.js. It loads quiz content from a JSON data file, lets the user choose a category and number of questions, runs a scored quiz session in the terminal, and then shows results with explanations and a review of incorrect answers.

## Overview

The application is a CLI-based quiz runner intended for learning and self-assessment. It uses terminal prompts to guide the user through a quiz session and presents feedback with ANSI-colored output.

Based on the repository contents, the app:

- loads questions from `data/questions.json`
- shows a welcome banner
- prompts for quiz category and question count
- randomizes questions
- tracks score and progress
- displays results and incorrect-answer review
- offers a replay option
- closes the readline interface cleanly on completion or error

## Features

- Interactive terminal quiz experience
- Category-based question selection
- User-defined question count per quiz session
- Randomized question order
- Progress tracking with a progress bar
- Immediate correctness feedback
- Final score summary
- Review of incorrect answers with explanations
- Replay support
- ANSI-colored terminal styling

## Tech Stack

- **Runtime:** Node.js `>=18.0.0`
- **Module system:** ES modules
- **Built-in Node APIs used:**
  - `node:fs/promises`
  - `node:path`
  - `node:url`
  - `readline`
- **Data format:** JSON
- **Testing:** Node test runner via `node --test`

> No third-party dependencies are indicated in the provided repository details.

## Prerequisites

- Node.js **18.0.0 or later**
- npm (bundled with Node.js)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/folken718/test-app.git
   cd test-app
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

> The provided repository information does not mention any external dependencies, but running `npm install` is still the standard setup step.

## Configuration

There is no separate configuration file mentioned in the repository.

Quiz content is configured through:

- `data/questions.json`

### Question data structure

The JSON file contains a top-level `categories` array. Each category includes:

- `name`
- `questions`

Each question includes:

- `question`
- `options`
- `answer` — index of the correct option
- `explanation`

### Included categories

- JavaScript Basics
- Node.js Fundamentals
- General Programming

## Usage

Start the application with:

```bash
npm start
```

This runs:

```bash
node index.js
```

### Typical flow

1. Launch the CLI.
2. Read the welcome banner.
3. Select a quiz category.
4. Choose how many questions to answer.
5. Answer each question in sequence.
6. Review progress and feedback.
7. View the final score and incorrect-answer explanations.
8. Choose whether to replay.

## Scripts / Commands

From `package.json`:

| Command | Description |
| --- | --- |
| `npm start` | Runs the quiz app with `node index.js` |
| `npm test` | Runs the Node.js test runner with `node --test` |

## Project Structure

```text
data/
  questions.json
index.js
package.json
src/
  colors.js
  input.js
  quiz.js
```

### File responsibilities

- **`index.js`**  
  Main entry point and application orchestration. Loads quiz data, handles the welcome flow, category/question selection, quiz execution, replay, and error handling.

- **`src/quiz.js`**  
  Core quiz logic. Includes question shuffling, quiz state, progress tracking, scoring, question handling, progress bar rendering, and final results display.

- **`src/input.js`**  
  Terminal input helpers. Provides readline interface creation and prompt utilities such as menu selection, confirmation, and pause behavior.

- **`src/colors.js`**  
  ANSI color helpers for formatted terminal output.

- **`data/questions.json`**  
  Quiz content and category/question data.

- **`package.json`**  
  Project metadata, module type, entry point, and scripts.

## Testing

The repository defines a test script:

```bash
npm test
```

This runs:

```bash
node --test
```

> The provided repository summary does not list any specific test files, so test coverage may be limited or not yet present.

## Deployment

This project is a local CLI application rather than a deployed web service.

### Recommended usage

- Run locally in a terminal with Node.js 18+
- Distribute as source code or a Node package if desired

> No deployment pipeline, publishing configuration, or production hosting setup is included in the provided repository contents.

## Contributing

If you want to extend the app, the repository structure suggests these safe extension points:

- Add or edit quiz content in `data/questions.json`
- Adjust terminal styling in `src/colors.js`
- Modify quiz flow and scoring in `src/quiz.js`
- Update user interaction behavior in `src/input.js`
- Change startup or replay behavior in `index.js`

Suggested contribution workflow:

1. Create a branch.
2. Make focused changes.
3. Add or update tests if applicable.
4. Run `npm test`.
5. Run `npm start` to verify the quiz flow manually.
6. Open a pull request.

## Troubleshooting

### `npm start` fails with an unsupported Node version
Make sure you are using Node.js **18.0.0 or later**.

### Questions do not load
Check that `data/questions.json` is valid JSON and follows the expected structure.

### Terminal output looks plain or uncolored
The app uses ANSI color helpers. If your terminal does not support ANSI colors, styling may not display as intended.

### Quiz ends unexpectedly
The app is designed to close the readline interface cleanly on error. If the session exits early, inspect the terminal output for validation or data-loading issues.

## FAQ

### How do I add more questions?
Edit `data/questions.json` and add questions under the appropriate category.

### How do I add a new category?
Add a new category object to the top-level `categories` array in `data/questions.json`.

### Can I change the quiz styling?
Yes. The terminal styles are defined in `src/colors.js`.

### Is there a web UI?
No. Based on the repository contents, this is a terminal-based CLI application only.

## License

A license file was not provided in the repository contents reviewed for this README.

If you intend to publish or share the project, add a license file and document it here.