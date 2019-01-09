# Brief Intro
- :office: : `Infostrum`(assigned by Global eSolutions @HongKong) @Songshan/Taipei
- :construction_worker: : Financial Software Engineer, 2018.04-
- maintain project product

## April 
|xth week|tasks|
|:-|:-|
|1st|-|
|2nd|-|
|3rd|-|
|4th(23)|**Start to work**|

## May
|xth week|tasks|tags|
|:-|:-|:-|
|1st(02)|[feature] Use [**Telerik**](https://www.telerik.com/products/winforms.aspx) grid instead of [**Dapfor**](http://www.dapfor.com/en/net-suite/net-grid) one.|`c#`, `winform`|
|2nd(07)|[feature] Change the login process from **async** to **blocking**.|`c#`, `winform`, `async-await`|
|3rd(14)|[bug] Doesn't record the form preferences(minimized window) **before switching account**.|`c#`, `winform`|
|4th(23)|[feature] Draw chart with import file(3 types formats) - Create a library project with unit test.|`c#`, `winform`, `unit-test`|
|5th(29)|**[contribution]** Introduce [Git](https://git-scm.com/) with my [slides](https://hackmd.io/p/ryHrIEaJX#/9) to the team.([Git Advanced](https://github.com/ChaoLiou/HowGitWorks))<br>**[contribution]** Self-host [Gitea](https://gitea.io/zh-tw/) service with Gitea **docker image**([MyDoc](./Gitea.md)).<br> **[contribution]** Sync(using script) repos both FTP and Gitea([MyDoc](./Sync@FTP2Gitea.md)).<br>**[contribution]** For other projects using `svn`, create new repos on Gitea.|`git`, `gitea`, `docker`, `ftp`, `svn`|

## June
|xth week|tasks|tags|
|:-|:-|:-|
|1st(04)|[feature] Draw chart with import file(3 types formats) - Include the library to the main project and implement the features.([Private Repo](https://github.com/ChaoLiou/ChartData))|`c#`, `winform`|
|2nd(11)|[bug] Doesn't record the form preferences(minimized window) **before reloading and logging out**.<br>[feature] change the chart title and the legend after importing file.|`c#`, `winform`|
|3rd(19)|**[contribution]** For some web app projects having older versions, merge them into one by different branch.|`git`, `gitea`|
|4th(26)|-|

## July
|xth week|tasks|tags|
|:-|:-|:-|
|1st(03)|[feature] Change the chart import feature from **blocking** to **async** while importing file. Support the analysis chart as well. <br>[feature] Change the login process from **async** to **blocking** including the server connecting process.|`c#`, `winform`, `async-await`|
|2nd(10)|**[assistance]** Create a **Vue.js** Web Page for financial news.([Private Repo](https://github.com/ChaoLiou/FinancialNews))|`vue`|
|3rd(17)|[bug] Take too long to load the preference form for the first time.<br>**[assistance]** add new components to the financial news web page, and fix some RWD adjustments.|`c#`, `winform`, `vue`, `rwd`|
|4th(23)|**[contribution]** Create a **C#** console app to generate htmls with meta-datas for **rich link previews** on LINE.([Public Repo](https://github.com/ChaoLiou/RichLinkPreviewMiddler))|`c#`, `meta-data`, `rich-link-preview`|
|5th(30)|-|

## August
|xth week|tasks|tags|
|:-|:-|:-|
|1st(06)|[bug] Take too long to load the preference form for the first time. - Pre-load the preference forms after logging in(without face2face). <br>[feature] Remove the chart timescale after importing file(no need), and use the `FileStream` to import file.<br>[feature] Change the financial news sources from ftp/xml to http/xml(in **JAVA**).|`c#`, `winform`, `java`|
|2nd(13)|[feature] Change the config property specifications for switching ftp/xml or http/xml(in **JAVA**).<br>[bug] Take too long to load the preference form for the first time. - Caused by the 3rd-party panel.<br>[bug] Throw an exception about the font not found caused by the Win10 updates. - recheck the `FontFamily` list before actually using them.<br>**[contribution]** Create mobile app for financial news using **React Native** with **Expo**(using [NativeBase](https://nativebase.io/) UI framework) - only Android(`.apk`), iOS(`.ipa`) needs Apple developer paid account.([Public Repo](https://github.com/ChaoLiou/FinancialNewsRN))|`java`, `c#`, `winform`, `react-native`, `expo`, `nativebase`|
|3rd(20)|**[assistance]** Set up the iMac PC enviroment.|`macOS`|
|4th(27)|[feature] Add some new parameters for initialization settings(in **Objective-C**).|`iOS`, `objective-c`|

## September
|xth week|tasks|tags|
|:-|:-|:-|
|1st(03)|**[assistance]** Let the financial news web page support IE10(all of above) - hex color notation(8->6), `$.ajax` instead of `fetch`, polyfill the `Object.assign` method, and don't use arrow function.<br>**[assistance]** Resize the iframe when the iframe content changes.([Code Block](https://github.com/ChaoLiou/FinancialNews/blob/8d69bc4c90eb93e4e7edb6e10f06b1ab4a3d35c5/index.js#L27-L51))<br>**[contribution]** Create a **C#** console app through the **sql database** API to generate documents(`.md`), including stored procedures, table & function: names, arguments, columns and dependencies.([Public Repo](https://github.com/ChaoLiou/DBDocTemplateGenerator))|`vue`, `ie10-aoa`, `polyfill`, `c#`, `ms-sql`|
|2nd(10)|[bug] The dot(`.`) button on the numpad will be the comma(`,`) button in `en_ID` locale, so a parsing error occurs(in **Objective-C**).|`iOS`,`objective-c`|
|3rd(17)|[bug] The dot(`.`) will be the comma(`,`) in `en_ID` locale while parsing chart data, so the chart got borken(in **Objective-C**).<br>**[contribution]** Create a **C#** console app to crawl the feeds of the financial news web page from [dailyfx](https://www.dailyfx.com/calendar?ref=TopNav) and then export the `.csv` file.([Public Repo](https://github.com/ChaoLiou/FinancialNewsCrawler))|`iOS`, `objective-c`, `c#`, `crawling`|
|4th(26)|**[contribution]** Self-host [CodiMD](https://github.com/hackmdio/codimd) with CodiMD **docker-compose.yml** and spread the **Markdown Syntax** to everyone(not only IT).([Home Page Pic](./codimd.PNG), and the [Markdown Syntax](https://github.com/ChaoLiou/Markdown))|`codimd`, `docker-compose`, `markdown`|

## October 
|xth week|tasks|tags|
|:-|:-|:-|
|1st(01)|-||
|2nd(08)|-||
|3rd(15)|[feature] Add the chart zooming in/out with the 3-rd party called `Core-plot`, using its `Delegation`(in **Objective-C**).|`objective-c`, `delegation`, `core-plot`|
|4th(22)|**[contribution]** Create a **LOASystem**(Leave of Absence System) using [VENoM-Docker](https://github.com/jamesaud/VENoM-Docker) for leaves taking and signing by manager.([Public Repo](https://github.com/ChaoLiou/LOASystem))|`vue`, `express`, `nodejs`, `mongodb`, `docker`, `docker-compose`, `vue-router`, `csr`|
|5th(29)|[feature] Change the most appropriate y range with the chart data(find out the max and min of y in the x range) while scrolling x-axis, and fix the position of the current price label(in **Objective-C**).|`iOS`, `objective-c`|

## November
|xth week|tasks|tags|
|:-|:-|:-|
|1st(05)|[feature-bug] The analysis chart will be overlapping on the main chart(in **Objective-C**).<br>[feature-bug] The moving horizontally event is overrided between the crosshair moving and the chart x-axis scrolling(in **Objective-C**).<br>[feature-bug] The position of date label will move while changing y range(in **Objective-C**).|`iOS`, `objective-c`|
|2nd(12)|**[assistance]** Set up the **Xamarin** environment.|`c#`, `xamarin`|
|3rd(19)|[feature] Let the analysis chart is always on the screen(in **Objective-C**).|`iOS`, `objective-c`|
|4th(26)|[feature] Rearrange the position of the crosshair labels while zomming(in **Objective-C**).|`iOS`, `objective-c`|

## December
|xth week|tasks|tags|
|:-|:-|:-|
|1st(03)|**[contribution]** Add a new leave kind for bussiness trip and a new list page for complement leaves to the **LOASystem**.|`vue`, `express`, `nodejs`, `mongodb`, `docker`, `docer-compose`, `vue-router`, `csr`|
|2nd(10)|[feature] Set bottom ToolbarPlacement on **Xamarin** Android Device.|`c#`, `xamarin`|
|3rd(17)|[bug] Throw an exception about visual styles.<br>**[contribution]** Add a feature to enable/disable employees, and delete employee if disabled, also with a confrim window to check again.|`c#`, `winform`, `vue`, `express`, `nodejs`, `mongodb`, `docker`, `docer-compose`, `vue-router`, `csr`|
|4th(24)|**[contribution]** Add a feature to take annual leaves for the next annual(called pre-annual), and when the time comes, the pre-annual leaves will be moved to annual leaves, then initialize to empty.|`vue`, `express`, `nodejs`, `mongodb`, `docker`, `docer-compose`, `vue-router`, `csr`|
