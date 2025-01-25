OVERVIEW

This script is created for users to be able to backup/restore application data in a more complete way. Supported devices must meet the following criteria: Android 8++arm64.

Since I am from Taiwan, the version released is Traditional Chinese (CN system will automatically translate its own script into Simplified Chinese).
Advantages

    Data integrity: After changing the system, all the original data will be retained, no need to re-login or download additional data packages.
    Support backup SSAID, perfect backup of LINE.
    Supports backup of application privileges Can backup runtime privileges and ops privileges.
    Easy to operate: Simple steps to back up the complete data of the application!
    Less restriction: No restriction on machine type, cross Android version.
    Powerful: Backup and restore split apk.
    Many algorithms: Currently supported compression algorithms are tar (default)
    zstd.
    Fast speed: even with zstd compression algorithm, the rate is still fast (compared to titanium backup swift backup).
    The script comes with tools integrity validation and compressed package validation.

How to use

Please read the following instructions carefully to minimize unnecessary problems.
Recommended tool: MT Manager, if you use Termux, please do not use tsu.
Please do not use tsu if you are using Termux. The following operations require ROOT!!!!

    First extract the downloaded data backup script.zip to any directory, you can see the following files and a directory: generate application list.sh backup_settings.conf backup_applications.sh tools backup_custom_folder.sh terminate_script.sh WARNING! Both backup and restore must ensure the existence and integrity of the tools or the script will be invalidated or binary recall will fail.

    Then run the GenerateAppList.sh script and wait for the end of the script output, then wait for the end of the prompt, it will generate an appList.txt in the current directory, which is all the third-party apps you have installed.

    Now open the generated appList.txt and save it according to the prompts inside, then you have set up the software you need to backup.

    Finally, find backup_settings.conf, open it and save it according to the prompts, then open backup_app.sh and wait for the backup to finish, it will generate a folder named with Backup_compression algorithm name in the current directory, which is your software backup. Keep this whole folder to other location, after brushing the machine to copy back to the phone, directly in the folder to find the restore backup.sh can restore all the backup data, the same reason, there is an appList.txt, the use of the same method with the 3rd step, do not need to restore the deletion can be, in addition to go into the folder of the backup folder to find a single application folder Backup script and restore script can be backed up separately. and restore script can be used to backup and restore the script alone.

    script execution process please pay attention to the red word prompts any error, and use the restore script pay attention to the end of the restore whether the application exists ssaid, assuming that ssaid prompts the existence of ssaid, please restart immediately after the restoration of ssaid has been applied to ssaid, assuming ssaid restoration immediately after the opening of the application will lead to ssaid applied to the failure, because android will generate a new The ssaid is one of the judgments to determine whether the application has changed the environment and device, to keep the consistency can reduce the prompts such as logging in a different place or the need to log in again to verify the method.

Additional instructions: How to recover The following are instructions for recovering the files in the folder?


    Find appList.txt in the recovery folder, open it, edit the list, save it and exit.

    Find restore backup.sh Give root and wait for the script to finish.

    Regenerate app list.sh can be used to refresh the list in appList.txt Use it when you delete any apps in the list to backup, or when restore backup.sh prompts the list error.

    terminate script.sh used when you suddenly want to terminate the script or accidental operation Similarly, there is a backup folder, because the script does not require background characteristics can not use conventional means of termination, so I wrote a separate script termination

About how to update the script?

    Currently there are three ways to update, there are the following ways
    1. manually download the backup script zip uncompressed directly to the script of any directory (not including tools directory) of any place to execute any script can be updated, the script will be prompted
    2. This backup of any script in the execution of the Internet to detect the version of the script, when the update will be prompted to download their own, according to the script prompts can be operated (conf update = 1 when in effect), the script Internet only for the purpose of checking for updates, without any illegal operation or the down loader!
    3. will download the compressed package is not uncompressed directly in /storage/emulated/0/Download script automatically detect the update, and follow the prompts can operate
    4. Download the script in the QQ group without unzipping the script will detect the update themselves.

Feedback

    If there is a problem during the use, please bring a screenshot and explain the problem in detail, build issues.
    Coolan @落葉淒涼TEL
    QQ Group 976613477
    TG https://t.me/yawasau_script

Q&A

    Why is there a dex in a shell script?
    The dex is used to realize purposes that are difficult to achieve with scripts, currently saaid backup recovery, backup recovery runtime permissions and oops permissions, downloading and accessing the GitHub api to check for script updates, listing the user application name and package name, and converting from traditional to simplified Chinese are all dex functions, thanks to Android-DataBackup by XayahSuSuSu!

Frequently Asked Questions

Q1：What should I do if the batch backup fails? A1：Exit the script, delete /data/backup_tools and backup again.

Q2：What should I do if the batch restore fails? A2：Exit the script, follow the same operation as above. If it is still wrong, please create issues, I will help you troubleshoot the error.

Q3：Can WeChat/QQQ backup & recover data perfectly? A3：Can't guarantee it, some people say it can't and some say it can, so there will be a prompt for backup. It is recommended to use your trusted backup software to back up WeChat/QQ once more to prevent losing important data.

Q4：Why do some apps take a long time to backup? For example, King of Glory, PUBG, the original God, WeChat, QQ. A4: Because the data package with the software are backed up to you, for example, the original God data package 9GB +, of course, long enough to crack, recovery is the same reason, but also to decompress the data package!

Q5:Script every backup is a new backup? A5;Scripts will be backed up when compared to the last backup SIZE size of the backup if there is a difference on the backup, otherwise ignore the backup to save time!

Backing up scripts took me a lot of time and effort, if you think it's good, you can donate XD . (https://paypal.me/YAWAsau?country.x=TW&locale.x=zh_TW))
Thanks for your contribution!

    Stinky Batch Lao K (kmou424): Provide part of the idea with validation function
    Chip Lao Fang (xiong's Lao Fang): provide automatic update script program
    Fatty Lao Chen (雨季騷年)
    XayahSuSuSu (XayahSuSuSu): provide App support, dex support

Document Editor: Petit-Abba, YuKongA




### Original Readme below

# Backup_script 數據備份腳本
[![Stars](https://img.shields.io/github/stars/YAWAsau/backup_script?label=stars)](https://github.com/YAWAsau)
[![Download](https://img.shields.io/github/downloads/YAWAsau/backup_script/total)](https://github.com/YAWAsau/backup_script/releases)
[![Release](https://img.shields.io/github/v/release/YAWAsau/backup_script?label=release)](https://github.com/YAWAsau/backup_script/releases/latest)
[![License](https://img.shields.io/github/license/YAWAsau/backup_script?label=License)](https://choosealicense.com/licenses/gpl-3.0)
[![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/yawasau_script)

## 概述

創作該腳本是為了使用戶能夠更加完整地**備份/恢復**應用數據，
支援設備必須符合以下條件：`Android 8+`+`arm64`。

由於本人是台灣人所以發布的版本為繁體版
(CN系統將自動翻譯自身腳本為簡體中文）


## 優勢

- 數據完整：在更換系統之後，原有的數據全部保留，無需重新登陸或者下載額外數據包。
- 支援備份SSAID 可完美備份LINE
- 支援備份應用權限 可備份運行時權限與ops權限
- 易操作：簡單几步即可備份應用完整數據！
- 限制少：不限制機型，可跨安桌版本。
- 功能強：可備份恢復`split apk`。
- 算法多：目前支持的壓縮算法有 `tar(默認)`
- `zstd`。
- 速度快：即使使用`zstd`壓縮算法速率依舊快速（對比鈦備份 swift backup）。
- 腳本自帶tools完整性效驗與壓縮包效驗
## 如何使用
`請認真閱讀以下說明，以減少不必要的問題`

##### 推薦工具：[`MT管理器`](https://www.coolapk.com/apk/bin.mt.plus)，若使用`Termux`，則請勿使用`tsu`。

#### !!!以下操作皆須ROOT!!! ####

1. 首先將下載到的`數據備份脚本.zip`解壓到任意目錄後，可以看到以下幾個文件與一個 目錄：`生成應用列表.sh` `backup_settings.conf` `備份應用.sh` `tools` `備份自定義資料夾.sh` `終止腳本.sh` `警告! 不論備份或是恢復都必須保證tools的存在與完整性 否則腳本失效或是二進制調用失敗`。

2. 然後執行`生成應用列表.sh`腳本，並等待腳本輸出結束，再等待提示結束，此時會在當前目錄生成一個`appList.txt`，這就是你當前安裝的所有第三方應用。

3. 現在打開生成的`appList.txt`，根據裏面的提示操作後保存，這樣你就設置好了需要備份的軟件。

4. 最後找到`backup_settings.conf`打開後根據提示設置保存，再打開`備份應用.sh`，等候備份結束完成後會在當前目錄生成一個以`Backup_壓縮算法名`命名的資料夾，裡面就是你的軟件備份。把這個資料夾整個保持到其他位置，刷完機后複製回手機，直接在資料夾裡找到`恢復備份.sh`即可恢復備份的所有數據，同樣道理，裡面也有個`appList.txt`，使用方法跟第3步驟一樣，不需要還原的刪除即可，另外進去備份好的資料夾找到單獨應用資料夾有個 Backup腳本 and restore腳本可以單獨備份與恢復腳本。

5. 腳本執行過程中請留意紅色字眼提示有無任何錯誤，並且使用恢復腳本時留意恢復結束後是否提示應用存在ssaid，假設提示存在ssaid請在恢復後立刻重啟已便套用ssaid,假設恢復ssaid後立刻打開應用會導致ssaid套用失敗，因為Android會產生一個新的saaid，如此會導致應用卡白屏或是提示需要登錄，ssaid是判斷應用是否換過環境與設備的判斷之一，保持一致可以減少諸如提示異地登錄或是需要重新登入驗證的方法。


 ##### 附加說明：如何恢復 以下是關於恢復資料夾內的文件說明?

1. 找到恢復資料夾內的appList.txt打開 編輯列表 保存退出

2. 找到恢復備份.sh 給予root後等待腳本結束即可

3. 重新生成應用列表.sh可用於刷新appList.txt內的列表 使用時機為當你刪除列表內的任何應用備份時,抑或者是恢復備份.sh提示列表錯誤時

4. 終止腳本.sh用於突然想要終止腳本或是意外操作時使用 同理備份資料夾也有一個，因為腳本無須後台特性不能使用常規手段終結，故此另外寫了一個腳本終止


# 關於如何更新腳本？
- 目前有三種更新方法，有下列方式
- 1.手動將下載的備份腳本zip不解壓縮直接放到腳本任意目錄(不包括tools目錄內)的任意地方執行任何腳本即可更新，腳本將提示
- 2.此備份的任何腳本在執行時均會聯網檢測腳本版本，當更新時會自己提示與下載，根據腳本提示操作的即可(conf update=1時生效),腳本聯網僅作為檢查更新用途，無任何非法操作亦或是下發格機
- 3.將下載的壓縮包不解壓縮直接放在/storage/emulated/0/Download腳本自動檢測更新，並按照提示操作即可
- 4.在QQ群內下載的腳本不解壓縮腳本會自己檢測更新

## 關於反饋
- 如果使用過程中出現問題，請攜帶截圖並詳細說明問題，建立 [issues](https://github.com/YAWAsau/backup_script/issues)。
- 酷安 @[落葉淒涼TEL](http://www.coolapk.com/u/2277637)
- QQ組 976613477
- TG https://t.me/yawasau_script

## 答疑
- 一個shell腳本內為什麼有dex?
- dex用來實現腳本難以實現的目的，目前saaid備份恢復，備份恢復運行時權限與ops權限，下載與訪問GitHub api來檢查腳本更新，列出使用者應用名稱與包名，繁體轉簡體均為dex的功能，感謝[Android-DataBackup](https://github.com/XayahSuSuSu/Android-DataBackup) by [XayahSuSuSu](https://github.com/XayahSuSuSu)

## 常見問題

Q1：批量備份大量提示失敗怎麼辦？
A1：退出腳本，刪除/data/backup_tools，再備份一次

Q2：批量恢復大量提示失敗怎麼辦？
A2：退出腳本，按照上面同樣操作。 如果還是錯誤，請建立issues，我幫你排除錯誤

Q3：微信/QQ 能不能完美備份&恢復數據？
A3：不能保證，有的人說不能有的人說能，所以備份會有提示。 建議用你信賴的備份軟件針對微信/QQ再備份一次，以防丟失重要數據

Q4：為什麼部分應用備份很久？ 例如王者榮耀、PUBG、原神、微信、QQ。
A4：因為連同軟件數據包都給你備份了，例如原神數據包9GB+，當然久到裂開了，恢復也是同理，還要解壓縮數據包

Q5:腳本每次備份都是全新備份嗎？
A5;腳本備份時會比對上次備份時的備份SIZE大小 如果有差異就備份,反之忽略備份節省時間

備份腳本耗費了我大量時間與精力 如果你覺得好用，可以捐贈XD
.(https://paypal.me/YAWAsau?country.x=TW&locale.x=zh_TW))


## 銘謝貢獻
- 臭批老k([kmou424](https://github.com/kmou424))：提供部分與驗證函數思路
- 屑老方([雄氏老方](http://www.coolapk.com/u/665894))：提供自動更新腳本方案
- 胖子老陳(雨季騷年)
- XayahSuSuSu([XayahSuSuSu](https://github.com/XayahSuSuSu))：提供App支持,dex支持

`文檔編輯：Petit-Abba, YuKongA`
