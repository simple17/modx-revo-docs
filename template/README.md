# Основной шаблон

## Файловая структура

Шаблон сайта состоит из файлов стилей, скриптов и картинок не относящихся к контенту сайта. Файлы следует располагать в директории template в корне filesystem. 
Структура директории template должна быть следующей(если не используется CSS фреймворк требующий отличную структуру):

* css - Для файлов стилей.
* js - Для файлов скриптов.
* img - Для картинок.

## Базовый шаблон MODX

	<!DOCTYPE html>
	<html>
		<head>
			[[$Head]]
		</head>
		<body>
			
			<header class="container">
				[[$Header]]
			</header>
			<div class="container">
				<div class="row">
					<div class="span4">
						<h2>Heading</h2>
						<p>Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. </p>
						<p><a class="btn" href="#">View details »</a></p>
					</div>
					<div class="span4">
						<h2>Heading</h2>
						<p>Donec id elit non mi porta gravida at eget metus. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus. Etiam porta sem malesuada magna mollis euismod. Donec sed odio dui. </p>
						<p><a class="btn" href="#">View details »</a></p>
					</div>
					<div class="span4">
						<h2>Heading</h2>
						<p>Donec sed odio dui. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Vestibulum id ligula porta felis euismod semper. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>	
						<p><a class="btn" href="#">View details »</a></p>
					</div>
				</div>
				<div class="row">
					<div class="span12">
						<h1>[[*longtitle:default=`[[*pagetitle]]`]]</h1>
						[[*content]]
					</div>
				</div>
			</div>
			<footer>
				[[$Footer]]
			</footer>
			[[$AfterFooter]]
		</body>
	</html>
	
## Основаный чанки
### Head
	<title>[[++site_name]] - [[*pagetitle]]</title>
	<base href="[[++site_url]]" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link href="css/bootstrap.min.css" rel="stylesheet" media="screen">
	<link href="css/style.css" rel="stylesheet" media="screen">
### Header
	<div class="hero-unit">
		<p class="lead">Сайт в разработке!</p>
		<p>This is a template for a simple marketing or informational website. It includes a large callout called the hero unit and three supporting pieces of content. Use it as a starting point to create something more unique.</p>
		<p><a href="#" class="btn btn-primary btn-large">Learn more »</a></p>
	</div>
### Footer
	<div class="row">
		<div class="span12">
			<p>© [[#ID-РЕСУРСА-С-НАСТРОЙКАМИ.tv.settings_company]] 2013</p>
		</div>
	</div>
### AfterFooter
	<script src="http://code.jquery.com/jquery.js"></script>
	<script src="js/bootstrap.min.js"></script>
