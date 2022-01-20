# commitizen-deno

Commitizen client powered by Deno and FZF

## Requirements

- Deno
- FZF

## Configuration


```yaml
# ~/.config/commitizen-deno/.git-czrc
message:
  items:
    - name: type
      description: Select the type of change that you're committing
      required: true
      form: select
      options:
        - name: feat
          description: A new feature
        - name: fix
          description: A bug fix
        - name: docs
          description: Documentation only changes
        - name: style
          description: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
        - name: refactor
          description: A code change that neither fixes a bug nor adds a feature
        - name: perf
          description: A code change that improves performance
        - name: test
          description: Adding missing tests or correcting existing tests
        - name: build
          description: "Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)"
        - name: ci
          description: "Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)"
        - name: chore
          description: Other changes that don't modify src or test files
        - name: revert
          description: Reverts a previous commit

    - name: scope
      description: What is the scope of this change (e.g. component or file name)
      form: input

    - name: subject
      description: Write a short, imperative tense description of the change
      required: true
      form: input

    - name: body
      description: Provide a longer description of the change
      form: input

    - name: breakingChange
      description: Describe the breaking changes if exist
      form: input

    - name: issue
      description: 'Add issue references (e.g. "fix #123", "re #123".)'
      form: input

  template: "<%- type %><% if (scope) { %>(<%- scope %>)<% } %>: <%- subject %><% if (body) { %>\n\n<%- body %><% } %><% if (breakingChange) { %>\n\nBREAKING CHANGE: <%- breakingChange %><% } %><% if (issue) { %>\n\n<%- issue %><% } %>"
```