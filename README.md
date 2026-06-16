## express app

Instructions

Create now a similar deployment pipeline for a simple Node.js/Express app found here(opens in a new tab).

Either clone the project or copy the files to your own repository. Set up a similar deployment pipeline (or the "first half") using GitHub Actions that was just described. Ensure that a new image gets pushed to Docker Hub every time you push the code to GitHub (you may e.g. change the message the app shows).


name: Release Node.js app

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      # ...
Some of the actions that the above example uses can be already outdated, so go through the documentation

actions/checkout(opens in a new tab)
docker/login-action(opens in a new tab)
docker/build-push-action(opens in a new tab)
docker/setup-buildx-action(opens in a new tab)
and use the most recent versions in your workflow.

Keep an eye on the GitHub Actions page to see that your workflow is working:

Add alt
Ensure also from Docker Hub that your image gets pushed there.

Next, run your image locally in detached mode, and ensure that you can access it with the browser.

If you use M1/M2 Mac, the image built by GitHub Action might cause problems in your machine due to different processor architecture. One way to get around this is to build a Multi-platform image, see here(opens in a new tab) for more!

Now set up and run the Watchtower(opens in a new tab) just as described above.

Now your deployment pipeline is set up! Ensure that it works:

make a change to your code
commit and push the changes to GitHub
wait for some time (the time it takes for GitHub Action to build and push the image plus the Watchtower poll interval)
reload the browser to ensure that Watchtower has started the new version (that is, your changes are visible)
Extend the docker-compose.yaml to start up both the Watchtower and the Express app.

Submit a link to the repository with the configurations.

Access with browser http://localhost:8080
# Docker-course-part3
