## 確認pecl php bin version
pecl sqlsrv有限制某個版本應該使用的php版本，安裝時需確認php版本
```
pecl version
```

## 更改pecl php bin version
如果有需要更改pecl php bin version
```
＃設定pecl php bin version
pecl config-set php_bin /usr/local/Cellar/php56/5.6.32_8/bin/php

＃設定php擴充套件目錄
pecl config-set ext_dir /usr/local/Cellar/php56/5.6.32_8/lib/php/extensions/no-debug-non-zts-20131226
```

## 透過pecl安裝 
[pecl sqlsrv](https://pecl.php.net/package/sqlsrv)
[pecl pdo_sqlsrv](https://pecl.php.net/package/pdo_sqlsrv)
```
# 安裝pdo_sqlsrv
pecl install pdo_sqlsrv

# 安裝sqlsrv
pecl install sqlsrv

# 選擇版本
pecl install sqlsrv-5.2.0
```

如果php版本不符合則出現
```
pecl/sqlsrv requires PHP (version >= 7.0.0), installed version is 5.6.32
No valid packages found
install failed
```

## 自行下載編譯安裝
執行完後pdo_sqlsrv.so會在當初設定pecl ext_dir這目錄下，可透過pecl config-show查看
```
#解壓縮
tar zxvf pdo_sqlsrv-5.2.0.tgz

#進目錄
cd pdo_sqlsrv-5.2.0

#根據php版本進到bin執行phpize
/usr/local/opt/php@7.1/bin/phpize

# 編譯
./configure

# 安裝
sudo make install
```
sqlsrv也是根據上面步驟

## php設定
打開php.ini加入以下，檔案路徑請自行修改
```
[sqlsrv]
extension="/usr/local/Cellar/php@7.1/7.1.13_24/lib/php/extensions/no-debug-non-zts-20160303/sqlsrv.so"
[pdo_sqlsrv]
extension="/usr/local/Cellar/php@7.1/7.1.13_24/lib/php/extensions/no-debug-non-zts-20160303/pdo_sqlsrv.so"

```
## 確認sqlsrv/pdo_sqlsrv是否已加載
![sqlsrv](/image/sqlsrv.png)
![pdo_sqlsrv](/image/pdo_sqlsrv.png)

## 安裝ODBC
參考手冊[Microsoft ODBC Driver](https://docs.microsoft.com/zh-tw/sql/connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server?view=sql-server-2017#microsoft-odbc-driver-131-for-sql-server)

![pdo_odbc](/image/pdo_odbc.png) 
