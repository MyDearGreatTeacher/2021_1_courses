# PowerShell
```
PowerShell不僅是一門指令碼語言，也是一種管理Shell，讓你幾乎可以控制和自動化管理Windows的各層面。
它可以互動式接受和執行命令，你也可編寫指令碼來管理如Exchange、IIS和SharePoint等Windows伺服器，
以及如Azure和Office 365等線上服務。
```
```
PowerShell 
PowerShell  ==  command line shell  ==>執行常用的cmdlet
PowerShell  ==  scripting language 程式語言
```
# PowerShell  ==  command line shell  ==>執行常用的cmdlet
```
使用powershell
```
```
powershell 指令格式 === 動詞-名詞  Verb-Noun

常用動詞 ===> Get, Set, Update, Remove
```
```
【實作練習 lab】 Get-Command
    ==> a list of every command PowerShell is aware of by default
```
```
PowerShell commands類型:
PowerShell commands come in a few flavors: 
cmdlets, functions, aliases(別名), and sometimes external scripts.
```
```
【實作練習 lab】 Get-Command -Name Get-Alias
```
### 查詢使用方法
```
PowerShell 包含詳細的說明文章，解釋了 PowerShell 概念與命令語法。 
您可以在命令提示字元中使用 Get-Help Cmdlet 來顯示這些文章
```
```
【實作練習 lab】Get-Help  Get-Command
```
```
相關連結
    Online Version: http://go.microsoft.com/fwlink/?LinkId=821482
    Get-Help
註解
    若要查看範例，請輸入: "get-help Get-Command -examples".
    如需詳細資訊，請輸入: "get-help Get-Command -detailed".
    如需技術資訊，請輸入: "get-help Get-Command -full".
    如需線上說明，請輸入: "get-help Get-Command -online"
```
```
【實作練習 lab】get-help Get-Command -examples
```

```
【實作練習 lab】 Get-Command -Type Cmdlet | Sort-Object -Property Noun | Format-Table -GroupBy Noun

This command gets all of the cmdlets, sorts them alphabetically by the noun in the cmdlet name, and then displays them in noun-based groups. This display can help you find the cmdlets for a task.
```

```
【實作練習 lab】
```

```
【實作練習 lab】Get-Help about_Core_Commands
```

```
【實作練習 lab】Get-Help -Name About*

 ==>  get a complete list of all the About topics available
```
# 作業 ==>完成底下報告
```
適用於系統管理的範例指令碼
這組範例會逐步解說適合使用 PowerShell 來管理系統的案例。
https://docs.microsoft.com/zh-tw/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7.1

使用物件

檢視物件結構
選取物件的組件
篩選管線中的物件
為物件排序
建立 .NET 和 COM 物件
使用靜態類別和方法
取得 WMI 物件 - Get-CimInstance


管理電腦

變更電腦狀態
收集電腦的相關資訊
使用 FilterHashtable 建立 Get-WinEvent 查詢

管理處理序與服務

使用處理序 Cmdlet 管理處理序
管理服務
管理 Windows PowerShell 磁碟機
使用印表機
執行網路工作
處理軟體安裝
從正在執行的處理序解碼 PowerShell 命令
使用輸出
概念
使用 Out-* Cmdlet 將資料重新導向
使用格式命令變更輸出檢視
管理磁碟機與檔案

管理目前的位置
使用檔案及資料夾
使用檔案、資料夾與登錄機碼
使用登錄項目
使用登錄機碼
建立 UI 元素

建立自訂輸入方塊
建立圖形化日期選擇器
多重選取清單方塊
從清單方塊選取項目
```
# 使用 PowerShell 資源庫
```
https://www.powershellgallery.com/

https://docs.microsoft.com/zh-tw/powershell/scripting/gallery/getting-started?view=powershell-7
PowerShell 資源庫是一個套件存放庫，其中包含您可以下載並利用的指令碼、模組和 DSC 資源。 
您可以使用 PowerShellGet 模組中的 Cmdlet，從 PowerShell 資源庫安裝套件。 
您不需要登入，就可以從 PowerShell Gallery 下載項目。
```

```
【實作練習 lab】 Get-Command -Module PowerShellGet
```

```
【實作練習 lab】Get-InstalledModule
     列出已從 PowerShell 資源庫安裝的套件
```
### 安裝模組
```

```

# PowerShell  ==  scripting language 程式語言
### 編寫與執行指令碼 write a script and execute
```
開發工具
PowerShell Integrated Scripting Environment (ISE) 
Microsoft’s Visual Studio Code editor
```
```
PS> powershell_ise.exe
```

### 撰寫底下程式 WriteHostExample.ps1
```
Write-Host 'Hello, I am in a script!'
```
### 執行程式
```
PS> C:\WriteHostExample.ps1
```

### execution policy 執行策略
```
The execution policy has four main configurations:
[1]Restricted(限制) ==> default, doesn’t allow you to run scripts.
[2]AllSigned This configuration allows you to run only scripts that have been cryptographically signed by a trusted party (more on this later).
[3]RemoteSigned This configuration allows you to run any script you write, and any script you download as long as it’s been cryptographically signed by a trusted party.
[4]Unrestricted(無任何限制) ==> This configuration allows you to run any scripts.
```
```
PS> Get-ExecutionPolicy

PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```
### 更多PowerShell程式設計技巧請參閱
