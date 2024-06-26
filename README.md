# How to install Docker

Execute these steps in the command line interface:

1. sudo apt update
2. sudo apt install docker docker-compose -y
3. sudo systemctl start docker
4. sudo usermod -a -G docker $USER
5. newgrp docker
6. cd ~/ros2_ws/src
7. git clone https://github.com/Combuster54/ros2_ci
8. cd ros2_ci

Verify if you can use the docker environment:

```console
user:~/ros2_ws/src/ros2_ci$ docker ps
```

# How to run Jenkins

```console
cd ~/ros2_ws/src/ros2_ci/
./start_jenkins.sh
```

You should see something like that in the snippet below. Copy the administrator password.

```console


Jenkins initial setup is required. An admin user has been created and a password generated.
Please use the following password to proceed to installation:

6bc8bd642b5XXXXXXXc864d1efa290e9

This may also be found at: /home/user/webpage_ws/jenkins/secrets/initialAdminPassword

```

Run the following to get the Jenkins URL. Copy the URL and enter it in the web browser. You should have access to the Jenkins web interface.

```console
user:~/ros2_ws/src/ros2_ci$ cat /home/user/jenkins__pid__url.txt
To stop Jenkins, run:
kill 182094

Jenkins URL:
https://i-01c4346b3ec554017.robotigniteacademy.com/bd501c55-30fe-471c-a290-0b6955964062/jenkins/
```

# How to create the first Jenkins job

Perform these steps in the Jenkins web interface:

1. Enter the administrator password and press the Continue button
2. Press "Install suggested plugins" and wait a while
3. Press "Skip and continue as admin"
4. Press "Not now"
5. Press "Start using Jenkins"

Congrats! Now, you can add the Jenkins jobs and do amazing things. Let's go! Perform these steps in the Jenkins web interface:

1. Press "New Item"
2. Enter the name, eg. "ROS2 Pipeline"
3. Choose "Pipeline"
4. Press the "OK" button
5. Enter the description
6. In the Pipeline section, change the Definition to "Pipeline script from SCM"
7. In the same section, change the SCM to "Git"
8. Paste "https://github.com/Combuster54/ros2_ci.git" into "Repository URL"
9. Change "Branch Specifier (blank for 'any')" to "main"
10. Press the "Save" button
11. Press the "Build Now" option from the left menu

Now, you have to wait for a while until the job executes all the steps.

# How to push changes into the repository

Now, you can change something in the code. For example, you can use something like this:

```console
user:~/ros2_ws/src/ros2_ci$ echo "ros2_jenkins" > test_file.txt
```

Execute these steps in the command line interface:

1. git add .
2. git commit -m "changing test_file.txt"
3. git push

After these steps, Jenkins should automatically execute the added previous job and verify our new changes.
