# Brief Intro
- `LearningTech` (`Innovue` now) @Pingzhen/Taoyuan
- Software Engineer/Junior Fullstack Developer, 14.12 - 18.02
- maintain 2 projects and develop new features (2 men group)
  - one is a website for searching & viewing patents 
  - another one is a website not only for searching & viewing patents, but also download them to your own project to
analyze in many different types of tables or charts  
- design and maintain `patents transfer system`
  - * transfer the patent which is the feeds for searching on websites, from sgml/xml/json to database)
- sometimes assist other developers' projects to implement customized features (3-4 men group)
- experience tags
  - `asp.net`, `asp.net mvc`, `webservice, webapi`, `ado.net, linq2sql`, `css/less`, `css/bootstrap`, `js/knockoutjs`, `js/jquery`
  - `MS SQL`, `IIS`
  - `regular expression`, `xml, sgml`, `manipulate archive(zip, gz, tar)`

# Experiences
- [patents transfer system](#patents-transfer-system)
- [crawling and scraping skills](#crawling-and-scraping-skills)
- [patent pdfs download system](#patent-pdfs-download-system)
- setting up projects on `tfs CICD`
- headless browser ui testing with Casperjs

### patents transfer system
- it's a system that transfer patent information from [xmls inside a archive] to [rows inside database/tables] 
- pros against orignal one: 
  - same design pattern for every patent source of the organizations/governments
  - will be able to debug clearly and easy to implement new patent source 
```
 __________________________________________
|Offical / Source Site released new patents| 
|(on average, twice a week each: isu/pub)  |
 ''''''''''''''''''''''''''''''''''''''''''
                |
                V
 _______________________________________________      A______________________________________________________________________
|download: schedulely / manual input to activate| -> |check consistent between the number of files and the number they record|
|(download archive: .zip, .gz.tar, .rar)        |    |(the records may be from index.lst, .csv or .xls,                      | 
 '''''''''''''''''''''''''''''''''''''''''''''''     | even do archive crc checksum to match the checksum in .txt they gave) |
                                                      ''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                                                      / [pass] or [reject then report]                        ______  
                                                     V                                                      /  loop  \
             B_____________________________________________________________________________________________V__        |
            |1. read contents(xml, sgml): extract / just read every entry in the archive from stream to string|_____ /
            |2. sgml to xml(.dtd) / xml -> xpath -> tag -> attribute & value -> fill the model class          |
             '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | a model list and ready to database ___
                              V                                  /loop\
             C__________________________________________________V_     |
            |sql bulk copy to insert rows to table several times  |___/
            |(based on the content size and the batch size)       |
             '''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | success or fail
                              V
             ______________________________________________________
            |report results & statistics of step A, step B & step C|
            |(send email / post json to webhook)                   |
             ''''''''''''''''''''''''''''''''''''''''''''''''''''''
```
### crawling and scraping skills
### patent pdfs download system
- it's a system for exist projects which need to add feature for downloading patent pdfs to implement so easily 
- on the project side, just make user fill the form & click the download button to finish, and post to webapi with informations, then it's all done.
```         
                                                  check the task is finished & gather the progress info then return
                                                    & generate the zip download link
 _______             C_return_GUID               _E_&_G_____________________         ____________________________________________
|website|________   /              \ ___________V_________________          |       |worker which prepare pdf/pdfs, then compress|
 '''''''         \ V     post       |pdf download center (webapi) |         |       |them into \{GUID}\xxx.0.zip (window service)|
 ___________      |--------A------->|generate a GUID for this task|         |      //''''''''''''''''''''''''''''''''''''''''''''
|browser ext|____/ post data:        '''''''''''''''''''''''''''''          |  sql||dependency  | update the same row each pdf done 
 ''''''''''' ^|    1. which pdf/pdfs     ^  ^   |                         __V______\\___________V_(when all done -> 
             ||    2. who wants          |  |    B---add-new-task-rows-->|download tasks(database)|      update finished & zip path)
             ||_D_while(true)_until_100%_|  |                             ''''''''''''''''''''''''
             | continuously ask progress    |
             |                with task GUID|
             |_F_&_H________________________|
              ask & return the download link
```


