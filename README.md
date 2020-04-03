# ENE (ENE's Not Excel)

Webpage to serve UFSC's classes approval/failure rate from CSV files.

## Setup
1. Install elm by using the [official guide](https://guide.elm-lang.org/install.html).
2. Compile Elm with the time-travelling debugger by using
`elm-make Main.elm --output index.html --debug`
or use `elm-reactor` and visit `http://localhost:8000`

Due to external CSS i recommend using [`elm-live`](https://github.com/wking-io/elm-live) during development.

## Maintaining this website
1. Request data in CSV format from [e-SIC](https://esic.cgu.gov.br/).
2. Run `convert.sh` in the obtained CSV files (do not run twice)(or use online tools).
3. Commit them to the csv folder.
4. If you are adding a new course, create a folder (`ene/csv/<course code>`) and update the `availableCourses` function in [`Data.elm`](https://github.com/caravelahc/ene/blob/master/src/Data.elm).

## GitLab Deploy
This project uses GitLab CI to deploy to GitHub Pages, the following variables need to be set in the [CI configuration panel](https://gitlab.com/caravelahc/ene/-/settings/ci_cd).
Ensure that the pipelines are using `clone` as the git strategy instead of `fetch`.

Variable|Description
|-|-|
REMOTE_URL|Used to set the remote to be pushed inside the CI, must use this format: `https://<deploy-bot-name>:<deploy-account-access-token>@github.com/caravelahc/ene.git`
DEPLOY_USERNAME|GitHub username for the deploy commit.
DEPLOY_EMAIL|GitHub account email for the deploy commit

### Thanks
- [@matheusmk3](https://github.com/MatheusMK3) for the CSS files
- [@tarcisioe](https://github.com/tarcisioe/) for the `convert.sh` script
