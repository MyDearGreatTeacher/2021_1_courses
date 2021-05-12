# $_session[]
```
$_SESSION
(PHP 4 >= 4.1.0, PHP 5, PHP 7, PHP 8)

$_SESSION — Session variables

Description 
An associative array containing session variables available to the current script. 

See the Session functions documentation for more information on how this is used.

https://www.php.net/manual/en/reserved.variables.session.php
```

## 常用的 Session 函式庫
```
https://www.php.net/manual/en/ref.session.php

session_abort — Discard session array changes and finish session
session_cache_expire — Get and/or set current cache expire
session_cache_limiter — Get and/or set the current cache limiter
session_commit — Alias of session_write_close
session_create_id — Create new session id
session_decode — Decodes session data from a session encoded string
session_destroy — Destroys all data registered to a session
session_encode — Encodes the current session data as a session encoded string
session_gc — Perform session data garbage collection
session_get_cookie_params — Get the session cookie parameters
session_id — Get and/or set the current session id
session_module_name — Get and/or set the current session module
session_name — Get and/or set the current session name
session_regenerate_id — Update the current session id with a newly generated one
session_register_shutdown — Session shutdown function
session_reset — Re-initialize session array with original values
session_save_path — Get and/or set the current session save path
session_set_cookie_params — Set the session cookie parameters
session_set_save_handler — Sets user-level session storage functions
session_start — Start new or resume existing session
session_status — Returns the current session status
session_unset — Free all session variables
session_write_close — Write session data and end session
```

```
PHP Session 使用介紹，啟用與清除 session
https://www.webtech.tw/info.php?tid=33

常用的 Session 函式庫
session_start：啟用一個新的或開啟正在使用中的session。
session_destroy：清除正在使用中的 session。
session_name：取得正在使用中的名稱或將名稱更新為新的名稱。
session_module_name：取得或更新正在使用中的模組。
session_save_path：存取目前使用中的 session 路徑。
session_id：存取目前使用中的 id。
session_register：註冊一組新的 session。
session_unregister：刪除一個正在使用中的 session。
session_is_registered：檢查目前使用中是否已經有此變數。
session_decode：資料解碼，解碼成功回傳 true。
session_encode：資料編碼，編碼成功回傳 true。

https://www.webtech.tw/info.php?tid=33
```
# PHP Session 使用範例說明
```
PHP Session 使用範例說明
https://www.wibibi.com/info.php?tid=135
```
