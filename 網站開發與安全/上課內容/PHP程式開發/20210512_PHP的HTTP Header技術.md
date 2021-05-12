# PHP的HTTP Header技術
```
用途:
網頁重新導向
使用者與密碼認證  ==> http 認證 : basic(base64) vs digest
自動導向到PC版或行動版網頁
讓使用者下載檔案( 隱藏檔案的位置 )
```
# PHP header() 函数
```
https://www.php.net/manual/en/function.header.php
https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/239657/
https://www.w3school.com.cn/php/func_http_header.asp
```
# http header
```
https://en.wikipedia.org/wiki/List_of_HTTP_header_fields

HTTP 頭欄位根據實際用途被分為以下 4 種類型：
通用頭欄位(英語：General Header Fields)
請求頭欄位(英語：Request Header Fields)
回應頭欄位(英語：Response Header Fields)
實體頭欄位(英語：Entity Header Fields)
```
# PHP header()更多範例
```
https://codertw.com/%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80/239657/
```
```
<?php

// ok
header(‘HTTP/1.1 200 OK’);

//設定一個404頭:
header(‘HTTP/1.1 404 Not Found’);

//設定地址被永久的重定向
header(‘HTTP/1.1 301 Moved Permanently’);

//轉到一個新地址
header(‘Location: http://www.baidu.com’);

//檔案延遲轉向:
header(‘Refresh: 10; url=http://www.example.org/’);
print ‘You will be redirected in 10 seconds’;

//當然，也可以使用html語法實現
// <meta http-equiv=”refresh” content=”10;http://www.example.org/ />
// override X-Powered-By: PHP:
header(‘X-Powered-By: PHP/4.4.0’);
header(‘X-Powered-By: Brain/0.6b’);

//文件語言
header(‘Content-language: en’);

//告訴瀏覽器最後一次修改時間
$time = time() – 60; // or filemtime($fn), etc
header(‘Last-Modified: ‘.gmdate(‘D, d M Y H:i:s’, $time).’ GMT’);

//告訴瀏覽器文件內容沒有發生改變
header(‘HTTP/1.1 304 Not Modified’);

//設定內容長度
header(‘Content-Length: 1234’);

//設定為一個下載型別
header(‘Content-Type: application/octet-stream’);
header(‘Content-Disposition: attachment; filename=”example.zip”‘);
header(‘Content-Transfer-Encoding: binary’);
// load the file to send:
readfile(‘example.zip’);

// 對當前文件禁用快取
header(‘Cache-Control: no-cache, no-store, max-age=0, must-revalidate’);
header(‘Expires: Mon, 26 Jul 1997 05:00:00 GMT’); // Date in the past
header(‘Pragma: no-cache’);

//設定內容型別:
header(‘Content-Type: text/html; charset=iso-8859-1’);
header(‘Content-Type: text/html; charset=utf-8’);
header(‘Content-Type: text/plain’); //純文字格式
header(‘Content-Type: image/jpeg’); //JPG圖片
header(‘Content-Type: application/zip’); // ZIP檔案
header(‘Content-Type: application/pdf’); // PDF檔案
header(‘Content-Type: audio/mpeg’); // 音訊檔案
header(‘Content-Type: application/x-shockwave-flash’); //Flash動畫


//顯示登陸對話方塊
header(‘HTTP/1.1 401 Unauthorized’);
header(‘WWW-Authenticate: Basic realm=”Top Secret”‘);
print ‘Text that will be displayed if the user hits cancel or ‘;
print ‘enters wrong login data’;
?>
```
