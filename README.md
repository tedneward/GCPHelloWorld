# GCPHelloWorld

Simplest Google Cloud Platform application

## Requirements
* OpenJDK 8
* [Gradle](https://gradle.org)
* [Google Cloud SDK](https://cloud.google.com/sdk/)
* `gcloud components install app-engine-java`
* `gcloud components update`

## Setup

If you have not yet already created a project, do so ('helloworld').
This can be done either in the browser (Google Cloud Platform Console),
or at the command-line using `gcloud projects create [project-name]`.

Then do a `gcloud init`. This will establish a configuration (which is
an account/project/region/etc tuple) that is used for subsequent actions.
This will also ask if you want an API enabled; answer yes.

Then do a `gcloud app create`. This will create an AppEngine application
within this project. It will ask you a region to use; use the one that's
physically closest to your location (unless you have particular reason to
use something different).

Then do a `gcloud auth application-default login`. This is the moment
where Google Cloud Platform authenticates you against the account for
which this application was defined. It will pop a browser window and do
the OAuth dance to authenticate you against your Google account. Failing
to do this will yield permission errors during deploy.

Lastly, you could do a `gcloud app deploy src/main/appengine/app.yml`. 
This will use the AppEngine YAML file to deploy the current application
code to the cloud--however, it probably isn't built yet. On top of which,
it would be better to do this as part of the build. Fortunately, we have
Gradle.

## Step 1: Yup, it's just a servlet

Have a look in src/main/java/com/newardassociates/demo/HelloServlet.java.

Yup, it's just a plain ol' servlet. Nothing to see here.

(Alternatively, if what you see here doesn't make sense to you, you probably
wanted to do the NodeJS tutorial down the hall. Or something.)

## Step 2: Build it locally

Verify it works locally by using `gradle jettyRun`. This will start Jetty
on port 8080 (which means, of course, nothing else can be running on that
port--if you have Tomcat installed, since that's the default port for
development instances of Tomcat, make sure Tomcat is shut down).

You could also just build the WAR (`gradle war`) and deploy that to your
application server container of choice, just to prove that it's nothing
more than a standard Java web archive.

## Step 3: To the cloud!

Push it to the cloud with `gradle appengineDeploy`. The first time this is done,
it will take a while--sometimes up to ten minutes. Be patient.




## Gradle

[Using Gradle and the App Engine Plugin](https://cloud.google.com/appengine/docs/flexible/java/using-gradle) 
& [Gradle Tasks and Parameters](https://cloud.google.com/appengine/docs/flexible/java/gradle-reference)

### Running locally

    $ gradle jettyRun

### Deploying

    $ gradle appengineDeploy

Note that deploying for the first time can take as much as ten minutes to complete. I
don't know of any way to make this go faster.

