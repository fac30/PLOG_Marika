## Guidance
Answer the following questions considering the learning outcomes for
- [Week 011](https://learn.foundersandcoders.com/course/syllabus/developer/week11-project05-DOTNET-testing/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment
 ### 1. Show evidence of some of the learning outcomes you have achieved this week.
### Learned Figma from Scratch
This week, I learned how to use Figma to create a prototype for the "Tech for Better" project.
Together with my colleague, we successfully delivered responsive designs for desktop, tablet, and mobile.
Breaking down different parts of the page into reusable components (following a React mindset) helped me stay focused and facilitated learning as I worked.

##### Researching how to incorporate accessibility into our design became a primary focus for our website.
We investigated color contrast, typography readability, and general accessibility principles, aligning our choices with WCAG standards.
For example, we implemented a high-contrast color palette between the background and text and selected accessible fonts, such as Roboto and Poppins, to support usability for all users.

##### We also discussed how to proceed with building the website and identified some key rules to follow:
- Create reusable components and page templates to streamline future updates.
- Add visual cues like banners and event images to encourage interaction and social connection.
- Use existing plugins instead of building custom ones to save time and maintain efficiency.


### Docker workshop
I started learning about Docker's architecture. I explored how the Docker Engine, Daemon, Client, Registry, Images, and Containers all work together. One of the big takeaways for me was understanding how Docker uses file system layers and how the client communicates with the daemon to manage containers.

1- How containers manage data using the following methods: 
- Writable Layers
- tmpfs
- Bind Mounts
- Volumes

```
docker network create my_bridge
docker run --network=my_bridge -p 8080:80 nginx
```

2- Understand how containers communicate internally and externally. Key concepts:
- Bridge Networking: Used for communication between containers on the same network.
- Host Networking: Shared the host’s network stack with containers but reduced isolation.
- Publishing Ports: Allowed services within containers to be accessible externally.

3 - Learned to manage multi-container applications using Docker Compose. I wrote my first YAML file.
 ```
version: "3"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  database:
    image: postgres
    volumes:
      - db_data:/var/lib/postgresql/data
volumes:
  db_data:
```

4- Working with Docker Hub
Practiced pulling, tagging, and pushing images to Docker Hub.

```
docker pull nginx
docker tag nginx:latest myrepo/nginx:custom
docker push myrepo/nginx:custom
```


 ### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.
> [**Learning outcome...**]  
> [your evidence here]

## Feedback (For CF's)
> [**Course Facilitator name**]

Alexander

> [*What went well*]  

Well done on learning Figma, it can be quite frustrating at the beggining, but it is a very useful tool. I am also very happy to see that you are spending time learning Docker. You will need it in your working place so the more you learn now, the better

