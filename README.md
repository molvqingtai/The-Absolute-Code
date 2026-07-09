# The Absolute Code

Coding agents can produce plausible code quickly. They also produce helpers, wrappers, fallbacks, compatibility paths, and tests for code that should not exist. Reviewers need a standard that does not mistake more code for better code.

Coding agents need an optimization objective, not another list of rules.

The Absolute Code defines that objective: express the required behavior and constraints with minimum human-readable code through semantic naming.

**The only rule of The Absolute Code: minimum code.**

_If the same behavior and constraints can be expressed with less code, the extra code must go._

## Convergence

How do we measure good code?

By the minimum human-readable code that expresses the same behavior and constraints.

Good code is also physically minimum code. If code satisfies the requirement and constraints, contains nothing extra, and stays readable through semantic naming, it has moved toward that minimum.

That is the convergence behind clean, elegant, maintainable, and well-designed. Different words, same shape.

This essay calls that shape minimum code. We did not invent it. We named the common denominator. The best possible code cannot be proven, only approached. But when behavior and constraints stay fixed, unnecessary code stays unnecessary no matter how respectable the abstraction looks.

Because the shape is physical, it can be tested: keep behavior, constraints, and semantic naming fixed, then remove everything that can go.

Minimum code is not the fewest characters or the shortest diff. It keeps every necessary boundary, guarantee, and failure state.

## Reduction Test

What can be deleted without changing behavior?

Hold behavior, constraints, and semantic naming fixed. Then ask what can disappear.

Can state be derived instead of stored? Can a branch move to the boundary that owns the difference? Can a wrapper call the primitive directly? Can invalid data become impossible earlier? Can a second truth collapse into one?

If yes, the implementation has not reached minimum code. If no, the remaining code should point to a requirement, boundary, guarantee, failure state, or domain rule.

Reduction is not isolated deletion. It reshapes the model until nothing unnecessary remains.

## Abstraction

When should I abstract this?

Abstract only when it removes more code and concepts than it adds.

An abstraction earns its place when it deletes repetition, names a stable domain concept, hides details callers should not know, or places a boundary where it belongs. Then the rest of the system becomes simpler because the abstraction exists.

An abstraction that only forwards, wraps, renames, or splits direct logic across files is extra code. The reader now has more names, jumps, and places for behavior to hide. Wait until the program has proved the concept exists. Until then, direct code is stricter.

OOP, functional programming, patterns, and libraries are implementation choices, not goals. Use whichever form preserves behavior, constraints, types, safety, errors, and verifiability with the least code.

## Boundaries

Why does the same bug need fixing in three places?

Repeated repair code usually means the boundary is wrong.

Fallbacks, normalization, and compatibility layers belong where uncontrolled shapes enter: external input, migrations, third-party APIs, URL parameters, forms, imported data. Boundary code translates the uncontrolled world into the model the system actually wants.

After that translation, repeated normalization means the model is still leaking. A fallback copied across callers turns an error shape into a supported path. Copied state becomes a second truth and a permanent synchronization problem.

Minimum code pushes data into the right model early, keeps repairs at the edge, and keeps the main path on one model.

## Design Feedback

Why does this feature feel harder than it should?

Awkward code is often design feedback.

If a feature requires wrappers, conversions, copied state, tunneling, repeated normalization, and exception branches in ordinary callers, the local code may not be the real problem. The shape of the model usually is.

Good design shortens implementation because behavior lives where it belongs. Bad design pushes complexity downward until every caller compensates. When changing the model deletes adapters, synchronization, and special handling, that is not cosmetic cleanup. It is design correction.

Minimum code protects teams from tiny-patch thinking. A patch can be small while making the maintained system larger. If the existing model is wrong, a tiny adapter can be worse than a direct reshape.

## Necessary Code

What happens if I delete this?

Minimum code keeps the code that makes the program true.

Types, validation, permissions, error handling, migration compatibility, observability, tests, and failure states can be necessary. Removing them may shorten the implementation, but it also removes guarantees.

Some products need complex code because the domain is complex. Minimum code does not demand a short file. It demands that every remaining piece of complexity comes from the domain, the requirement, or the boundary, not from avoidable structure.

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
