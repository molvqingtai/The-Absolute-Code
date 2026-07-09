# The Absolute Code

Coding agents can produce plausible code quickly. They also add helpers, wrappers, fallbacks, compatibility paths, and tests for code that should not exist. Reviewers need a standard that does not collapse into taste.

Coding agents need an optimization objective, not another list of rules.

The Absolute Code defines that objective: express the required behavior and constraints with minimum human-readable code through semantic naming.

**The only rule of The Absolute Code: minimum code.**

_If the same behavior and constraints can be expressed with less code, the extra code must go._

## Convergence

How do we measure good code?

By the minimum human-readable code that expresses the same behavior and constraints, readable through semantic naming. Good code is also physically minimum code.

If code satisfies the requirement and constraints, contains nothing extra, and remains readable through semantic naming, then it has reached that physical minimum.

That is the convergence behind good code. Clean, elegant, maintainable, and well-designed are different words pointing at the same shape. Abstractions, boundaries, structures, libraries, and models start from different problems, but when they are right they converge here.

We did not invent this shape; we recognized the common denominator of good code. The best possible code cannot be proven, only approached. When behavior and constraints stay the same, less human-readable code with semantic naming is the practical standard for moving closer.

Because the shape is physical, it can be tested: keep behavior, constraints, and semantic naming fixed, then remove everything that can go.

Minimum code is not the fewest characters or the shortest diff. It keeps every necessary boundary, guarantee, and failure state.

## Reduction Test

What can be deleted without changing behavior?

Hold behavior, constraints, and semantic naming fixed. Then ask what can disappear.

Can state be derived instead of stored? Can a branch move to the boundary that owns the difference? Can a wrapper call the primitive directly? Can invalid data become impossible earlier? Can a trusted library replace this mechanism? Can a second truth collapse into one? Can an abstraction disappear because the concept has not appeared?

If yes, the implementation has not reached minimum code. If no, the remaining code should point to a requirement, boundary, guarantee, failure state, or domain rule.

Reduction is not isolated deletion. It reshapes the model until nothing unnecessary remains.

## Abstraction

When should I abstract this?

Abstract only when it removes more code and concepts than it adds.

An abstraction earns its place when it deletes repetition, names a stable domain concept, hides detail callers should not know, or puts a boundary where it belongs. Then the rest of the system carries less.

An abstraction that only forwards, wraps, renames, or splits direct logic across files is extra code. The reader now has more names, jumps, and places for behavior to hide. Wait until the program has proved the concept exists. Until then, direct code is stricter.

OOP, functional programming, patterns, and libraries are implementation choices, not goals. Use whichever form preserves behavior, constraints, types, safety, errors, and verifiability with the least necessary human-readable code through semantic naming.

## Boundaries

Why does the same bug need fixing in three places?

Repeated repair code usually means the boundary is wrong.

Fallbacks, normalization, and compatibility layers belong where uncontrolled shapes enter: external input, migrations, third-party APIs, URL parameters, forms, imported data. Boundary code translates outside shapes into the internal model.

After that translation, repeated normalization means the model is still leaking. A fallback copied across callers turns an error shape into a supported path. Copied state becomes a second truth and a future stale-value bug.

Minimum code pushes data into the right model early, keeps repairs at the edge, and keeps the main path on one model.

## Design Feedback

Why does this feature feel harder than it should?

Awkward code is often design feedback.

If a feature requires wrappers, conversions, copied state, tunneling, repeated normalization, and exception branches in ordinary callers, the model is often the real source of complexity. The source of truth may sit in the wrong layer, or the implementation may bypass a framework or domain primitive that already owns the behavior.

Good design shortens implementation because behavior lives where it belongs. Bad design moves complexity down until every caller compensates. When changing the model deletes adapters, synchronization paths, and exception branches, the model was the fix.

Minimum code protects teams from tiny-patch thinking. A patch can be small while making the maintained system larger. If the existing model is wrong, a tiny adapter can be worse than a direct reshape. The measure is final maintained code, not today's diff.

## Necessary Code

What happens if I delete this?

Minimum code keeps the code that makes the program true.

Types, validation, permissions, error handling, migration compatibility, observability, tests, and failure states can be necessary. Removing them may shorten the implementation, but it removes guarantees. If deleting code hides a failure, breaks a migration, weakens a permission boundary, or makes behavior unverifiable, that code belongs.

Some products need complex code because the domain is complex. Minimum code does not demand a short file. It demands that every remaining piece of complexity come from the domain, the requirement, or a required engineering constraint—not from avoidable structure.

Code golf fails. Dense code that hides boundaries, compresses meaning, or makes failure states hard to see leaves less text, not better code. Semantic naming is part of the standard.

## Agent Integration

Reference this document from `AGENTS.md` or `CLAUDE.md`:

```md
@The-Absolute-Code.md
```

For a remote reference, use the canonical URL:

```md
@https://github.com/molvqingtai/The-Absolute-Code/blob/master/README.md
```

Use it as the coding, review, and refactoring standard: express the required behavior and constraints with minimum human-readable code through semantic naming.
