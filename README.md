# three-tier-application-collegecourse
USED THIS PROJECT FOR APLLYING WEBHOOK CONCEPT
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Step 1 : Install the plugin

Install the "Github Integration" plugin in the jenkins.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Step 2 : Build the project in jenkins

Copy the url of the github project and create a new job in the jenkins

Enable the github project option and choose git in the scm and provide the necessary details.

Finally, enable the github hook trigger for gitscm polling and save the job.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Step 3 : Generate jenkins token

Click on the user and then go to configure.

Generate a token there by giving a name and copy it. This token will be used as secret password in github webhook.

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Step 4 : Create a webhook for that project in github

Inside the project, go to settings, click on webhook and create a new webhook by giving AddWebhook.

Paste your token in the secret section and select the content type.

In the payload url, yu have to give the jenkins server url.

[If your jenkins is running on the localhost, yu cant give the url as such. Because GitHub would not know how to contact "localhost" or 127.0.0.1: what GitHub would consider "local" is not your local machine.]

[That means your PC must expose to the internet the port 8080.]

[If you want to try to run Jenkins on localhost, the other way around is that, install ngrok which expose localhost urls over internet.]

[After installation of the ngrok run ngrok http 8080. It will give you a url like this: http://3b2db437.ngrok.io]

Now under payloadUrl type the url as:  http://3b2db437.ngrok.io/github-webhook/  and give AddWebhook.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Step 5 : Check whether the webhook is working fine

When yu click on webhook option, if the webhook has a green tick, it means our webhook is configured properly.

After this, commit and push changes into our repo.

After pushing changes into your branch, go to Jenkins dashboard check the build. The build automatically gets triggered (After each and every commit).







