# Monorepo vs Polyrepo for micro-service architecture

[Medium Article](https://medium.com/@jaspreet2379/monorepo-vs-polyrepo-for-micro-service-architecture-e258a6e550d7)

## What is Monorepo

Monorepo is a type of repository(typically git repo) used to manage source code using only one repository.

Monorepo is also known as one-repo or uni-repo.

- A monorepo architecture uses only one repository, rather than many.
- For example, a monorepo can use one repo with 3 directories; one directory for a web front end, another directory for a mobile app, yet another for a backend code.

## What is Polyrepo

Polyrepo is a type of repository(typically git repo) used to manage source code using multiple repository.

Polyrepo is also known as many-repo or multi-repo.

- A polyrepo architecture uses multiple repositories, rather than one.
- For example, a polyrepo can use 3 repos, one repo for a web front end, another repo for a mobile app, yet another repo for a backend code.
  
I am assuming, you are reading this article after having worked or some knowledge about pros and cons about each. Read following for more understanding.

[Github](https://github.com/joelparkerhenderson/monorepo_vs_polyrepo)

[Why Google stores billions of lines of code in a single repository - 2016](https://news.ycombinator.com/item?id=15889148)

[It is OK to keep random things in a single monorepo](https://dev.to/zkochan/it-is-ok-to-keep-random-things-in-a-single-monorepo-566e)

In the end it all depends on team, culture, company, requirements of the project and most important tools that you have to minimize complexity at scale.

## Here, i want to touch upon a specific use case of mono-repo for micro-service projects as title states

Smaller teams that may not access to tools for managing complexity of a large project including micro-services.

If your project has large sub-projects, it will be better to use multi-repo approach.

But a mono-repo is more suitable for micro-service project including dozens of related small folders for example AWS Lambdas. Now, multi-repo approach will yield dozens of repo spread across GitHub or GitLab; will be a nightmare to handle co-ordination for smaller teams.

Another use case would be, a css framework that has small components like buttons, widgets, forms etc along with shared components. Although in the end all will be merged unlike micro-service example.

*Use mono-repo for projects including small size semi-independent sub-projects or components. For large sub-projects or components if not tightly coupled use poly-repo.*

So far, we have a repo for large front end app(typically react, angular or vue), large mobile app(java, flutter or whatever it used these days) and micro-service backend API code.

We have 3 repos thus a multi-repo approach, but the 3rd one is a mono-repo of independent AWS Lambda`s.

### But, we have one problem as with any mono-repo…

Say a team of 5 people working on 70 odd lambdas, where each developer typically work on 10–20 lambdas. Now, a developer don`t want to download or changes made to rest of 50–60 lambdas he/she not working on.

So pull master branch with all of code everytime will be in-efficient,

```bash
git pull master
```

However there is a way to do it

1. Create a shared branch for shared modules, few developer can work on this.
2. Pull shared branch with `git pull origin shared`
3. Create multiple branches from latest shared branch commit where each branch add additional folder for lambda code. say branches = `lambda1`, `lambda2`. If branch already exists skip step 3.
4. Then merge changes first checkout your branch say `lambda1`, `git merge --squash shared` with merge latest shared folder into `lambda1` branch locally, work on `lambda1` and push to remote `lambda1` branch.

*Note: Each lambda branch acts as a master; merge --squash keep history of every branch linear.*
*Note: Don\`t merge your branch with master in this scenario, but can do so for css framework example.*

Thus, every branch on remote has shared modules and specific micro-service code.

I haven\`t explored git worktree.

```bash
 git worktree add
```

Please provide feedback if you any other way of managing lambda or kubernetes code.
