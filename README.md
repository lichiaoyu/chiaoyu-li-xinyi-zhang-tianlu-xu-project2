# Sudoku Project 2

## How to Run
To use, run `npm install` and then `npm run dev` in the root directory.

```bash
npm install
npm run dev
```
## Deliverables

GitHub repo: [https://github.com/lichiaoyu/chiaoyu-li-xinyi-zhang-tianlu-xu-project2](https://github.com/lichiaoyu/chiaoyu-li-xinyi-zhang-tianlu-xu-project2)  
Render app: [https://chiaoyu-li-xinyi-zhang-tianlu-xu-project2.onrender.com/](https://chiaoyu-li-xinyi-zhang-tianlu-xu-project2.onrender.com/)  
Video walkthrough: [https://youtu.be/nEYTEj1mKXM](https://youtu.be/nEYTEj1mKXM)  
Collaborators: Chiao-Yu Li, Xinyi Zhang, Tianlu Xu  

## Challenges Faced

A key challenge was maintaining consistent game behavior across many interactions, including cell selection, input and deletion, conflict validation, resets, and win detection. We addressed this by centralizing state updates in a reducer within `src/state/GameContext.jsx`, ensuring each action follows a single, traceable update path. Another challenge was supporting both 6×6 (easy) and 9×9 (normal) boards without duplicating logic; we parameterized validation and rendering using the board size and subgrid dimensions. Finally, time management was a meaningful constraint: implementing bonus features such as backtracking-based unique puzzles and the hint system required careful scoping so we could still complete and polish the core requirements within the limited timeline.

## Additional Features or Design Changes

Given more time, we would add a notes (“pencil marks”) feature so users can store multiple candidate values in a cell before committing to a final entry. This matches how many players solve Sudoku and would reduce reliance on repeated trial-and-error edits. We would also add a difficulty selector beyond the two required modes (for example, “medium”) by adjusting clue density while reusing the same validation and rendering pipeline. Finally, we would refine puzzle generation performance (especially for unique-solution generation) so new boards can be produced faster without sacrificing correctness.

## Assumptions Made

We assumed the project’s “easy/normal” modes correspond to our Project 1 “easy/hard” visual layout and styling, so we reused the same overall UI structure while updating routes and naming to match the Project 2 requirements. On the selection page, puzzle titles and authors are intentionally mocked, and each selection functions as a navigation entry rather than a single author board with multiple difficulty variants. In this implementation, the mode is determined by the route (`/games/easy` vs `/games/normal`) and the generated puzzle constraints, rather than representing two difficulty versions of an identical board. We also assumed immediate visual feedback is appropriate for this assignment, so conflicts are highlighted rather than preventing input entirely.

## Time to Complete

This assignment took approximately **40 hours**, including planning, implementation, debugging, styling, and final review.

## Bonus Points Accomplished

**Attempted bonus items:**

* **Local Storage (3 pts)**
* **Backtracking / Unique Solution (4 pts)**
* **Hint System (5 pts)**
* **Early Submission (2 pts):** 

**Details:** We implemented unique-solution puzzle generation by generating a solved grid and removing clues only when solution counting confirms the puzzle still has exactly one solution (`src/sudoku/generator.js`, `src/sudoku/solver.js`). We added localStorage persistence to restore in-progress games after refresh, with storage reads/writes scoped to the Context layer and cleared on reset or completion (`src/state/GameContext.jsx`). We also implemented a hint feature that finds a cell with exactly one valid candidate in the current board state and highlights it for the user (`src/sudoku/hint.js`, `src/components/Cell.jsx`).
