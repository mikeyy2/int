# Reflection

## The topic

We built an interactive visualizer for **integer (arithmetic) overflow**. We chose this topic because it is self-contained and lends itself well to a visual, hands-on demonstration. The whole idea of overflow is about what happens at the boundary of a fixed-width value, and letting a user physically push a number past that boundary and watch it wrap makes the concept much more intuitive than reading about it.

## What we learned

Building the tool forced us to be precise about a few things we had only loosely understood before. The biggest one was that a value and its *interpretation* are two separate things. The same byte `0xFF` is `255` when read as unsigned and `-1` when read as signed two's complement. We had seen this stated in class, but having to display both interpretations from the same stored bits side by side made it click.

We also got a clearer picture of why overflow is dangerous in real code rather than just being a curiosity. The classic bug is a size or length check such as `if (len + 1 < buffer_size)`. If `len` is already at its maximum, `len + 1` wraps to a small number, the check passes when it should fail, and a buffer can be overrun. Seeing the wraparound happen made that failure mode concrete.

## The workflow

We used an AI-assisted development workflow:

1. **Scoping.** We described the assignment and the topic options to the AI and talked through which concept would be easiest to make genuinely interactive. We settled on integer overflow and a focused single-interaction design.
2. **Generation.** The AI produced a first version as a single self-contained HTML/JavaScript file, with no external dependencies so it would run by just opening it in a browser.
3. **Iteration.** We reviewed the result and asked for changes to the content and presentation until it matched what we wanted, including refining the wording of the explanations and cleaning up the final layout.
4. **Documentation.** We had the AI help generate the README, then wrote this reflection in our own words.

## Takeaways

The AI was most useful for getting past the blank-page stage quickly and for handling the boilerplate of a clean, responsive UI. The understanding came from reviewing and refining the output. We had to actually reason about whether the signed/unsigned math was correct and whether the explanations were accurate, which meant we could not treat the generated code as a black box.
