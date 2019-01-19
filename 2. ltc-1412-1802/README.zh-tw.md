# 簡略介紹
- :office: : `LearningTech` @Pingzhen/Taoyuan
- :construction_worker: : Software Engineer/Junior Fullstack Developer, 2014.12 - 2018.02
- 維護 2 個專案, 並開發新功能 (2 人團隊)
  - 一個是專利檢索與檢視的網站平台
  - 另一個不只是檢索與檢視, 還能下載儲存到自己的線上專案裡, 再透過多種表格與圖表進一步分析
- 重新設計與維護 `專利轉置系統`
  - * 轉置專利 從 html/sgml/xml/json 的形式檔案 到 資料庫, 這些專利就是網站平台的檢索與檢視資料
- 協助其他開發團隊的專案, 實作一些客製化功能 ( 3-4 人團隊 )
- 經驗標籤
  - `asp.net`, `asp.net mvc`, `webservice, webapi`, `ado.net, linq2sql`, `css/less`, `css/bootstrap`, `js/knockoutjs`, `js/jquery`
  - `MS SQL`, `IIS`
  - `regular expression`, `xml, sgml`, `manipulate archive(zip, gz, tar)`

# 里程碑經歷
- [專利轉置系統](#專利轉置系統-arrow_up_small)
- [設定公司專案到 `tfs CICD`](#將公司專案的-cicd-設定至-tfs-arrow_up_small)
- [專利 PDF 下載系統](#專利-pdf-下載系統-arrow_up_small)
- 無頭瀏覽器 UI 測試 (使用 Casperjs)

## 專利轉置系統 [:arrow_up_small:](#里程碑經歷)
- 這個系統能轉置專利資訊從 `壓縮檔裡的檔案` 到 `資料庫的資料集`
- 為何我要把舊系統替換掉? 
  - 即可使用相同的 design pattern 針對不同的專利來源實作 (專利來源: 可能是政府, 如 us, tw, cn,... 或組織, 如 ep, wo, docdb,...)
  - 未來 debug 問題也能夠更清晰, 更輕鬆
  - 負責維護的新進人員所需的知識門檻較低
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

## 將公司專案的 CICD 設定至 tfs [:arrow_up_small:](#里程碑經歷)
- [tfs cicd notes](https://hackmd.io/s/Bkg9M3LSQ)
- [Console Application: BuildFailedNotification](https://github.com/ChaoLiou/BuildFailedNotification)
  - 在 tfs CICD 上自訂 Task 執行這程式, 讓 build 失敗之後還能回報.
## 專利 PDF 下載系統 [:arrow_up_small:](#里程碑經歷)
- 這個系統讓公司其他已存在的專案能提供 `專利 PDF 下載`的功能
- 一個已存在的專案(例如: 網站, browser extension), 只要提供介面讓使用者填資料(email), 再由程式透過 post 把資訊送到 PDF 下載系統 webapi, 就完成了. 
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


