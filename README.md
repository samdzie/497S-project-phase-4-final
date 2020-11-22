# Team Vision: Project Phase 4 Final

## Overview
Our project is a web application for organizing communities. Our vision
is to combine the features of a home webpage with those of a shared
online calendar. The goal is to allow groups of people - whether they
be friend groups, clubs, or organizations - to have an easy-to-use tool
for organizing events.

This project was developed for [CS 497S: Scalable Web Systems][1],
taught by Professor Tim Richards at UMass Amherst in Fall 2020.

## Team Members
- Hichem Bennia
- Sam Dziewietin
- Achintya Kumar
- Angela Nayiga
- Zenry Padua

## System Design
The system is divided into four microservices:

- Web UI: A web app for displaying a group's homepage and calendar.
- Homepages: Manages information displayed on a group's homepage (e.g
group name, welcome message).
- Events: Manages the events displayed on each group's calendar.
- Images: Manages images used by the system, especially group icons.

The Web UI service consists of a frontend and a backend, while the other
services consist of a database and RESTful API. The Web UI frontend
requests data from the backend, which in turn makes API calls over HTTP
to the other services to obtain the necessary data.

Each service is built into a Docker image (or several with
docker-compose). These images are then deployed to AWS Elastic
Beanstalk (EB).

## Scalability
Most of our scalability considerations are taken from recommendations
given in Sam Newman's *Building Microservices*.

Our first major step towards addressing scalability concerns is by
establishing service boundaries such that each team member develops,
tests, and deploys their own microservice. This allows each team member
to select the technology that best fits their needs and also allows
each service to be scaled independently of the others (e.g. by
deploying more instances).

Our method of deployment is to build Docker images and deploy them on
Elastic Beanstalk. This approach significantly reduces the time and
effort required for deployment and allows us to rapidly expand the
number of server instances, if necessary.

As demonstrated in the Web UI service, we are developing the ability to
employ continuous integration (CI) and continuous delivery (CD) to
significantly speed up the development and release processes. GitHub
Actions allows us to run a CI workflow on each push, using pytest to
run unit and service tests. GitHub Actions also permits us to
automatically deploy our services to Elastic Beanstalk when a new
release is created.

## Repositories
- [Web UI][2]
- [Homepages][3]
- [Events][4]
- [Images][5]
- [Voice Assistant][6]

## Demo Videos
- Web UI
- Homepages
- [Events][9]
- Images
- Voice Assistant
- Entire System


[1]: https://sites.google.com/cs.umass.edu/compsci-497s-f20-submissions
[2]: https://github.com/samdzie/group-web-ui
[3]: https://github.com/HichBen/homepage-app
[4]: https://github.com/zenpadua/497S-events-microservice
[5]: https://github.com/Angela-N/image-microservice
[6]: https://github.com/achintyaakumar/voice-microservice
[9]: https://youtu.be/C6oZpZvJpX8
