# Brief Intro
- `LearningTech` (`Innovue` now) @Pingzhen/Taoyuan
- Software Engineer/Junior Fullstack Developer, 14.12 - 18.02
- maintain 2 product projects and develop new features (2 men group)
- design and maintain `data transfer` system in scheduler or friendly manipulation
  - transfer the data which is the feeds for searching on our website from xml/json/... to database)
- often assist other projects to implement customized features (3-4 men group)
- experience tags
  - `asp.net`, `asp.net mvc`, `webservice, webapi`, `ado.net, linq2sql`, `T-SQL`, `css/less`, `css/bootstrap`, `js/knockoutjs`, `js/jquery`
  - `MS SQL`, `IIS`
  - `regular expression`, `xml, sgml`, `reading archive(zip, gz, tar)`

# Experiences
- [data transfer system](#data-transfer-system)
- [crawling and scraping skills](#crawling-and-scraping-skills)
- [pdf downloading system](#pdf-downloading-system)
- setting up projects on `tfs CICD`
- headless browser ui testing with Casperjs

### data transfer system
- same pattern for every type
- clearly debugging and easy to implement new one 
```
 __________________________________________
|Offical / Source Site released new package| 
|(on average, twice a week each)           |
 ''''''''''''''''''''''''''''''''''''''''''
                |
                V
 _______________________________________________      A______________________________________________________________________
|download: schedulely / manual input to activate| -> |check consistent between the number of files and the number they record|
|(download archieve: .zip, .gz.tar, .rar)       |    |(the records may be from index.lst, .csv or .xls,                      | 
 '''''''''''''''''''''''''''''''''''''''''''''''     | even do archive crc checksum to match the checksum in .txt they give) |
                                                      ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                                                      / pass or reject then report                            ______  
                                                     V                                                      /  loop  \
             B_____________________________________________________________________________________________V__        |
            |1. read contents(xml, sgml): extract / just read every entry in the archive from stream to string|_____ /
            |2. sgml to xml(.dtd) / xml -> xpath -> tag -> attribute & value -> fill the model class          |
             '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | a model list and ready to database ___
                              V                                  /loop\
             C__________________________________________________V_     |
            |sql bulk copy to insert rows to table several times  |___/
            |(based on the content size and change the batch size)|
             '''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | success or fail
                              V
             ___________________________________________________
            |the results & statistics of step A, step B & step C|
            |(output: email -> send, json -> post to webhook)   |
             '''''''''''''''''''''''''''''''''''''''''''''''''''
```
### crawling and scraping skills
### pdf downloading system
- fill the form & click the download button on the website, then you can leave this page
```
 _______              C_return_GUID                                            ___________________________________________
|website|________   /              \ _____________________________            |worker which prepare pdf/pdfs, then compress|
 '''''''         \ V     post       |pdf download center(webapi)  |           |them into \{GUID}\xxx.0.zip (window service)|
 ___________      |--------A------->|generate a GUID for this task|          //''''''''''''''''''''''''''''''''''''''''''''
|browser ext|____/ post data:        '''''''''''''''''''''''''''''       sql||dependency  | update the same row each pdf done 
 ''''''''''' ^|    1. which pdf/pdfs     ^  ^   |                         ___\\___________V_______(when all done -> finished & zip path)
             ||    2. who wants          |  |    B---add-new-task-rows-->|download tasks(database)|
             ||_D_while(true)_until_100%_|  |                             ''''''''''''''''''''''''
             | get with GUID to ask progress|
             |_E_&_F________________________|
             get & return the download url to the zip path
```


