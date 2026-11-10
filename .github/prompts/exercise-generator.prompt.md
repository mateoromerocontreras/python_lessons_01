---
name: exercise-generator
description: "Create beginner Python exercises for a stated topic and difficulty, with clear requirements, examples, edge cases, and optional hints."
argument-hint: "Topic, difficulty (easy/intermediate/challenging), number of exercises, and whether to include hints or solutions"
agent: "agent"
---

Create a set of learner-facing Python exercises for the requested topic and difficulty.

Use the topic, difficulty, number of exercises, and solution preference from the user's request. If omitted, default to one beginner topic, three exercises, standard-library Python, and no full solutions. Ask a concise clarification only when the topic or difficulty is missing and cannot be inferred.

Before writing exercises:

- Read [AGENTS.md](../../AGENTS.md) and follow its course and exercise conventions.
- Inspect the most relevant lesson or exercise file in the workspace so the new work matches the course sequence and avoids duplication.
- Keep the exercises appropriate for the requested difficulty and previously taught concepts.

For each exercise, provide:

- A descriptive title and a clear learner goal.
- Prerequisites or concepts being practiced.
- A precise task description.
- Required inputs, expected outputs, and constraints.
- At least one sample case and relevant edge cases.
- A short completion check the learner can run or verify.

Order the set from easier to harder. Prefer this progression when it fits the topic:

1. Predict or explain a short code example.
2. Modify a small working program.
3. Write a focused function or program.
4. Combine the topic with earlier concepts in a realistic mini-task.

Teaching rules:

- Use plain language and descriptive names.
- Keep examples runnable with Python 3 and avoid third-party packages unless requested.
- Introduce only the concepts needed for the exercise.
- Keep each task small enough to finish in one sitting.
- Include error cases and boundary values when the topic involves input, indexing, or data processing.
- Keep learner prompts separate from hints and solutions. Include progressive hints only when requested. Include full solutions only when explicitly requested.
- Link to related workspace material instead of copying it.

Return the result in this format:

# [Exercise Set Title]

## Audience and Difficulty

State the intended learner level, topic, assumed prerequisites, and estimated time.

## Exercises

Use one subsection per exercise with the required details above.

## Self-Check

Give three to five short questions or checks that confirm the learner understood the topic.

## Instructor Notes

Include only if requested. Otherwise, state that solutions and instructor notes were not included.
