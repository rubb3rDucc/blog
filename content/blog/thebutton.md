+++
date = '2025-03-28T01:07:53-04:00'
title = 'The Button'
+++

## Why I wanted to build it.

Project Github: https://github.com/rubb3rDucc/button

I wanted to deploy a simple web app on the cloud and expose it to the internet. I also wanted to finish it within a week. 

I have a problem with finishing personal projects. The main issue I saw after looking back on past projects is that I will choose projects with an enormous scope and unclear goals. I then start them, overextend one feature, get bored, and drop it. 

## Goals with it.

The project that fit these initial goals was a program where a user presses a button to increase or decrease a value. Having something so simple helped immensely with how versatile I could implement it. 

I could program a web page using HTML and JavaScript to simplify the implementation and store the values in local storage. The issue is that the count would persist on the user’s browser and not for anyone visiting the site. I had to further refine my user experience goals:

~~I wanted to deploy a simple web app on the cloud and expose it to the internet. I also wanted to finish it within a week.~~

I wanted to deploy a simple web app on the cloud and expose it to the internet. I also wanted to finish it within a week. Users can click a button to increase or decrease a count. All users visiting the web app can view the current count.
 
Now, that I got what the user experience will look like, but what about the developer experience? 

With this project, I wanted to learn more about deploying on the cloud, using docker, and using a CI/CD pipeline. I decided to draw from my experiences working in other codebases and scouring the internet for modern techniques to develop web apps.

- **Develop the web app using TypeScript and PostgreSQL.** I am adept at using both and enjoy developing with them.

- **I used Docker and docker-compose to build and test a containerized version of the web app + database.** I can build and use a version of the codebase in a separate environment. I can use a containerized database to use a fresh version of it every time I wanted to test and not worry about constantly rebuilding my database running locally. It also eliminates the need for maintaining a mock test database. I used the same containerized server + database technique when I built and tested the codebase environment on the CI/CD pipeline in GitHub.

- **Use Google Cloud for cloud deployment to deploy containerized docker containers.** I came to this decision after finishing the program and having a version running with a local build and database and a containerized build and database through Docker. 
 
## Thoughts on Cloud Deployment.

After I had read some of the what's what in cloud deployment, and it sounded interesting, I found that I could deploy a docker container on the cloud and host it. It's definitely more expensive than hosting a build on a VPS as it involves using more of the Cloud Providers services to serve your app, and services made specifically for doing so can be more expensive than using something more straightforward.

For example, hosting a PostgreSQL database on Google Cloud through Cloud SQL is more expensive than hosting it on something aimed at hobbyists or solo devs like Supabase. You can try other major cloud service providers like AWS and Azure, but you find the exact cost issues. There's always hosting it yourself, but you must deal with added electricity costs and handling server issues like crashes and backups. 

Although each approach has positives and negatives, there isn't anything wrong with using any of them. Currently, each service provides enough products and services to deploy a simple web app and database. What I think it comes down to for solo-devs is how much public-facing documentation is there for the cloud service, how easy it is to approach and use, and how much the community supports it. And when I say community support I mean how many times people have ran across issues, posted about them on Stack Overflow or Github, and had them resolved by themselves or others.

I chose Google Cloud because it offered the best documentation and developer experience. The gcloud CLI was easy to use, and the documentation was clear and concise. Although a little outdated, the Cloud Run and Cloud SQL documentation included videos and links to example code on GitHub. 

The final touch that sealed Google Cloud for me was the guided tutorials within its UI. When I opened up the connection between the Cloud SQL instance and the Cloud Run instance, I needed to input PostgreSQL credentials within Cloud Run. I don't remember how it popped up, but there was a guided tour explaining where and how to create the variables to use as credentials. 


## What I Learned From it.

**Choosing a cloud provider is challenging.** Google Cloud was not my first choice. Going off of recommendations from friends and general sentiment from the internet, I started using AWS. I made an account and started reading about the services offered. However, the more I read into it, the more confused I became with how vague AWS's documentation was about implementing the services within projects and what service to use. There were more than 10 ways to run a Docker container on AWS, all at different price points and with varying degrees of quality documentation for each. 

To make sure I was not going crazy, I googled "deploying a docker container to aws" and came across a Reddit post talking about this: https://www.reddit.com/r/aws/comments/1dgsogstrying_to_simply_take_a_docker_image_and_run_it/
One of the commenters also linked to an article confirming my suspicions: https://www.lastweekinaws.com/blog/the-17-ways-to-run-containers-on-aws/. 

Like the original post, I moved on from AWS to find another cloud service provider. Perhaps I'll go back and use AWS. If I have more time to comb through the different ways of deploying to AWS and wading through the documentation to figure out, I could use it again.

**Although there are many ways to deploy an app, there's no best way.** Like developing software, there are a million ways to deploy an app. You can deploy it to a cloud provider, a VPS, or self-host it. What helps determine what deployment method to go with are the constraints on a project, such as time to implement, cost, and service provider support. And if you don't like what you are using for deployment, you can migrate to another provider and try another solution. That's why modularity and code reusability are essential, so it is easy to pack up and leave whenever you need to switch providers and services.

## Conclusion.

It was a great project to complete. For so long, I focused on building something big, like trying AI/ML or building a big generic dating or e-commerce app. I did not want to start any of them because the scope felt intimidating or I wasn't that interested. But focusing on something small and adding complexity to it - that sounded fun.

Also, this project is a great springboard for learning and extensibility. Since this web was so simple, I can focus on implementing the concepts I want to learn like:

- migrate to another cloud service provider for deployment and hosting. I would like to use Digital Ocean or a VPS for the server and Supabase for the database.
- Redo the backend in .Net or Python and connect it to the Cloud SQL DB instance.
- Automate the cloud deployment though a pipeline with OpenTofu, Terraform, or Python.
- Add a mobile front-end and deploy it as another app instance on the Cloud.
- Develop a new front-end with a framework.
- Add a message queue or server sent eventing to show real-time updates for the counter.