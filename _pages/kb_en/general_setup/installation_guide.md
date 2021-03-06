---
lang: en
layout: article_with_sidebar
updated_at: '2017-07-19 22:19 +0400'
identifier: ref_VG5mIoLT
title: Installation Guide
version: X-Cart 5.2.5 and later
categories:
  - General setup
published: true
order: 0
---


## Introduction

This guide describes the process of installing X-Cart 5 on your server.

## Table of Contents

*   [Introduction](#introduction)
*   [Table of Contents](#table-of-contents)
*   [Server requirements](#server-requirements)
    *   [Hardware requirements](#hardware-requirements)
*   [Browser compatibility](#browser-compatibility)
*   [Installation process](#installation-process)
    *   [Upload X-Cart 5 onto your server](#upload-x-cart-5-onto-your-server)
    *   [Create an empty database](#create-an-empty-database)
    *   [Run the installation wizard and follow the steps](#run-the-installation-wizard-and-follow-the-steps)
        *   [Step 1\. License agreement](#step-1-license-agreement)
        *   [Step 2\. Creating administrator account](#step-2-creating-administrator-account)
        *   [Step 3\. Environment check](#step-3-environment-check)
        *   [Step 4\. Configuring X-Cart 5](#step-4-configuring-x-cart-5)
        *   [Steps 5 and 6\. Some magic](#steps-5-and-6-some-magic)
        *   [Step 7\. Installation completed](#step-7-installation-completed)
*   [Possible installation problems](#possible-installation-problems)
    *   [1\. Problems with connection to database](#problems-with-connection-to-database)
    *   [2. Permission checking failed](#permissionchecking-failed)
    *   [3. Disabled functions](#disabled-functions)
    *   [4\. Disabled PHP extensions](#disabled-php-extensions)
    *   [5\. HTTPS bouncer is not installed](#https-bouncer-is-not-installed)

## Server requirements

Before you get started you might want to check whether your web server spec meets system requirements. Even if you don't, the installation wizard will alert you during the process that something is not set up properly.

Here is the system requirements list:

*   PHP __5.4__ or higher
*   __PDO__ extension with MySQL driver
*   __Phar__ extension
*   __mbstring__ extension is highly recommended (though X-Cart has a polyfill for it, native extension will speed up string processing)
*   MySQL 5.1.31 or higher. You can also use MySQL-compatible database engine MariaDB.
*   200-300Mb of disk space
*   libCURL module support (minimum required CURL version is 7.39.0; version 7.43.0 is recommended)
*   `ini_set` enabled
*   `safe_mode` disabled
*   `file_uploads`  enabled
*   `post_max_size` set to 2M+ and larger than the `upload_max_filesize` value (critical for installation)
*   `upload_max_filesize` set to 2M or higher
*   `magic_quotes_runtime` disabled (for PHP versions prior to 5.4.x)
*   `memory_limit` set to 128M or higher (if you are using 64-bit processors in your server environment, the `memory_limit value` must be 256M or higher)
*   GDLib 2.0 or ImageMagick (recommended for proper image resizing routines)
*   {% link "PHP time limit" ref_xqnpttd4 %} properly set according to your server config
*   mod_rewrite-like components to enable proper work of {% link "SEO-friendly URLs" ref_nJxrzFEZ %}
*   if xdebug is enabled, `xdebug.max_nesting_level` must be set to 300
*   if OPcache is enabled, `opcache.save_comments` and `opcache.load_comments` must be true (set to "1"). Any other cachers should not strip comments from the code too.

### Hardware requirements

<table class="ui celled padded compact small table">
  <thead>
    <tr>
      <th style="text-align: center;" class="confluenceTh">&nbsp;</th>
      <th colspan="3" style="text-align: center;" class="confluenceTh">Traffic</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th style="text-align: center;" class="confluenceTh">Catalog size</th>
      <th class="confluenceTh"><span style="color: rgb(0,0,0);">up to 100 visitors/day</span>
      </th>
      <th class="confluenceTh"><span style="color: rgb(0,0,0);">up to 5 000 visitors/day</span>
      </th>
      <th class="confluenceTh"><span style="color: rgb(0,0,0);">up to 15 000 visitors/day</span>
      </th>
    </tr>
    <tr>
      <th class="confluenceTh">1 500 SKUs</th>
      <td class="confluenceTd"><span style="color: rgb(0,0,0);">a good shared/cloud hosting</span>
      </td>
      <td class="confluenceTd">
        <p>VPS / Dedicated server</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual-core CPU</li>
          <li>RAM 1 GB</li>
          <li>250 Mbps connection</li>
        </ul>
      </td>
      <td class="confluenceTd">
        <p>Dedicated server</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual CPU dual-core</li>
          <li>RAM 8 GB, SAS HDD</li>
          <li>500 Mbps connection</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th class="confluenceTh">20 000 SKUs</th>
      <td class="confluenceTd"><span style="color: rgb(0,0,0);">a good shared/cloud hosting</span>
      </td>
      <td class="confluenceTd">
        <p>VPS / Dedicated server</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual-core CPU</li>
          <li>RAM 2 GB</li>
          <li>250 Mbps connection</li>
        </ul>
      </td>
      <td class="confluenceTd">
        <p>Dedicated server</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual CPU dual-core</li>
          <li>RAM 16 GB, SAS HDD</li>
          <li>500 Mbps connection</li>
        </ul>
      </td>
    </tr>
    <tr>
      <th class="confluenceTh">300 000 SKUs</th>
      <td class="confluenceTd">
        <p>VPS hosting</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual-core CPU</li>
          <li>RAM 2 GB</li>
          <li>100 Mbps connection</li>
        </ul>
      </td>
      <td class="confluenceTd">
        <p>Dedicated server</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual-core CPU</li>
          <li>RAM 4 GB, SAS HDD</li>
          <li>250 Mbps connection</li>
        </ul>
      </td>
      <td class="confluenceTd">
        <p>Dedicated server</p>
        <ul style="margin-left: 1.6em;">
          <li>Dual CPU quad-core</li>
          <li>RAM 16 GB, SAS HDD</li>
          <li>500 Mbps connection</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## Browser compatibility

X-Cart 5 supports following browsers:

*   Google Chrome (latest version)
*   Safari (latest versions for MacOS X v10.8 and later, iOS7 and later)
*   Firefox (latest version)
*   Internet Explorer 10 and higher

## Installation process

This article covers the process of installation for X-Cart versions 5.2.5 and later. For earlier versions the process is similar; however, the installation wizard steps are a bit different. 

A video guide for installing X-Cart is available:

**Published on Jan 18, 2017**
<iframe class="youtube-player" type="text/html" style="width: 800px; height: 450px" src="https://www.youtube.com/embed/N21P9jBh2sA" frameborder="0"></iframe>


### Upload X-Cart 5 onto your server

1.  Download the most recent X-Cart 5 package from this page: [http://www.x-cart.com/download.html](http://www.x-cart.com/download.html)
2.  Upload the downloaded package onto your server.
3.  Unpack the X-Cart 5 archive to the web-root directory of your server. You can do it using the archive tools of your Control panel or using the following command via SSH: 

    for zip archive: 

    ```php
    unzip x-cart-5.3.4.4-en.zip
    ```

    for tgz archive: 

    ```php
    tar -xzpf x-cart-5.3.4.4-en.tgz
    ```

    (Be sure to replace the file name with the actual name of the archive you have downloaded).

### Create an empty database

Create an empty database in your MySQL storage.

### Run the installation wizard and follow the steps

#### Step 1\. License agreement

Open the link: **`http://<your-domain>/<x-cart-5-directory>/install.php`** in your browser. It will start the installation wizard. Accept the license agreement and click **Next**.

![]({{site.baseurl}}/attachments/524295/8719150.png)

#### Step 2\. Creating administrator account

At this step, you need to define the email and password for your store's administrator profile. Once you are done with that, X-Cart 5 will send a notification to the email address you have specified along with some service info.

 ![]({{site.baseurl}}/attachments/524295/8719151.png)

#### Step 3\. Environment check

Now the installation wizard will check whether your server meets the system requirements for X-Cart 5\. It will report if the requirements are not met. If everything is OK, you will be automatically redirected to the next step.

![]({{site.baseurl}}/attachments/524295/8719154.png)

#### Step 4\. Configuring X-Cart 5

At this step you need to define the basic settings of your X-Cart 5 installation. Typically the page looks like the snapshot below:

![]({{site.baseurl}}/attachments/524295/8719155.png)

Let's walk through the settings you need to adjust. The first group of settings on this page is as follows:

*   **MySQL server name**: The name of your MySQL server. In most cases, it is **localhost**. If it is different, your host has likely notified you about it.
*   **MySQL database name**: The name of the database that will be used by your X-Cart 5 store (You have created this database earlier at the step "**Create an empty database**").
*   **MySQL username** and **MySQL****password**: The credentials needed to access the X-Cart 5 database on your MySQL server.
*   **Install a sample catalog**:Whether you want to have sample data in your X-Cart installation for you to experiment with. If this is your first experience with X-Cart 5, we strongly recommend enabling this check box.

Below you will find links to some advanced configuration settings. Click on a link to access the respective settings section.

Here's the **Advanced MySQL settings** section:

![]({{site.baseurl}}/attachments/524295/8719156.png)

In this section, you can adjust the following settings:

*   **MySQL server port**: The port for connection to your MySQL server. In most cases, it is **3306** and can be omitted.
*   **MySQL server socket**: This should be defined if the connection to your MySQL server is done via a socket, not via specifying a server and a port. To be honest, it is quite a rare situation, and you almost always run the connection via specifying a server and a port. Anyway, if using a socket is your case, **do not specify** a server and a port. Just define the socket.
*   **MySQL tables prefix**: The prefix of tables in order to distinguish ones related to X-Cart from others in your database. However, it is highly recommended to use a separate database for X-Cart 5 and not to put any other applications' tables into this database.

And here is the **Advanced server settings** section:

![]({{site.baseurl}}/attachments/524295/8719157.png)

In this section, you can adjust the following settings:

*   **Web server name**: The domain name at which your store will be accessible from the Internet. The installation script defines it automatically, so you can just keep what you see in this field.
*   **Secure web server name**: The domain name for secure connections (HTTPS). Usually, it copies the main domain name; however, in some cases your hosting may provide a different domain name for your secure web server.
*   **X-Cart 5 web directory**:The web-accessible directory of your server or hosting account where X-Cart will be installed. The installation script defines it automatically.
*   **Default time zone**: Your store's time zone. This needs to be defined to correctly set up the time, dates, number formats, etc.

Once you are done adjusting these settings, click **Next**.

#### Steps 5 and 6\. Some magic

These two steps are dedicated to some boring work that X-Cart 5 has to do. It creates MySQL tables, cache, development code and so on. These steps are fully automated, so you just need to wait and let X-Cart 5 do the job. Usually it takes less than a minute.

![]({{site.baseurl}}/attachments/524295/8719158.png)

#### Step 7\. Installation completed

Now the installation process has been completed. You can use the links provided to access your store's customer front end and admin area. 

![]({{site.baseurl}}/attachments/524295/8719159.png)

## What to do next?

X-Cart store is ready to work and the whole world is open to you. You might want to {% link 'fill your products catalog' ref_fhzzxDTy %}, setup {% link 'shipping' ref_7tvT7GEK %} and {% link 'payment' ref_Jq6Bsdrt %} methods first.

Also, you definitely should customize your store's {% link 'look and feel' ref_bzUBJufx %} and {% link 'setup SEO-friendly URLs' ref_nJxrzFEZ %} by configuring your server.

P.S. And don't forget about {% link 'security measures' ref_secureconfig %}!

## Possible installation problems

If you face any problem during **Environment** check, you get a general instruction about how to fix it. You can pass it to your developers or hosting team and they will be able to take care of it. This section describes typical problems you may encounter and what you can do in order to fix them.

### 1\. Problems with connection to database

Such problems generally mean that MySQL credentials were specified incorrectly or MySQL server/database is incorrectly set up.

Examples:

1.  ```php
    FATAL ERROR: Cannot connect to the specified MySQL server : SQLSTATE[28000] [1045] Access denied for user 'tony'@'localhost' (using password: YES) Click the 'BACK' button and review the MySQL server settings provided
    ```

    Such error message means that your MySQL login or password are incorrect. You need to double check your MySQL credentials and input them correctly.
    _Note: sometimes this problem can happen even when you correctly specify login and password, but there is actually the problem with **MySQL user** preferences. You can check it in a following manner: go to the **phpMyAdmin** console of your server and check the MySQL user's **Host** field. If it is specified as **% (Any host)**, then you should remove this MySQL user and create new one with the same name but specify Host field as **localhost (Local)**._

2.  ```php
    FATAL ERROR: Cannot connect to specified MySQL server : SQLSTATE[HY000] [1044] Access denied for user 'tony'@'localhost' to database 'xcart' Click the 'BACK' button and review the MySQL server settings you have provided.
    ```

    Such error message means that your MySQL login/password allowed X-Cart to log to MySQL server, but your database does not exist or your MySQL user cannot access it. You should log into your MySQL dashboard and make sure that your database exists and the MySQL user has an access to it.

3.  Other MySQL errors like:

    ```php
    FATAL ERROR: Cannot connect to the specified MySQL server : SQLSTATE[HY000] [2002] No connection could be made because the target machine actively refused it.
    FATAL ERROR: Cannot connect to the specified MySQL server : SQLSTATE[HY000] [2002] The requested address is not valid in its context.
    FATAL ERROR: MySQL server doesn't support InnoDB engine. It is required for X-Cart 5 operation(current version is 5.1.73-cll)
    ```

    mean that there is something wrong with your MySQL server settings. You need to send such error message to your hosting team and ask them to fix it.

### 2. Permission checking failed

Such error messages may look like this:

```php
Permissions checking failed. Please make sure that the following file permissions are assigned (UNIX only):
chmod 666 /home/tony/public_html/xcart/.htaccess

or

Permissions checking failed. Please make sure that the following file permissions are assigned (UNIX only):
chmod 0777 /Applications/MAMP/htdocs/xcart/
find /Applications/MAMP/htdocs/xcart/var -type d -exec chmod 0777 {} \;
find /Applications/MAMP/htdocs/xcart/var -type f -exec chmod 0666 {} \;
find /Applications/MAMP/htdocs/xcart/images -type d -exec chmod 0777 {} \;
find /Applications/MAMP/htdocs/xcart/images -type f -exec chmod 0666 {} \;
find /Applications/MAMP/htdocs/xcart/files -type d -exec chmod 0777 {} \;
find /Applications/MAMP/htdocs/xcart/files -type f -exec chmod 0666 {} \;
chmod 666 /Applications/MAMP/htdocs/xcart/etc/config.php
chmod 666 /Applications/MAMP/htdocs/xcart/.htaccess
```

Such error messages mean that some files do not have suitable permissions and you must correct them manually. Copy the instructions suggested and run them using **Terminal** section in your Control Panel.

There are several examples of error message for better understanding of the process:

1.  ```php
    chmod 666 /home/tony/public_html/xcart/.htaccess
    ```

    Such instruction means that all users must have readable and writable permissions for the  `/home/tony/public_html/xcart/.htaccess` file.

2.  ```php
    find /Applications/MAMP/htdocs/xcart/var -type d -exec chmod 0777 {} \;
    ```

    Such instruction means that all users must have all possible permissions (`chmod 0777`) to all directories `(-type d`) inside `/Applications/MAMP/htdocs/xcart/var` folder.

3.  Similarly to above

    ```php
    find /Applications/MAMP/htdocs/xcart/files -type f -exec chmod 0666 {} \;
    ```

    this instruction means that all users must have readable and writeable permissions (`chmod 0666`) to all files `(-type f`) inside `/Applications/MAMP/htdocs/xcart/var` folder.

### 3. Disabled functions

Your hosting company may disable several default PHP functions and X-Cart 5 cannot work while they are disabled. In this case, you will get the error message like this:

```php
There are disabled functions (phpinfo, escapeshellcmd, escapeshellarg, openlog, syslog, exec, popen) that may be used by software in some cases and should be enabled
```

The list of disable functions can be different.

In order to solve this issue, you should send the list of disabled PHP functions (`phpinfo, escapeshellcmd, escapeshellarg, openlog, syslog, exec, popen` from the example above) to your hosting team and ask to enable them in your account.

### 4\. Disabled PHP extensions

If you are getting an error message like this: 

```php
PDO extension with MySQL support must be installed.
```

it means that your server does not support library to work with MySQL via PDO. PDO is an extension that ensures safe work with database and it is required for proper X-Cart 5 work. Ask your hosting team to enable it for your hosting account.

If you are on local machine, you need to edit your php.ini file, uncomment the following line there and restart Apache.

```php
;extension=pdo_mysql.so

it should become
extension=pdo_mysql.so
```

### 5\. HTTPS bouncer is not installed

If you are getting an error message like this:

```php
libcurl extension not found
```

it means that libCurl system library is not enabled in your account and your PHP scripts cannot create connections to other services. Ask your hosting team to enable libCurl for you.

{% link "Setting up cURL" ref_sshnMtN7 %} article may be helpful if you are installing X-Cart 5 on your local server.
