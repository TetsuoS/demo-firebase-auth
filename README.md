Local: GCP Cloud > CloudShell > Project: mymarkdown-ceo
https://console.cloud.google.com/home/dashboard?project=mymarkdown-ceo&folder=&organizationId=
cd /home/administrator/python-docs-samples/appengine/standard/firebase/firenotes

https://cloud.google.com/appengine/docs/standard/python/authenticating-users-firebase-appengine#adding_the_firebase_authentication_user_interface

https://console.firebase.google.com/project/mymarkdown-ceo/overview?hl=ja

https://www.youtube.com/watch?v=iEOVRzAwwzU&feature=youtu.be





# Firenotes: Firebase Authentication on Google App Engine

[![Open in Cloud Shell][shell_img]][shell_link]

[shell_img]: http://gstatic.com/cloudssh/images/open-btn.png
[shell_link]: https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/python-docs-samples&page=editor&open_in_editor=appengine/standard/firebase/firenotes/README.md

A simple note-taking application that stores users' notes in their own personal
notebooks separated by a unique user ID generated by Firebase. Uses Firebase
Authentication, Google App Engine, and Google Cloud Datastore.

This sample is used on the following documentation page:

[https://cloud.google.com/appengine/docs/python/authenticating-users-firebase-appengine/](https://cloud.google.com/appengine/docs/python/authenticating-users-firebase-appengine/)

You'll need to have [Python 2.7](https://www.python.org/) and the [Google Cloud SDK](https://cloud.google.com/sdk/?hl=en)
installed and initialized to an App Engine project before running the code in
this sample.

## Setup

1. Clone this repo:

        git clone https://github.com/GoogleCloudPlatform/python-docs-samples.git

1. Navigate to the directory that contains the sample code:

        cd python-docs-samples/appengine/standard/firebase/firenotes

1. Within a virtualenv, install the dependencies to the backend service:

        pip install -r requirements.txt -t lib

1. [Add Firebase to your app.](https://firebase.google.com/docs/web/setup#add_firebase_to_your_app)
1. Add your Firebase project ID to the backend’s `app.yaml` file as an
environment variable.
1. Select which providers you want to enable. Delete the providers from
`main.js` that you do no want to offer. Enable the providers you chose to keep
in the Firebase console under **Auth** > **Sign-in Method** >
**Sign-in providers**.
1. In the Firebase console, under **OAuth redirect domains**, click
**Add Domain** and enter the domain of your app on App Engine:
[PROJECT_ID].appspot.com. Do not include "http://" before the domain name.

## Run Locally
1. Add the backend host URL to `main.js`: http://localhost:8081.
1. Navigate to the root directory of the application and start the development
server with the following command:

        dev_appserver.py frontend/app.yaml backend/app.yaml

1. Visit [http://locahost:8080/](http://locahost:8080/) in a web browser.

## Deploy
1. Change the backend host URL in `main.js` to
https://backend-dot-[PROJECT_ID].appspot.com.
1. Deploy the application using the Cloud SDK command-line interface:

        gcloud app deploy backend/index.yaml frontend/app.yaml backend/app.yaml

    The Cloud Datastore indexes can take a while to update, so the application
    might not be fully functional immediately after deployment.

1. View the application live at https://[PROJECT_ID].appspot.com.
