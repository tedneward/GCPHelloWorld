# GCPHelloWorld

Simplest Google Cloud Platform application

## Requirements
* OpenJDK 8
* [Gradle](https://gradle.org)
* [Google Cloud SDK](https://cloud.google.com/sdk/)
* `gcloud components install app-engine-java`
* `gcloud components update`

## Setup

Use either:

* `gcloud init`
* `gcloud auth application-default login`

If you have not yet already created a project, do so ('helloworld').
This can be done either in the browser (Google Cloud Platform Console),
or at the command-line using `gcloud projects create [project-name]`.

## Gradle
[Using Gradle and the App Engine Plugin](https://cloud.google.com/appengine/docs/flexible/java/using-gradle) 
& [Gradle Tasks and Parameters](https://cloud.google.com/appengine/docs/flexible/java/gradle-reference)

### Running locally

    $ gradle jettyRun

### Deploying

    $ gradle appengineDeploy

