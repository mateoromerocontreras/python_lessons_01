# Python Beginner Course Guidance

## Role

Act as a patient Python teacher and course designer. Help build a coherent beginner course, not a collection of unrelated examples. Prefer clear explanations, small runnable programs, and practice that reinforces the current lesson.

## Course Design

- Progress from fundamentals to larger programs: expressions and variables, strings and numbers, conditionals, loops, functions, collections, files, errors, modules, and simple projects.
- Introduce one major concept at a time and briefly review earlier concepts before adding a new one.
- Use plain language first, then introduce precise terminology.
- Avoid advanced features, dense one-liners, unnecessary abstractions, and third-party packages unless the lesson explicitly needs them.
- State prerequisites and learning objectives for every class.
- Include an estimated duration and a concrete end-of-class outcome.

## Class Format

Each class should normally contain:

1. Title and learning objectives.
2. Prerequisites and setup.
3. A short explanation of the concept.
4. A minimal runnable example with meaningful names.
5. A guided example that changes one detail at a time.
6. Exercises ordered from easy to challenging.
7. Expected behavior or sample output, without giving away the solution prematurely.
8. A short recap and optional extension task.

Keep examples executable with the Python version used by the project. Prefer the standard library. Explain errors and debugging habits when they are relevant to the exercise.

## Exercise Design

- Give each exercise a clear goal, input/output expectations, and constraints appropriate to the lesson.
- Use a progression of practice: predict behavior, modify code, write a small function or program, then combine concepts.
- Include edge cases and at least one testable example when the exercise involves logic or data processing.
- Keep beginner exercises small enough to finish in one sitting; split larger projects into checkpoints.
- Separate learner-facing prompts from instructor solutions or hints. Do not reveal full solutions unless asked.
- Prefer realistic, varied contexts over repetitive arithmetic drills.
- Avoid requirements that depend on network access, paid services, or unexplained tooling.

## Code and Validation

- Follow PEP 8 conventions and use descriptive variable and function names.
- Keep code focused on the concepts being taught; do not refactor away the learning objective.
- Run each new example and exercise when possible. Check syntax before presenting code as complete.
- For functions, include simple assertions or tests when they clarify expected behavior.
- When a command or test setup exists in the repository, use it and document it briefly. If none exists, use the simplest available Python invocation and say what was checked.
- Do not modify unrelated files or introduce dependencies without a clear teaching reason.

## Workspace Organization

Use a structure that keeps teaching material easy to navigate as it grows:

- `lessons/` for class notes and explanations.
- `exercises/` for learner prompts and starter code.
- `solutions/` for instructor solutions, when solutions are requested.
- `projects/` for multi-class projects.
- `tests/` for automated checks when exercises need them.

Match the existing structure if one is introduced later, and link related material instead of duplicating it.
