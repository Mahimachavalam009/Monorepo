# Monorepo
Monorepo explained

# What is a Monorepo?
A monorepo is a single repository containing multiple distinct projects, with well-defined relationships.

![image](https://github.com/user-attachments/assets/0356be47-93db-44b8-9fd4-32105bba7a03)

# Not just “code colocation”


Consider a repository with several projects in it. We definitely have “code colocation”, but if there are no well defined relationships among them, we would not call it a monorepo.
Likewise, if a repository contains a massive application without division and encapsulation of discrete parts, it's just a big repo. You can give it a fancy name like "garganturepo," but we're sorry to say, it's not a monorepo.
In fact, such a repo is prohibitively monolithic, which is often the first thing that comes to mind when people think of monorepos. Keep reading, and you'll see that a good monorepo is the opposite of monolithic.

![image](https://github.com/user-attachments/assets/58b58478-0e82-4379-88e4-887d66593106)

![image](https://github.com/user-attachments/assets/09b20ced-4add-4dc3-ae8d-1768d9885375)

# A “Polyrepo”
For the sake of this discussion, let's say the opposite of monorepo is a "polyrepo". A polyrepo is the current standard way of developing applications: a repo for each team, application, or project. And it's common that each repo has a single build artifact, and simple build pipeline.

![image](https://github.com/user-attachments/assets/491e4d95-bf53-46d7-89d0-0247eb81cf73)

The industry has moved to the polyrepo way of doing things for one big reason: team autonomy. Teams want to make their own decisions about what libraries they'll use, when they'll deploy their apps or libraries, and who can contribute to or use their code.
![image](https://github.com/user-attachments/assets/e9372eda-503f-4091-8cd5-d031fa0c7bf6)

Those are all good things, so why should teams do anything differently? Because this autonomy is provided by isolation, and isolation harms collaboration. More specifically, these are common drawbacks to a polyrepo environment:
```
Cumbersome code sharing : To share code across repositories, you'd likely create a repository for the shared code. Now you have to set up the tooling and CI environment, add committers to the repo, and set up package publishing so other repos can depend on it. And let's not get started on reconciling incompatible versions of third party libraries across repositories...


```
