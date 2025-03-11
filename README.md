# AutoCoder

AutoCoder is an automated code generation tool designed to speed up the software development process by generating boilerplate code, templates, and other repetitive structures based on issues and predefined patterns.

## Features 
* Code Templates: Jumpstart your projects with a variety of language-specific templates;
* Customizable Generation: Tailor the generated code to your specific needs by specifying your prompt as a
GitHub Issue;
*  Integration Support: Works as part of your CI/CD pipeline using workflows with GitHub Actions;

## Using the AutoCoder Composite Action

To use this action, set up a `.github/workflows/main.yml` file in your repository like that below


name: AutoCodeGen
on:
  issues:
    types: [labeled]

jobs:
  generate_code:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: AutoCoder Composite Action
        uses: your-username/autocoder-action@v1
        with:
          github_token: \{{ secrets.GITHUB_TOKEN }}
          openai_api_key: $\{{ secrets.OPENAI_API_KEY }}
          issue_label: 'autocoder'

Make sure to replace `your-username` with your GitHub username and `autocoder-action` with the name of your repository. This configuration will invoke the AutoCoder action when an issue is labeled with the specified label.