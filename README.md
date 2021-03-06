GreenPHP
===
###框架特色：
专为多平台应用开发订制。清晰的MVC模式，集成常用功能类库，经历三年线上运行保持稳定！
###框架包含：
    * RestApi
    * 自动生成
    * Api文档及测试
    * Web页面开发
    * 后台管理
###目录说明：
    -apps  项目文件
		-web  前端项目
		-admin 后台管理项目
	 -core 公共文件与配置
		-config 项目配置文件
		-extends 项目扩展类
		-library 框架类库
		boot.inc.php 框架初始化
	 -static 前端静态脚本文件
	 -temp 模板编译目录，Linux中需配置读写权限
	
###如何访问：
	前端页面：http://host/dir/view/module/phpfilename
	后台页面：http://host/dir/admin/module/phpfilename
	host 主机域名
	dir 定向到框架根目录（即 index.php 所在目录）
	view 或 admin 固定（区分前台与后台可在.htaccess文件修改）
	module 即apps项目下的目录名
	phpfilename 即 apps 项目目录下的php文件名(不包含php后缀)
	如要访问 htdocs/apps/admin/mgr/login.php 文件
	URL为 http://localhost/admin/mgr/login
		
###使用配置：
	Config::addPath(dirname(__FILE__).'/config/'); //设置配置目录
	$conf = Config::get('filename.conf/arraykey'); //多维数组可像访问目录一样增加"/"来获取
###使用DB：
    $db = Database::connect(Config::get('db.conf/default'),true);
    $insertid = $db->insertInto(’tablename‘, array('field'=>'value'))->execute();
    $bool = $db->delete('tablename')->where('field','value')->execute();
    $bool = $db->update('tablename')->set(array('field'=>'value'))->where('field',$value)->execute();
    $result = $db->from('tablename')->where('field',$value)->fetchAll();
    还可以直接使用PDO
    $pdo = $db->getPdo();
    $pdo->query($sql)->fetchAll();
    
    DB集成FluentPDO，更多功能请查阅
    http://fluentpdo.com/documentation.html#todo
##使用模板
	php中加载模板：
	$assign = array ('name'=>'GreenPHP');
	$tpl = new Tpl(Config::get ('tpl.conf/web'));
	$tpl->display ('index.html', $assign);
	模板标签：
	输出变量使用 {$name}
	PHP代码使用 <!--{phpcode}-->
	循环列表如：
	<!--{foreach($list as $key=>$item):}-->
	    {$item} //输出列表变量
	<!--{endforeach;}-->

