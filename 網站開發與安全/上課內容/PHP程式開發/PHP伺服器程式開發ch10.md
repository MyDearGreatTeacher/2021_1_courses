# PHP伺服器程式開發 ch 10 ...
```
1.表單設計與伺服器資料處理
```

# 1.表單設計與伺服器資料處理
## 客戶端表單程式1 phone.html
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <form>
      姓&nbsp;&nbsp;&nbsp;名：<input type="text" name="UserName" size="40"><br>
      E-Mail：<input type="email" name="UserMail" size="40" value="username@mailserver"><br>
      年&nbsp;&nbsp;&nbsp;齡：
      <input type="radio" name="UserAge" value="Age1">未滿20歲
      <input type="radio" name="UserAge" value="Age2" checked>20~29
      <input type="radio" name="UserAge" value="Age3">30~39
      <input type="radio" name="UserAge" value="Age4">40~49
      <input type="radio" name="UserAge" value="Age5">50歲以上<br>
      您使用過哪些廠牌的手機？
      <input type="checkbox" name="UserPhone[]" value="hTC" checked>hTC
      <input type="checkbox" name="UserPhone[]" value="Apple">Apple
      <input type="checkbox" name="UserPhone[]" value="ASUS">ASUS
      <input type="checkbox" name="UserPhone[]" value="SONY">SONY<br>
      您使用手機時最常碰到什麼問題？<br>
      <textarea name="UserTrouble" cols="45" rows="4">上網品質不夠穩定</textarea><br>
      您使用過哪些電信業者的門號？(可複選)
      <select name="UserNumber[]" size="4" multiple>
        <option value="中華電信">中華電信
        <option value="台灣大哥大" selected>台灣大哥大
        <option value="遠傳">遠傳
        <option value="亞太電信">亞太電信
      </select><br>
      <input type="submit" value="提交">
      <input type="reset" value="重新輸入">
    </form>
  </body>
</html>
```
## 客戶端表單程式2 phone2.html
```
      <form> ==> 改成  <form method="post" action="confirm.php">
  ........  加入資料傳送方法(method="post")及伺服器處理程式(action="confirm.php")
```
## 伺服器處理程式 confirm.php
```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
  <body>
    <?php
      $Name = $_POST["UserName"];
      $Mail = $_POST["UserMail"];
      switch($_POST["UserAge"])
      {
        case "Age1":
          $Age = "未滿20歲";
          break;
        case "Age2":
          $Age = "20~29";
          break;
        case "Age3":
          $Age = "30~39";
          break;
        case "Age4":
          $Age = "40~49";
          break;
        case "Age5":
          $Age = "50歲以上";
      }
      $Phone = $_POST["UserPhone"];
      $Trouble = $_POST["UserTrouble"];
      $Number = $_POST["UserNumber"];
    ?>
    <p><i><?php echo $Name; ?></i>，您好！您輸入的資料如下：</p>
      電子郵件地址：<?php echo $Mail; ?><br>
      年齡：<?php echo $Age; ?><br>
      曾經使用過的手機廠牌：<?php foreach($Phone as $Value) echo $Value.'&nbsp;'; ?><br>
      使用手機時最常碰到的問題：<?php echo $Trouble; ?><br>
      使用過哪些電信業者的門號：<?php foreach($Number as $Value) echo $Value.'&nbsp;'; ?>
  </body>
</html>
```
### 作業1:使用者註冊表單
### 作業2:使用者登入表單(範例:github登入表單)
### 作業3:將使用者表單輸入的資料寫入文字檔 ==>再用pdf印出
### 作業4:將使用者表單輸入的資料寫入資料庫
