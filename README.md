# Quiz CLI

A simple Node.js command-line quiz game for learning JavaScript, Node.js fundamentals, and general programming concepts.

This repository did not include a README before, so this file documents the project, how to run it, and how the quiz data is structured.

## Features

- Interactive terminal-based quiz experience
- Category selection
- Optional question count selection
- Randomized question order
- Immediate feedback after each answer
- Final score summary with review of missed questions
- Uses modern ES modules and async/await

## Requirements

- Node.js 18 or newer

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

## Usage

Start the quiz with:

```bash
npm start
```

You will be prompted to:

1. Choose a quiz category
2. Choose how many questions to answer
3. Enter the number of the answer for each question
4. Review your final results
5. Decide whether to play again

## Testing

Run the test suite with:

```bash
npm test
```

> Note: the project currently uses Node's built-in test runner (`node --test`). If no test files are present yet, the command may complete without executing any tests.

## Project Structure

```text
.
├── index.js
├── package.json
├── data/
│   └── questions.json
└── src/
    ├── colors.js
    ├── input.js
    └── quiz.js
```

### File overview

- `index.js` - Application entry point; loads quiz data and runs the main loop
- `src/quiz.js` - Quiz logic, scoring, progress display, and results summary
- `src/input.js` - Terminal input helpers for selections and confirmations
- `src/colors.js` - Console color formatting helpers
- `data/questions.json` - Quiz questions and category data

## Question Data Format

Questions are stored in `data/questions.json` using this structure:

```json
{
  "categories": {
    "category-id": {
      "name": "Category Name",
      "questions": [
        {
          "question": "Question text",
          "options": ["Option A", "Option B", "Option C", "Option D"],
          "answer": 2,
          "explanation": "Optional explanation shown after answering"
        }
      ]
    }
  }
}
```

### Field details

- `categories` - Top-level object containing all quiz categories
- `name` - Display name shown to the player
- `questions` - Array of question objects for the category
- `question` - The question prompt shown in the terminal
- `options` - Array of possible answers
- `answer` - Zero-based index of the correct option
- `explanation` - Optional helper text displayed after each question

## Notes

- The quiz shuffles questions within the selected category each time you play.
- Results include a score summary and a review of any incorrect answers.
- The application uses ES modules, so imports use `import`/`export` syntax rather than CommonJS `require()`.

## Future Improvements

- Add more quiz categories and questions
- Allow full random quiz mode across all categories
- Support timed questions
- Track high scores across runs
- Add automated tests for quiz logic and input handling
- Improve accessibility and keyboard navigation

## License

MIT
