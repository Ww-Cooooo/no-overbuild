# quality and process

This case includes maintainer feedback from 2026-09-10 and a contextual explanation. The application below is guidance, not a claim that a later implementation passed. The excerpts and their English translation are distinguished explicitly. No original conversation is needed to follow the case.

### What happened

During work on a desktop client, the maintainer asked why requirements from a UI design Skill had not been carried through even though the agent had read it. The subsequent exchange exposed a mistaken interpretation of earlier requests to avoid overengineering: the agent had treated those requests as a reason to minimize the product implementation itself.

The maintainer was asking to remove unhelpful testing and process overhead while still completing the agreed product. This distinction matters because a short slogan such as "keep it lightweight" does not identify which work is unnecessary.

### The maintainer's correction

The following excerpts are verbatim from the maintainer's feedback on 2026-09-10. The second paragraph appeared later in the same message; intervening sentences are omitted here.

> 你理解错了，我说的不要过度工程化，指的意思是不要加一堆没有用的测试，不要加一堆中大型企业才用的一些回归测试和流程之类的。但是我没让你做的时候不把东西做好了呀，你东西得给我做好了呀，那就看来是我们那几大原则有问题。

> 我就是说，不用做那么多测试，不用做那么多没有必要的冒烟的东西，冒烟测试什么的，也没有必要弄一堆没有意义的哈希值在那互相比。我指的是这个意思，而不是说你这个东西做的少。

English translation of those excerpts:

> You misunderstood me. By avoiding overengineering, I meant not adding a pile of useless tests or regression testing and processes needed only by medium-to-large enterprises. I did not mean you could stop doing the work well. You still have to make the product good; that suggests our principles need correction.

> I meant there is no need for so many tests, unnecessary smoke tests, or meaningless comparisons of hashes. That is what I meant, not that you should do less of the product work.

The agent then explained that it should fully consider the design, deliver the requested functionality and experience, and choose tests for actual value. The maintainer confirmed that understanding and asked to repair the principles before continuing the client work. That confirms the intended distinction; it does not establish that a later client implementation was accepted.

### Applying the correction

Suppose the current task calls for a polished interface, useful motion, search, and a working detail view. The instruction to keep the project lightweight does not authorize dropping search, using a static placeholder for the detail view, or replacing requested motion with an unrelated cosmetic transition.

Choose implementation tools by what they help deliver. An existing component or animation library may reduce the work needed to produce a reliable result. Introducing a library only to make the stack look sophisticated would need a different justification. Counting dependencies alone cannot settle that choice.

Verification should examine the result the user will use: the rendered interface, the requested interaction, and the failure or compatibility behavior affected by the change. Repeated full-suite runs or file hashes do not compensate for never checking whether the interaction works or the interface is legible.

If a real constraint makes the requested result impractical, explain the specific tradeoff. Do not silently lower the target and describe the reduced result as an application of this Skill.

### What carries over, and what does not

The reusable lesson is to identify what each piece of work contributes before cutting it. Product completeness, useful design, and meaningful validation can all require effort.

The feedback is not a ban on smoke tests, hashes, enterprise tools, or extensive testing. A smoke test may reveal a broken startup path; a hash may answer whether a downloaded artifact is byte-identical to the expected one. Keep those checks when that is an actual question for the task. They do not answer whether an interface is useful or a feature meets its requirements.

The desktop client's specific visual requirements belong to that task. They do not require every future software project to add motion or a graphical interface.
