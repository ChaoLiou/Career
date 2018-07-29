# Brief Intro
- `LearningTech` (`Innovue` now) @Pingzhen/Taoyuan
- Software Engineer/Junior Fullstack Developer, 14.12 - 18.02
- maintain product project and develop new features (2 men group)
- design and maintain `data transfer` system in scheduler or friendly manipulation
  - transfer the data which is the feeds for searching on primary product (website) from xml/json/... to database)
- assist other projects to implement customized features (3-4 men group)
- `asp.net`, `asp.net mvc`, `ado.netxlinq2sql`, `css/less`, `css/bootstrap`, `js/knockoutjs`, `js/jquery`

# Experiences (only if it's worth mentioning)
## Outline
- [data transfer system](#data-transfer-system)
- [crawling and scraping skills](#crawling-and-scraping-skills)
- [pdf downloading system](#pdf-downloading-system)
- set up all primary projects on `tfs CICD`
- browser ui testing with Casperjs

### data transfer system
- First of all, you should know that the `data` here is the `patent data`, and these patents which users can search for on products are provided from many different countries (like us, tw, cn, jp, kr) or organizations (like ep, wipo, docdb). On average, most of the patent sources would provide new patents twice a week.
- Before I'm in this work, there are a lot of console applications or batch executions for every patent source to get its data transfer procedure done. It's like "ok, today we want to add a new patent source to database for searching, then we design a new data transfer procedure for only this new patent source, and future we do it whole again". It's really unmaintainable to me, because of all application logic/execution flows I need to remember.
- I decide to arrange them by notes, and make a new pattern not only for every patent source but also new patent source we want in the future.
### crawling and scraping skills
### pdf downloading system
