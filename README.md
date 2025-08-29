# structura-solution-base-template

This repository provides a standardized base template for initializing new solution repositories, with a focus on React, Next.js, and TypeScript. It is designed for easy adaptation and extension, ensuring consistency, best practices, and security for future solutions.

## Features

- **Consistent Project Structure:** Predefined folders for source code, components, styles, utilities, and types.
- **Dev Container Support:** Includes a ready-to-use [devcontainer](.devcontainer/devcontainer.json) configuration for rapid onboarding and reproducible development environments.
- **CI/CD Ready:** Contains sample [GitHub Actions workflow](.github/workflows/github-actions.yml) and [Azure Pipelines configuration](.azure/azure-pipelines.yml).
- **Comprehensive .gitignore:** Supports Node.js, environment files, and build artifacts.
- **Analysis Tools Configuration:** See [.analisys-tools.yaml](.analisys-tools.yaml) for enabled code quality and security tools.
- **OWASP Security Best Practices:** Secure HTTP headers, environment variable usage, and input validation guidance included.
- **ESLint and Prettier:** Configured for code quality and consistency.
- **Extensible:** Easily update or extend for new frameworks and languages.

## Project Structure

```
structura-solution-base-template/
├── .azure/                # Azure Pipelines and related files
│   └── azure-pipelines.yml
├── .devcontainer/         # Dev container configuration
│   └── devcontainer.json
├── .github/               # GitHub workflows
│   └── workflows/
│       └── github-actions.yml
├── .vscode/               # VSCode settings and launch configs
│   └── launch.json
├── docs/                  # Documentation files
│   └── README.md
├── package-feed/          # Placeholder for package artifacts
├── scripts/               # Placeholder for automation scripts
├── src/                   # Source code
│   ├── pages/             # Next.js pages
│   ├── components/        # React components
│   ├── styles/            # Global and component styles
│   ├── utils/             # Utility functions (e.g., security helpers)
│   └── types/             # TypeScript types
├── tests/                 # Test code
├── public/                # Static assets (e.g., favicon)
├── .analisys-tools.yaml   # Code quality and security tools configuration
├── .editorconfig          # Editor configuration
├── .gitignore             # Comprehensive ignore rules
├── .project_type.yml      # Project type metadata
├── CHANGELOG.md           # Changelog following Keep a Changelog
├── LICENSE                # MIT License
├── next.config.js         # Next.js configuration
├── package.json           # Node.js project configuration
├── tsconfig.json          # TypeScript configuration
└── README.md              # This file
```

## Getting Started

1. **Clone this repository** to use as a starting point for your new solution.
2. **Install dependencies:**
    ```sh
    npm install
    ```
3. **Run the development server:**
    ```sh
    npm run dev
    ```
4. **Open the app in your browser:**
    ```sh
    "$BROWSER" http://localhost:3000
    ```
5. **Update the placeholder files and folders** (`src/pages/`, `src/components/`, etc.) as needed for your project.

## Security Best Practices

- Secure HTTP headers are set via Next.js middleware.
- Use environment variables for secrets and sensitive configuration.
- Input validation and sanitization are recommended using libraries like `validator`.
- Regularly update dependencies and audit for vulnerabilities.
- Follow [OWASP Top 10](https://owasp.org/www-project-top-ten/) guidelines.

## Code Quality & Security

The following tools are enabled via [.analisys-tools.yaml](.analisys-tools.yaml):

- Static analysis: ESLint, Sonar, CodeQL, etc.
- Dependency checks: Snyk, Dependency Check, Trivy
- Test runners: Jest
- Formatting: Prettier
- Others: CLOC, Gitleaks, SEMGRP

## Dev Container

A ready-to-use [devcontainer](.devcontainer/devcontainer.json) is provided for VS Code, supporting Node.js development.

## Contributing

Feel free to fork this template and submit pull requests for improvements or additional stack support.

##
