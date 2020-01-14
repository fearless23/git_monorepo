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

