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

# Cumbersome code sharing: 
To share code across repositories, you'd likely create a repository for the shared code. Now you have to set up the tooling and CI environment, add committers to the repo, and set up package publishing so other repos can depend on it. And let's not get started on reconciling incompatible versions of third party libraries across repositories...

# Significant code duplication:
No one wants to go through the hassle of setting up a shared repo, so teams just write their own implementations of common services and components in each repo. This wastes up-front time, but also increases the burden of maintenance, security, and quality control as the components and services change.
# Costly cross-repo changes to shared libraries and consumers:
Consider a critical bug or breaking change in a shared library: the developer needs to set up their environment to apply the changes across multiple repositories with disconnected revision histories. Not to speak about the coordination effort of versioning and releasing the packages.
# Inconsistent tooling:
Each project uses its own set of commands for running tests, building, serving, linting, deploying, and so forth. Inconsistency creates mental overhead of remembering which commands to use from project to project.


# A “Monorepo”
We can end up in pretty tricky situations when working in a polyrepo. But how can a monorepo help solve all of them?

# No overhead to create new projects
Use the existing CI setup, and no need to publish versioned packages if all consumers are in the same repo.

# Atomic commits across projects
Everything works together at every commit. There's no such thing as a breaking change when you fix everything in the same commit.
# One version of everything
No need to worry about incompatibilities because of projects depending on conflicting versions of third party libraries.
# Developer mobility
Get a consistent way of building and testing applications written using different tools and technologies. Developers can confidently contribute to other teams’ applications and verify that their changes are safe.

![image](https://github.com/user-attachments/assets/9ebe1d32-b28f-4ad8-85c9-f11aeb669fc1)

# Monorepo Feautures :

# 1) Local computation caching
The ability to store and replay file and process output of tasks. On the same machine, you will never build or test the same thing twice.

![image](https://github.com/user-attachments/assets/fd1bfa9a-143d-4f39-b2fe-24967a4b5d24)

# 2) Local task orchestration
The ability to run tasks in the correct order and in parallel. All the listed tools can do it in about the same way, except Lerna, which is more limited.

![image](https://github.com/user-attachments/assets/b14a29fb-67a8-4956-a090-ae20b4092a71)

# 3) Distributed computation caching
The ability to share cache artifacts across different environments. This means that your whole organisation, including CI agents, will never build or test the same thing twice.

![image](https://github.com/user-attachments/assets/73601def-f83b-4ee9-b062-43b2b1e86e6d)

# 4) Distributed task execution
The ability to distribute a command across many machines, while largely preserving the dev ergonomics of running it on a single machine.

![image](https://github.com/user-attachments/assets/ff668173-11b7-43b8-9170-1cd627919caa)

# 5) Transparent remote execution

The ability to execute any command on multiple machines while developing locally.

# 6) Detecting affected projects/packages

Determine what might be affected by a change, to run only build/test affected projects.

![image](https://github.com/user-attachments/assets/e7a3f364-7402-42c8-93f1-ef5736a59a02)

# 7) Workspace analysis

The ability to understand the project graph of the workspace without extra configuration.

![image](https://github.com/user-attachments/assets/c4c7e707-8ae5-414d-a015-cb061df2fa16)

# 8) Dependency graph visualization

Visualize dependency relationships between projects and/or tasks. The visualization is interactive meaning you are able to search, filter, hide, focus/highlight & query the nodes in the graph.

# 9)Source code sharing

Facilitates sharing of discrete pieces of source code.

![image](https://github.com/user-attachments/assets/95d3d33a-c644-4651-9211-4c4ef871f832)

# 10)Consistent tooling

The tool helps you get a consistent experience regardless of what you use to develop your projects: different JavaScript frameworks, Go, Rust, Java, etc.
In other words, the tool treats different technologies the same way.

For instance, the tool can analyze package.json and JS/TS files to figure out JS project deps, and how to build and test them. But it will analyze Cargo.toml files to do the same for Rust, or Gradle files to do the same for Java. This requires the tool to be pluggable.

![image](https://github.com/user-attachments/assets/5d0d64ba-193b-45d0-83ee-046413c221a9)

# 11) Code generation

Native support for generating code

![image](https://github.com/user-attachments/assets/c50bfdca-8ed3-4429-95d5-65de6e8badc7)


# 12) Project constraints and visibility

Supports definition of rules to constrain dependency relationships within the repo. For instance, developers can mark some projects as private to their team so no one else can depend on them. Developers can also mark projects based on the technology used (e.g., React or Nest.js) and make sure that backend projects don't import frontend ones.

![image](https://github.com/user-attachments/assets/e950cc80-cb0e-4d45-ae78-36e228153416)



resources : https://opensource.google/documentation/reference/thirdparty/oneversion
