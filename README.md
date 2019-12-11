# GitHub actions

## Deploy to Heroku
  - heroku login
  - heroku authorizations:create
  - copy the token and store it at a secret in GitHub (HEROKU_API_TOKEN)
  - update the action config file
    ```
      name: Deploy to Heroku
      on: [push]
      jobs:
        build:
          runs-on: ubuntu-latest
          steps:
          - uses: actions/checkout@v1
          - name: Deploy to Heroku
            env:
              HEROKU_API_TOKEN: ${{ secrets.HEROKU_API_TOKEN }}
              HEROKU_APP_NAME: "your-app-name-here"
            run: git push https://heroku:$HEROKU_API_TOKEN@git.heroku.com/$HEROKU_APP_NAME.git origin/master:master
    ```
