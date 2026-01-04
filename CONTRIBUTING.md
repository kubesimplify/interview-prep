# Contributing to Kubesimplify Interview Prep

Thank you for your interest in contributing to the **Kubesimplify Interview Prep** platform! We are an open-source, community-driven project dedicated to providing high-quality, real-world interview scenarios for DevOps, SRE, and Kubernetes roles.

## Project Structure

This project is built with **Hugo** and uses a structured content hierarchy. Understanding this structure is key to making successful contributions.

```text
content/
├── devops/
│   ├── beginner/
│   │   ├── _index.md        # Level definitions
│   │   └── question-1.md    # Actual interview question
│   ├── advance/
│   └── expert/
├── sre/
│   ├── beginner/
│   └── ...
└── k8s/
    ├── beginner/
    └── ...
```

## How to Contribute a New Question

We welcome new interview scenarios! Please follow these steps:

1.  **Fork the Repository**: click "Fork" on GitHub and clone your fork locally.
2.  **Create a New Branch**: `git checkout -b add-new-question`
3.  **Choose the Domain and Level**: Decide if your question fits into `devops`, `sre`, or `k8s`, and select the appropriate difficulty (`beginner`, `advance`, `expert`).
4.  **Create the File**: Create a new `.md` file in the correct directory.
    *   Example: `content/sre/advance/memory-leak-debugging.md`
5.  **Use the Template**: Copy the following frontmatter and structure into your file:

    ```markdown
    ---
    title: "Descriptive Title of the Question"
    date: 2023-10-27T10:00:00+00:00
    draft: false
    weight: 10  # Optional: higher numbers appear lower in the list
    description: "A one-sentence summary of the scenario."
    ---

    ### Scenario
    Describe the real-world situation. For example: "A Kubernetes pod is constantly restarting with OOMKilled status..."

    ### Question
    State the interview question clearly. "How would you debug this issue and what are the potential fixes?"

    ### Expected Answer
    Provide a structured answer with key points to look for:
    1.  **Analysis**: Step 1...
    2.  **Solution**: Step 2...
    3.  **Optimization**: Step 3...
    ```

6.  **Verify**: Run `npm run dev` locally and verify your question appears correctly in the list and detailed view.
7.  **Submit a Pull Request**: Push your branch and open a PR with a clear description of your addition.

## Style Guidelines

*   **Tone**: Professional, encouraging, and technically accurate.
*   **Formatting**: Use standard Markdown. Use code blocks for commands and logs.
*   **Images**: If you need to add diagrams, place them in `assets/images/` and verify they load correctly.

## Reporting Issues

If you find a bug or incorrect information, please search existing issues first. If none exist, open a new issue with:
*   Clear title
*   Description of the issue
*   Steps to reproduce (if applicable)

## License
By contributing, you agree that your contributions will be licensed under the project's [License](LICENSE).
