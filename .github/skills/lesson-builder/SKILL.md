---
name: lesson-builder
description: "Design beginner Python classes and exercises with a coherent progression, runnable examples, guided practice, hints, and validation. Use when creating a lesson, class plan, exercise set, workshop, or small beginner project."
argument-hint: "Describe the Python topic, learner level, lesson length, or project goal"
user-invocable: true
disable-model-invocation: false
---

# Beginner Python Lesson Builder

## Purpose

Create a complete, teachable beginner Python lesson or a small sequence of lessons. Produce material that helps a learner understand one main idea, practice it progressively, and leave with a runnable result.

## When to Use

Use this skill when the user asks to:

- Create or improve a Python class or lesson.
- Design beginner exercises, homework, quizzes, or practice tasks.
- Build a short Python workshop or course module.
- Turn a Python topic into a guided learning sequence.
- Create a small beginner project split into checkpoints.

## Inputs and Defaults

Identify these inputs from the request:

- Topic or target outcome.
- Learner level and assumed prior knowledge.
- Class duration or number of sessions.
- Whether the user wants learner materials, instructor notes, solutions, or all three.
- Existing lesson or course location, if provided.

If details are missing, use these defaults and state them briefly: absolute beginner, one 60-90 minute class, Python standard library only, learner-facing lesson plus exercises, and solutions kept separate unless requested. Ask a concise question only when the missing detail would materially change the lesson.

## Procedure

1. Inspect nearby lessons, exercises, README files, and project instructions before creating content. Follow the repository's existing naming and folder conventions.
2. Place the lesson in the appropriate directory, normally `lessons/`, with exercises in `exercises/` and instructor solutions in `solutions/` when requested.
3. Choose one primary concept and define two to four measurable learning objectives. Add prerequisites, setup, estimated time, and a concrete end-of-class outcome.
4. Check the course progression. Briefly review prerequisite concepts and avoid introducing multiple advanced ideas at once.
5. Teach the concept in this order: plain-language explanation, precise vocabulary, minimal runnable example, guided variation, then independent practice.
6. Design exercises in increasing difficulty:
   - Predict or explain a short piece of code.
   - Modify a working example.
   - Write a small function or program.
   - Combine the lesson concept with earlier concepts in a realistic mini-task.
7. For each exercise, include the goal, inputs and expected outputs, constraints, a sample case, and relevant edge cases. Keep full solutions and progressive hints separate from the learner prompt.
8. Add a short recap, a self-check or exit question, and one optional extension. For multi-class projects, define a checkpoint that can be run and reviewed after each session.
9. Run every new code example when possible. Check syntax and verify sample output. Use assertions or lightweight tests for functions and logic when they clarify the contract.
10. Review the final material against the quality checklist below, then summarize created or changed files and the validation performed.

## Teaching Constraints

- Use plain language before formal terminology.
- Introduce one major concept at a time.
- Prefer descriptive names, explicit control flow, and readable formatting over cleverness.
- Follow PEP 8 and use the standard library unless a dependency is essential to the stated goal.
- Avoid dense one-liners, unexplained abstractions, and features beyond the learner's level.
- Keep exercises finishable in one sitting; split larger work into checkpoints.
- Use varied, realistic contexts instead of repetitive arithmetic drills.
- Do not require network access, paid services, or unexplained tools.
- Do not reveal full solutions in learner-facing material unless the user asks for them.

## Quality Checklist

Before finishing, confirm that:

- The lesson has a clear audience, duration, prerequisites, objectives, and outcome.
- The examples are runnable and match the explanation.
- Exercises reinforce the lesson's primary concept and progress from easy to challenging.
- Inputs, outputs, constraints, examples, and edge cases are specified.
- Hints and solutions do not accidentally replace the learner's work.
- The material links to related lessons instead of duplicating them.
- New code has been syntax-checked or run, and any unverified code is clearly identified.
- No unrelated files or dependencies were added.

## Completion Format

Report:

1. The lesson topic and intended learner level.
2. The files created or updated.
3. The exercise progression in one short sentence.
4. Validation performed and any remaining gaps.
