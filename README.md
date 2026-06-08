---
title: quiz-cli
description: Interactive command-line quiz game for learning JavaScript
license: MIT
---

# quiz-cli

An interactive command-line quiz game for learning JavaScript and general programming concepts.

## Overview

`quiz-cli` is a self-contained Node.js terminal application that loads quiz questions from JSON, lets the user choose a category and question count, and then presents multiple-choice questions one by one with instant feedback and a final score summary.

The app is built with modern ES modules and uses Node's built-in `readline` and file system APIs. Questions, answer options, and explanations are separated from the application logic in `data/questions.json`.

## Features

- Interactive terminal quiz experience
- Category selection from JSON-driven question sets
- Question count selection before starting a quiz
- Randomized question order within a quiz session
- Multiple-choice answers entered by number
- Immediate correct/incorrect feedback
- Explanations shown after each question
- Final results summary with performance message
- Review of incorrect answers at the end
- Replay prompt after each round
- ANSI color styling for improved readability

## Tech Stack

- **Runtime:** Node.js `>=18.0.0`
- **Language:** JavaScript
- **Module system:** ES modules (`"type": "module"`)
- **Built-in Node APIs:**
  - `node:fs/promises`
  - `node:url`
  - `node:path`
  - `node:readline`
- **Testing:** Node's built-in test runner (`node --test`)

## Prerequisites

- Node.js **18 or newer**
- A terminal capable of displaying ANSI color codes

## Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd test-app
   ```

2. Install dependencies:

   The repository does not declare any external npm dependencies in `package.json`, so there is nothing required to install. If you want to initialize the local project state anyway, you can still run:

   ```bash
   npm install
   ```

## Configuration

No environment variables or external configuration files are used.

The quiz content is defined in:

- `data/questions.json`

To change the quiz content, edit that file directly.

## Usage

Start the application:

```bash
npm start
```

This runs:

```bash
node index.js
```

### What happens when the app starts

1. A welcome banner is displayed.
2. You choose a category.
3. You choose how many questions to answer.
4. The quiz begins.
5. Each answer is checked immediately.
6. Your score and review are shown at the end.
7. You are asked whether you want to play again.

### Answering questions

- Menu selections are made by entering the number of the option.
- Confirmation prompts accept `y`/`n` style input.
- Between questions, the app may prompt you to press Enter to continue.

## Available Categories

The bundled question set includes:

- JavaScript Basics
- Node.js Fundamentals
- General Programming

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
  Application entry point and main control flow.

- **`src/quiz.js`**  
  Quiz logic, scoring, progress bar rendering, and results display.

- **`src/input.js`**  
  Terminal input helpers built on Node's `readline` module.

- **`src/colors.js`**  
  ANSI color and text styling helpers.

- **`data/questions.json`**  
  Quiz content and question data model.

## Scripts / Commands

From `package.json`:

| Script | Command | Description |
| --- | --- | --- |
| `start` | `node index.js` | Starts the quiz application |
| `test` | `node --test` | Runs Node's built-in test runner |

## Testing

The repository defines a `test` script:

```bash
npm test
```

However, no test files were included in the provided repository snapshot. As a result, `node --test` may complete without running any tests unless you add test files.

## Deployment

This project is designed as a local command-line application.

No deployment configuration, CI/CD workflow, or production build pipeline is included in the repository.

## Contributing

No contributing guidelines were provided in the repository.

If you want to extend the app, likely entry points include:

- Adding or editing questions in `data/questions.json`
- Extending quiz behavior in `src/quiz.js`
- Adding new terminal prompts in `src/input.js`
- Adjusting styling in `src/colors.js`

## License

MIT, according to `package.json`.

No separate `LICENSE` file was included in the provided snapshot.

## Troubleshooting / FAQs

### The app exits with an error immediately
- Make sure you are running **Node.js 18+**.
- Confirm that `data/questions.json` exists and contains valid JSON.

### Colors are not displaying correctly
- Use a terminal that supports ANSI escape codes.
- Some minimal terminals or redirected output streams may not render styling.

### `npm test` reports no tests
- This is expected if no `*.test.js` / `*.spec.js` files exist yet.
- Add tests using Node's built-in test runner to enable meaningful test coverage.

### Can I add more categories or questions?
Yes. Add new category entries and question objects to `data/questions.json` using the existing structure:

- top-level `categories`
- each category has:
  - `name`
  - `questions`
- each question has:
  - `question`
  - `options`
  - `answer` (zero-based index)
  - `explanation`

### Are there any environment variables to configure?
No. The application does not use environment variables.

## Data Model

Each question in `data/questions.json` follows this shape:

```json
{
  "question": "Question text",
  "options": ["Option 1", "Option 2", "Option 3", "Option 4"],
  "answer": 2,
  "explanation": "Why the correct answer is correct."
}
```

- `answer` is a **zero-based index** into the `options` array.

## Notes

- The quiz logic shuffles questions before each round.
- The application currently uses only built-in Node.js modules.
- The repository snapshot does not include external assets, build tooling, or deployment files.