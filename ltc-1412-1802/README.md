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
                                                      / pass or reject then report                            _____   
                                                     V                                                      /  loop \
             B_____________________________________________________________________________________________V__       |
            |1. read contents(xml, sgml): extract / just read every entry in the archive from stream to string|____ /
            |2. sgml to xml(.dtd) / xml -> xpath -> tag -> attribute & value -> fill the model class          |
             '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | a model list and ready to database
                              V
             C____________________________________
            |sql bulk copy to insert rows to table|
             '''''''''''''''''''''''''''''''''''''
                              | success or fail
                              V
             ___________________________________________________
            |the results & statistics of step A, step B & step C|
            |(output: email -> send, json -> post to webhook)   |
             '''''''''''''''''''''''''''''''''''''''''''''''''''
```
### crawling and scraping skills
### pdf downloading system
- 
