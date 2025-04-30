# ghc-clean-architecture

This repository demonstrates how to use a `copilot-instructions.md` file to
guide GitHub Copilot in generating a C# API following an opinionated
implementation of Clean Architecture.

## Copilot instructions file

Contextual detail for your codebase can be automatically provided to GitHub
Copilot by adding it to a file located at `.github/copilot-instructions.md`. The
[instructions file](.github/copilot-instructions.md) in this repo demonstrates
how it can be used to guide GitHub Copilot in the creation of new apps following
Clean Architecture, domain-driven design (DDD), and test-driven development
(TDD) principals.

## Sample prompt

Using the provided `copilot-instructions.md` file, the following prompt can be 
used in GitHub Copilot's Agent mode to create an API for a to-do application.
It's recommended that you use Claude 3.7 Sonnet for your model.

```
Create a new API called Todo that follows Clean Architecture principals. Add a use cases for creating and retrieving to-do items.
```

## References

- [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [Domain driven design (DDD)](https://en.wikipedia.org/wiki/Domain-driven_design)
- [Test-driven development (TDD)](https://en.wikipedia.org/wiki/Test-driven_development)
- [GitHub Copilot custom instructions](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot)
- [Choosing the right AI model for your task](https://docs.github.com/en/copilot/using-github-copilot/ai-models/choosing-the-right-ai-model-for-your-task#comparison-of-ai-models-for-github-copilot)
