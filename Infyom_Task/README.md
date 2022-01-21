## 作業三：Laravel 建立與 Infyom 套件使用

### 環境建置
Macbook 環境使用 XAMPP-VM

### 建立Laravel環境

1. 先安裝 [composer](https://getcomposer.org/download/) 管理php套件

2. 到 /opt/lampp/htdocs/ 目錄下創建 laravel專案

      `composer create-project --prefer-dist laravel/laravel infyomDemo`

3. 修改demo目錄下.env 在這之前先下載vim[註1]

      - DB_DATABASE=infyomDemo  *並新增同名數據庫*

      - 執行 `php artisan migrate`

4. 修改storage權限`sudo chmod -R 777 storage`

5. 啟動laravel服務`php artisan serve`

### infyom使用

`composer require infyomlabs/laravel-ui-adminlte`

1. composer.json require新增 

```
"infyomlabs/laravel-generator": "^3.0",
"laravelcollective/html": "^6.2",
"infyomlabs/adminlte-templates": "^3.0",
"laravel/ui": "^3.0"
```

`composer update`


2. config/app.php 新增 

```
'Form'      => Collective\Html\FormFacade::class,
'Html'      => Collective\Html\HtmlFacade::class,
'Flash'     => Laracasts\Flash\Flash::class,
```

`php artisan vendor:publish --provider="InfyOm\Generator\InfyOmGeneratorServiceProvider"`

`php artisan infyom:publish`

`php artisan ui bootstrap --`

`php artisan infyom.publish:layout `

`php artisan infyom:scaffold Category`

```
name string text
required
exit
```

[註1] 下載vim
```
sudo apt-get update
sudo apt-get install apt-file
sudo apt-file update
sudo apt-get install vim
```
參考連結 [Youtube Laravel Package Tutorial](https://youtu.be/-V6RUmAXMEA)
