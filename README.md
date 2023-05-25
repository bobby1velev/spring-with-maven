1. Fork this repository: https://github.com/stoenpav/spring-with-maven - 5
2. Create a new Pipeline Job in Jenkins - 5
3. Write a declarative pipeline inside which:
   1. Runs on a static slave - 5
   2. Uses the appropriate tools - 7
   3. Create a stage to clone the repository - 5
   4. Create a stage to <b>Build</b> the application using <b>mvn clean install</b> - 7
   5. Create a stage to <b>Test</b> the application using <b>mvn test</b> - 7
   6. Create a stage which builds and tags a docker image - 6
   7. Create a stage which pushes the docker image - 6
   8. Create a stage which deploys the docker image - 7
   9. Create a post block which cleans the workspace after the pipeline finishes - 5
4. Store the pipeline in a Jenkinsfile and push it to your forked repo - 5
5. Create an integration between Jenkins and Github and add the appropriate block in the Jenkinsfile in order to work - 10

<h3>PASS >= 60</h3>

Upon completion send me, in slack, your repository with the Jenkinsfile and a proof that you have a working integration by going to the Polling Log and screenshot of the first two lines like:

<h3>Started on May 23, 2023, 1:43:22 PM
Started by event from 172.17.0.4 ⇒ http://localhost:8080/github-webhook/ on Tue May 23 13:43:22 UTC 2023</h3>

You have 1 hour. ChatGPT is forbidden, Google is not. Good Luck ! :)

changing readme to start autopush


