# How we work

## Traditionally

A common trend when building APIs is to start coding the functionality first, and then test and document it when it is considered to be ready. This makes the API a byproduct of the development process, instead of a product that was intentionally designed.

Event with design guidelines that can help by providing a high-level set of rules, a code-first approach can still cause several problems:

- Documentation and tests are an afterthought and often forgotten, incomplete, or incorrect.
- The functionality is often influenced by how the underlying system already works and may be too limited to achieve the intended goals. This also makes the API less flexible to work with for unforeseen use-cases in the long run.
- Without clearly communicated expectations, the implementation may work very different than the intended behaviour.
- Naming and resource representations are often decided by one or two developers as an afterthought. But because a lot of publiq APIs have some overlapping concepts, this quickly causes inconsistency and confusion about what the right name for a concept is and how they relate to eachother across APIs. (For example in UiTdatabank and UiTPAS we used to speak about `organizers` & `balies`, `labels` & `markers`, ...)

To make matters worse, once an API is released it is hard to make changes to its existing functionality. Once integrations have been built onto it, we must ensure that the API keeps working the same way to avoid breaking those integrations.

Even when these issues get spotted before the API (or new functionality) is released, it is always more work to fix them when the code has already been written and needs to be refactored.

## Design-first

To tackle the problems that come with a code-first approach, we have adopted a design-first approach.

While every team that builds an API is free to implement this how they see fit, our design-first approach centers around a few key principles.

### OpenAPI contracts

Before a single line of code gets written, an [OpenAPI](https://www.openapis.org/) contract has to be created and reviewed by all stakeholders.

These OpenAPI contracts live in the Stoplight project of each product and must conform to the OpenAPI 3.0.x or (preferably) 3.1.x spec.

Stakeholders that are often involved in writing or reviewing the OpenAPI contract:

- The API's product owner, to ensure all required functionality is covered and provide domain expertise
- The API's users, to give input about the expected functionality and behaviour (if possible)
- The API's developer(s), to give technical input
- An API architect, to ensure conformity with the design guidelines and give input on overlapping functionality/naming with existing APIs

Often this is implemented by discussing the required functionality first in a group setting like a meeting or video call, after which either the API developer(s) provide an initial draft of the OpenAPI contract that can then be reviewed by the API architect or vice-versa. In case many questions or problems arise this can be an iterative process with multiple meetings/videocalls with all stakeholders and changes to the draft before it is finalized.

More specifically the OpenAPI contract almost always lives in a git repository, in which a branch gets created for the new functionality. The changes can then be reviewed in a pull request, before they get merged.

### Automatic tests

[WIP]
