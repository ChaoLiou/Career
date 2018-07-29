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
> source: it means these `countries` and `organizations` I mentioned above.
- Before I'm in this work, there are a lot of `console applications` or `batch executions` for every patent source type to get its data transfer procedure done. It's like "ok, today we want to add a new patent source type to database for searching, then we design a new data transfer procedure for **only** this new patent source type, and future we will do it whole again". It's really **unmaintainable** to me, because of all application logic/execution flows I need to remember.
- I decide to arrange them by notes, and make a new `pattern` not only for every patent source type we already had but also new patent source type we want in the future. The steps of this `pattern` includes:
  - [detect and download](#detect-and-download) (with or without this step, it depends on the source)
  - [detect and check the goods](#detect-and-check-the-goods)
  - [pre-transfer and transfer](#pre-transfer-and-transfer)
  - [report to us](#report-to-us)

#### detect and download
- detect the volume archives between the official and local, then download the volume archives we don't have. (like mirror copy)
> volume: maybe a date or week no
#### detect and check the goods

#### pre-transfer and transfer

#### report to us

### crawling and scraping skills
### pdf downloading system
