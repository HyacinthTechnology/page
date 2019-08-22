# 关于
PHP-page是一个轻量级的分页类


# 需求
对低版本做了向下支持，但建议使用 PHP 5.3 +

# 安装
```shell
composer require hyacinth/page
```
```php
use HyacinthTechnology\Pager;
```


# 示例
```php
<?php
    /*
     * 数据分页
     * $page 当前页数
     * $PageCount 数据库查询的总记录数
     */
	function pager($page,$PageCount){
        $pag = new Pager();
        $pag->AbsolutePage = $page; //当前锁定页
        $PageCount = ($PageCount + 10 - 1) / 10; //计算页数
        $pag->PageCount = intval($PageCount);   //总页数量
//        $pag->FirstPageLink = '/home/1'; //首页链接
        $pag->Size = 10;   //页码尺寸
		/*
		 * ToString(参数)
		 * 1 分页
		 * 2 简易分页
		 * 3 只显示、上一页和下一页
		 */
		$pageCodeHtml = $pag->ToString(1); //获得分页过后的html
        echo $pageCodeHtml; //将输出以下内容
    }
	//接受页面传递过来的页码
	$pager = $_GET['page'];
	 pager($pager,150);
```