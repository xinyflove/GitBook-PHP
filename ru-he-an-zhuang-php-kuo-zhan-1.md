# 如何安装PHP扩展

PECL（PHP Extension Community Library）是 PHP 的扩展库，它提供了一些 PHP 扩展，可以增强 PHP 的功能。所有扩展包列表查询地址：[https://pecl.php.net/package-stats.php](https://pecl.php.net/package-stats.php)

## Window 上安装PHP扩展

在PECL上找到所需要的PHP扩展，点击有DLL标识的链接地址，进行对应PHP版本的资源下载，但是你需要注意以下几点问题：

* VC6 是运行于 Apache 服务器；
* Thread safe（线程安全）是以模块形式运行在 Apache 上，如果你以 CGI 的模式运行 PHP，请选择非线程安全模式（non-thread safe）；
* VC9 是运行于 IIS 服务器上；
* 下载完你需要的二进制包后，解压压缩包，将 php\_mongodb.dll 文件添加到你的PHP扩展目录中（ext）。ext 目录通常在 PHP 安装目录下的 ext 目录。

打开 php 配置文件 php.ini 添加以下配置：

```
extension=php扩展.dll
```

重启服务器，通过浏览器访问phpinfo，如果安装成功，就会看到安装扩展的信息。

## Linux 上安装 PHP 扩展

### 命令行安装

你可以在 Linux 中执行以下命令来安装 MongoDB 的 PHP 扩展驱动

```
$ sudo pecl install mongodb
```

使用php的pecl安装命令必须保证网络连接可用以及root权限。

### PECL包安装

在PECL上找到所需要的PHP扩展，点击有.tgz标识的链接地址，进行对应PHP版本的资源下载。

已安装MongoDB扩展为例

```
$ wget http://pecl.php.net/get/mongodb-1.5.2.tgz
$ cd /mongodb-1.5.2
$ phpize
$ ./configure
$ make && make install
```

如果你的 php 是自己编译的，则安装方法如下(假设是编译在 /usr/local/php目录中)：

```
$ wget http://pecl.php.net/get/mongodb-1.5.2.tgz
$ cd /mongodb-1.5.2
$ /usr/local/php/bin/phpize
$ ./configure --with-php-config=/usr/local/php/bin/php-config
$ make && make install
```

安装成功后，会有类似以下安装目录信息输出：

```
...
Installing shared extensions:     /usr/lib/php/extensions/debug-non-zts-20151012/
```

执行以上命令后，你需要修改php.ini文件，在 php.ini 文件中添加mongo配置，配置如下：

```
extension_dir=/usr/lib/php/extensions/debug-non-zts-20151012/
extension=mongodb.so
```

> **注意：**你需要指明 extension\_dir 配置项的路径。
>
> 可以通过以下命令查看目录地址：
>
> ```
> $ php -i | grep extension_dir
>   extension_dir => /usr/lib/php/extensions/debug-non-zts-20151012 =>
>                    /usr/lib/php/extensions/debug-non-zts-20151012
> ```

## MAC 中安装 PHP扩展驱动

你可以使用 autoconf 安装 PHP 扩展驱动。

你可以使用 Xcode 安装 PHP 扩展驱动。

如果你使用 XAMPP，你可以使用以下命令安装 PHP 扩展驱动：

以安装MongoDB扩展为例

```
sudo /Applications/XAMPP/xamppfiles/bin/pecl install mongo
```

如果以上命令在XMPP或者MAMP中不起作用，你需要在 Github上下载兼容的预编译包。

然后添加 extension=mongodb.so 配置到你的 php.ini 文件中。
