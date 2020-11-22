# Brief Intro
- :office: : `LearningTech` @Pingzhen/Taoyuan
- :construction_worker: : Software Engineer/Junior Fullstack Developer, 2014.12 - 2018.02
- maintain 2 projects and develop new features (in a 2-men group)
  - one is a website for `searching & viewing patents` 
  - another one is also a website not only for `searching & viewing patents`, but also `save them to own account` to
analyze on tables or charts
- renew and maintain `patents transfer system`
  - * transfer the patents which are feeds for searching, from [html sgml xml json] formats to MS-SQL DB)
- join a temparory developer team for new project to implement new & customized features (usually in a 3-men group)
- experience tags
  - `asp.net`, `asp.net mvc`, `webservice, webapi`, `ado.net, linq2sql`, `css/less`, `css/bootstrap`, `js/jquery`
  - `MS SQL`, `IIS`
  - `regular expression`, `xml, sgml`, `manipulate archive(zip, gz, tar) with .net`

# Milestone Experiences
- [patents transfer system](#patents-transfer-system-arrow_up_small)
- [patent pdfs download system](#patent-pdfs-download-system-arrow_up_small)
- [setting up projects on tfs CICD](#setting-up-projects-on-tfs-cicd-arrow_up_small)
- headless browser ui testing with Casperjs

## patents transfer system [:arrow_up_small:](#milestone-experiences)
- it's a system which be able to transfer patents informations from [files inside archives] to [rows in database/tables] 
- the reason why I repalced the old system with this(what's the pros?)
  - create a pattern for every new patent source of the organizations/governments
  - more clearly and easily to maintain or implement new patent source for developers
  - low threshold knowledge for new manipulators(dispart big features into small pieces)
```
 __________________________________________
|Official / Source Site released new patents| 
|(on average, twice a week each: isu/pub)  |
 ''''''''''''''''''''''''''''''''''''''''''
                |
                V
 _______________________________________________      A__________________________________________________________________________
|download: schedulely / manual input to activate| -> |check consistent between the number of files and the number they record    |
|(download archive: .zip, .gz.tar, .rar)        |    |(the records may be from index.lst, .csv or .xls,                          | 
 '''''''''''''''''''''''''''''''''''''''''''''''     | even do archive crc checksum to match the checksum in .txt given by them) |
                                                      '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                                                      / [pass] or [reject then report]                        ______  
                                                     V                                                      /  loop  \
             B_____________________________________________________________________________________________V__        |
            |1. read contents(xml, sgml): extract / just read every entry in the archive from stream to string|_____ /
            |2. sgml to xml(.dtd) / xml -> xpath -> tag -> attribute & value -> fill the data model           |
             '''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | model list ready                  ____
                              V                                  /loop\
             C__________________________________________________V_     |
            |sql bulk copy to insert rows to table several times  |___/
            |(base on the content size and the batch size)        |
             '''''''''''''''''''''''''''''''''''''''''''''''''''''
                              | success or fail
                              V
             ______________________________________________________
            |report results & statistics of step A, step B & step C|
            |(send email / post json to webhook)                   |
             ''''''''''''''''''''''''''''''''''''''''''''''''''''''
```
## setting up projects on tfs CICD [:arrow_up_small:](#milestone-experiences)
- [tfs cicd notes](https://github.com/ChaoLiou/Blog/issues/1)
- [Console Application: BuildFailedNotification](https://github.com/ChaoLiou/BuildFailedNotification)
  - customize a Task to execute this application on tfs CICD, for reporting the failed builds.
## patent pdfs download system [:arrow_up_small:](#milestone-experiences)
- it's a system for the patent pdfs downloading feature and it's easily implemented on existing projects   
- on the existing project side, just make sure user fill the form & click the download button to finish, and post to webapi with informations on server side, then it's all done.
```         
                                                  check the task is finished & gather the progress info then return
                                                    & generate the zip download link
 _______             C_return_GUID               _E_&_G_____________________         ____________________________________________
|website|________   /              \ ___________V_________________          |       |worker which prepare pdf/pdfs, then compress|
 '''''''         \ V     post       |pdf download center (webapi) |         |       |them into \{GUID}\xxx.0.zip (window service)|
 ___________      |--------A------->|generate a GUID for this task|         |      //''''''''''''''''''''''''''''''''''''''''''''
|browser ext|____/ post data:        '''''''''''''''''''''''''''''          |  sql||dependency  | update the status of the row in each pdf to done status 
 ''''''''''' ^|    1. which pdf/pdfs     ^  ^   |                         __V______\\___________V_(when all done -> 
             ||    2. who wants          |  |    B-add-new-task-in-rows->|download tasks(database)|      update finished & zip path)
             ||_D_while(true)_until_100%_|  |                             ''''''''''''''''''''''''
             | continuously ask progress    |
             |                with task GUID|
             |_F_&_H________________________|
              ask & return the download link
```


