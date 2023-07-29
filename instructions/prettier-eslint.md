# Install Prettier

npm install --save-dev prettier

# Configuration

The next step is to configure Prettier. Prettier uses cosmiconfig to find and load configuration files under your project, here we’ll create a .prettierrc.json file with basic configuration under the root directory. You can refer to the document to get more details about configuration.

{
"trailingComma": "all",
"tabWidth": 2,
"singleQuote": true,
"jsxBracketSameLine": true
}

# Use ESLint to handle code quality and use Prettier to handle code formatting.The problem can be solved by turning off some part of rules in ESLint using eslint-config-prettier.

npm install --save-dev eslint-config-prettier

# Choose the default formatter.

Press Ctrl+Shift+P(Win) or Cmd+Shift+P(Mac)
Type Format Document With...
Then click Configure Default Formatter... and choose it from the list.
