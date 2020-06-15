<h1>DevOps-Task1</h1>
<h2>Objective:</h2>

Setup up infrastructure, for the three team's or environemnts :

1.Production

2.Testing

3.Quality Assurance Team

Production Team will deploy the code first.
And with the work going on in the developement team, the code will be deployed on the testing environment, which will be then tested by the QA team and only after their approval the code will get deployed on the production environment. 

<h2>Requirements:</h2>

1.Knowledge of Docker Containers.

2.Jenkins.

3.Git & Github.

4.Networking.


<h2>My Project:</h2>

I have made 3 jobs each for production, testing and Quality Assurance Team.

<h2>#Job-1</h2>

If Developer push  to dev1(feature) branch then Jenkins will fetch from dev1 and and deploy it on dev1-docker environment.

![job1](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/job1.png)
![job1](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/job1.1.png)

<ul>
  <li> -p 8089:80 This exposes the port no. 8089 of particular image to make it accessible from outside world. </li>
  <li> -v /root/testtask/: This shows that an outside volume is attached to destination folder of particular container.
</ul>
Whenever any new commit occurs in dev1 branch, it downloads the code and deploy in this container image. And testing is done on this     server only. Only if this code is properly working then only it will be deployed on master server.

<h2>#Job-2</h2>

If Developer push to master branch then Jenkins will fetch from master and deploy it on master-docker environment.

![job2](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/job2.png)
![job2](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/job2.1.png)

<ul>
  <li> -p 8088:80 This exposes the port no. 8088 of particular image to make it accessible from outside world. </li>
  <li> -v /root/prodtask/: This shows that an outside volume is attached to destination folder of particular container.
</ul>
Whenever any new commit occurs in master branch, it downloads the code and deploy in this container image.

Both dev1-docker and master-docker environment are launched on different docker containers.

<h2>#Job-3</h2>

It is an Upstream job which will manually check (test) for the website running in dev1-docker environment. If it is running fine then Jenkins will merge the dev1 branch to master branch.
The above two mentioned job will work as the downstream for this job.

![job3](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/job3.png)
![job3](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/job3.1.png)

 <h2>Before the Job3:-</h2>
 
  We have the same code in both the dev1(feature) and master branch.
  
  Master:-
  ![before](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/before.png)
  
  Dev1:-
  ![before](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/before.1.png)
  
  <h3>Updating the code in Dev1 branch:-</h3>
  
  ![update](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/before.2.png)
  
  
  <h2>After successfull execution of Job3:-(upstream job)</h2>
  
  We'll have the merged data:-
  
  ![after](https://raw.githubusercontent.com/gauravsjc02/DevOps-Task1/master/task1/after.png)
