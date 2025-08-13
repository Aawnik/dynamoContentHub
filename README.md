# dynamoContentHub
### TechStack
- UI__Angular
- Middleware__Node/Express
- Database__MongoDb


### WorkFlow
> 01_Initialize project directory. Install Node.js. Install and configure VS Code with recommended extensions (ESLint, Prettier). Initialize a Git repository.
### purpose of `**vscode/extensions.json**`..?
- it automates & standardizes the devEnv for entire team.
- it tells the devs which extensions to install, which reduces the onBoarding friction and ensures every team member has same tools for linting, formating & debugging.
- this keeps the projects tooling requirements directly to the repo. Thus, reducing the "it works on my machine" issues related to the editor conf.

### We ignored the entire `.vscode/` directory in `.gitignore` but then committed `.vscode/extensions.json`. Explain the reasoning behind this decision.
- `vscode/` directory can contain user-specific workspace settings, like color themes, font sizes, or panel layouts. However this is personal for every dev. so, ignored..
- `extensions.json`, defines the **project's standard tooling**, which *should* be consistent for everyone

### purpose of `npm init -y`? What does the `-y` flag do and when should you *not* use it?
- `npm init` is to create a `package.json` file, which lists metadata, dependencies, and scripts.
- `-y` flag stands for "yes," and it automatically accepts all the default prompts from `npm init`.
- While creating the library or public project we should not use `-y`. Here, we should go through the prompts carefully to provide a meaningful name, description, keywords, license, and repository URL, as this metadata is crucial for other developers to discover and use your package.
  
### A team member suggests adding a `formatOnSave` setting to the project's shared VS Code settings. You argue against it. What is your reasoning and what is the superior alternative?
- `formatOnSave` is an anti-pattern as it leads to **polluted commits**. A developer might change one logical line, and saving the file will reformat hundreds of other lines which would mess the whole code.
- The superior architectural solution is to use a **`pre-commit` hook** with a tool like Husky and `lint-staged`. which automatically formats *only the changed files being staged for the commit*. This enforces style consistency for the code entering the repository without polluting the Git history, keeping commits small, focused, and easy to review."

### What is the difference between `npm install <package>` and `npm install --save-dev <package>` and why is this distinction critical for a production system?
- `npm install <package>` || `npm i -S`, adds the package to the `dependencies` list in `package.
  - These are packages required for the application to *run* in production
- `npm install --save-dev <package>`|| `npm i -D`, adds it to `devDependencies`. These are packages only needed for the *development* process (e.g., ESLint, Prettier, testing libraries)
- When deploying to production, you run `npm install --production`, which **only** installs `dependencies`. This creates a smaller, faster, and more secure production build by excluding all the unnecessary development tools.





