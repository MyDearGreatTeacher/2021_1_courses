# PowerShell語法
```
輸入與輸出
  輸入 ==> Read-Host
  $Age = Read-Host "Please enter your age"
  $pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
  https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1
  
  輸出 ==> Write—Host  Write—Output
  https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/write-host?view=powershell-7.1
  https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.1
  

型別(Data Type)與資料結構
   Arrays|Hashtables|Lists, dictionaries, queues, and stacks
   
變數(Variables)

運算子(Operators)與表示式
   Arithmetic |  Assignment | Comparison | Regular expression-based operators
   Binary |  Logical  |  Type | Redirection operators

流程控制(CONTROL FLOW)
   決策結構 ==> The if Statement  | The else Statement | The elseif Statement | The switch Statement
   重複(loop)結構 ==> foreach | for  |while  | do/while | do/until 

函式(Functions)

模組(Modules)
```
### 進階技術
```
檔案處理: CSV Excel  JSON

正則表達式: Regular expression

PESTER 測試技術
```
### 應用
```
Sample scripts for system administration
https://docs.microsoft.com/en-us/powershell/scripting/samples/sample-scripts-for-administration?view=powershell-7.1
```
# 教科書
```
PowerShell 流程自動化攻略 
Powershell for Sysadmins: A Hands-On Guide to Automating Your Workflow
Adam Bertram 著 林班侯 譯  碁峰資訊  2020-12-09

https://nostarch.com/powershellsysadmins

Part I: Fundamentals ==> 基本語法
Chapter 1: Getting Started
Chapter 2: Basic PowerShell Concepts
Chapter 3: Combining Commands
Chapter 4: Control Flow
Chapter 5: Error Handling
Chapter 6: Writing Functions
Chapter 7: Exploring Modules

Chapter 8: Running Scripts Remotely
Chapter 9: Testing with Pester

Part II: Automating Day-to-Day Tasks 應用 ==>很重要
Chapter 10: Parsing Structured Data
Chapter 11: Automating Active Directory
Chapter 12: Working with Azure
Chapter 13: Working with AWS
Chapter 14: Creating a Server Inventory Script

Part III: Building Your Own Module  超級棒 ==> 撰寫powershell模組
Chapter 15: Provisioning a Virtual Environment
Chapter 16: Installing an Operating System
Chapter 17: Deploying Active Directory
Chapter 18: Creating and Configuring a SQL Server
Chapter 19: Refactoring Your Code
Chapter 20: Creating and Configuring an IIS Web Server
```
