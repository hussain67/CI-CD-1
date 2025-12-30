# Folders

     .github/workflows

# File; Name can be chosen

      test.yml

# Name

     name: Test Project

# Trigger

    on:push

# jobs:

# steps

# action/Run

      name:Test Project
      on:push
      jobs:
         test:
            runs-on: ubuntu-latest
            steps:
               -  name: Get Code.
                  uses: actions/checkout@v3
               -  name: Install NodeJS
                  uses: actions/setup-node@v3
                  with:
                     node-version: 18
               -  name: Install dependencies
                  run:  npm ci
               - name:  Run tests
                 run:   npm test

<!--
name: Deployment Exercise 1
on: push
jobs:
  deployment:
    runs-on: ubuntu-latest
    steps:
      - name: Get Code
        uses: actions/checkout@v3
      - name: Install dependencies
        run: npm ci
      - name: Lint
        run: npm run lint
      - name: Test Code
        run: npm run test
      - name: Build Code
        run: npm run build
      - name: Deploy Code
        run: echo " Deploying..."

 -->
