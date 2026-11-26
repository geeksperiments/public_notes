# A Software Factory Critic Joins a Software Factory

![The software factory, illustrated by Factory](https://factory.com/static/cover-3092ba.png)

*Image: Factory, from [Factory 2.0](https://factory.com/news/software-factory).*

On November 4, 2026, HumanLayer announced it is joining Factory. I noticed because HumanLayer's founder, Dex Horthy, has been one of the sharper critics of the idea Factory is built on. So what is he doing joining them?

## The news

HumanLayer is Dex's company, known for practical writing and talks on working with AI coding agents ([the announcement](https://www.humanlayer.dev/blog/humanlayer-joins-factory)). Factory builds AI agents it calls "droids" for the software development lifecycle. Its end goal is what it calls the software factory: a continuous loop where requests and problems come in, and agents plan, build, test, review, ship and monitor the software ([Factory 2.0](https://factory.com/news/software-factory)).

I had read Dex's essay "Why Software Factories Fail" ([the essay](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/wsff.md)) and I watch a number of his talks, so this caught my attention.

## What he has been arguing

The essay goes after the "lights-off" factory, where AI agents write all the code and no human reads it. His argument comes down to how the models are trained. A model is rewarded when the tests pass, and nothing in that process penalizes it for making the code harder to maintain over time. By maintainability, he means how easily you can change one part of a system without breaking another. His conclusion is that no amount of tooling around the model fixes what is really a training problem. The essay also says you can still move fast without setting your codebase on fire.

![Slide from Dex Horthy's talk: models keep improving at solving one-off problems, while improving codebase quality lags](Attachments/12-factor-factories-slide-know-your-enemy.svg)

*Slide from Dex Horthy's talk ([6:26](https://youtu.be/-NFMsM2y0Vk?t=386)): models keep getting better at one-off problems, not at improving codebase quality.*

## His own answer

His recent talk, ["12 Rules for a Software Factory That Doesn't Ship Slop"](https://youtu.be/-NFMsM2y0Vk), comes close to answering my question. He opens by saying he is now part of Factory. He then says that after he titled his earlier talk and essay "Why Software Factories Fail," people decided he was the anti-software-factory guy. His reply ([1:22](https://youtu.be/-NFMsM2y0Vk?t=82)): he actually loves software factories and is a huge fan.

## What the talk adds

He backs his argument with data from [SlopCodeBench](https://www.scbench.ai/), a benchmark from a University of Wisconsin lab. Instead of asking an AI to solve a single task, it checks whether AI agents keep a codebase healthy as the requirements change. It is still very unsaturated: the best models score in the mid-teens, in percent ([1:22](https://youtu.be/-NFMsM2y0Vk?t=82)). It is an early attempt at the maintainability measurement the essay said was missing.

He also argues that a software factory is a way of thinking about the work, not a black box you can buy ([14:11](https://youtu.be/-NFMsM2y0Vk?t=851)). Some layers you can simply buy, like virtual machines or an off-the-shelf coding agent. Verifying your own code is not one of them. Only your team knows how your code should be tested ([13:25](https://youtu.be/-NFMsM2y0Vk?t=805)). To me that lines up with Factory's own writing about standardizing the process, not just the output.

## The thread, and the open question

At the end of the talk he launched an anti-slop manifesto ([slopmanifesto.com](https://slopmanifesto.com/)). "Slop" is his term for work where someone put less effort into producing it than the reader has to spend understanding it ([15:42](https://youtu.be/-NFMsM2y0Vk?t=942)). The manifesto says AI should make our work better, not just easier, and that humans stay accountable for what ships ([17:09](https://youtu.be/-NFMsM2y0Vk?t=1029)).

The principles in the joining announcement are composable tools over black boxes, multiplayer planning and collaboration, and lab-neutral orchestration. To me they sit comfortably with that philosophy. That is my reading, not his stated reason for joining.

One tension remains. Factory 2.0 describes a continuous loop that it wants to be fully AI-driven. It also says autonomy should grow gradually and that engineers stay responsible for governance and outcomes. How far that goes toward lights-off is what I'd watch.

The entertaining headline is that a critic joined the thing he criticized. His own framing is simpler: he was never against factories, only against slop. My reading is that this move lets him help build the kind he argued for.

## What I take from it

- However the code gets written, we still decide what "good" looks like for our systems and who reviews it ([13:25](https://youtu.be/-NFMsM2y0Vk?t=805), [18:03](https://youtu.be/-NFMsM2y0Vk?t=1083)).
- Passing tests is not the same as healthy code. Quality over time is worth measuring on its own.

---

## Sources

- [HumanLayer is joining Factory](https://www.humanlayer.dev/blog/humanlayer-joins-factory) (Nov 4, 2026)
- [Why Software Factories Fail](https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/wsff.md) (Dex Horthy)
- [12 Rules for a Software Factory That Doesn't Ship Slop](https://youtu.be/-NFMsM2y0Vk) (Dex Horthy, AI Engineer)
- [Factory 2.0: From coding agents to software factories](https://factory.com/news/software-factory)
- [SlopCodeBench](https://www.scbench.ai/)
- [Anti-slop manifesto](https://slopmanifesto.com/)

**Source method:** my summary of the talk is paraphrased from an automated transcript of the recording, checked against its slides, so wording is not quoted and product names may be slightly off. The reading of why he joined Factory is mine, not his.

For a point-by-point summary of the talk, see [12 Factor Factories (Dex Horthy)](./12%20Factor%20Factories%20(Dex%20Horthy).md).
