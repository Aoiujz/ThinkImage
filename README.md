## ThinkImage 是什么？

ThinkImage是一个PHP图片处理工具。目前支持图片缩略图，图片裁剪，图片添加水印和文字水印等功能。可自由切换系统支持的图片处理工具，目前支持GD库和Imagick库。在GD库下也能良好的处理GIF图片。

## ThinkImage 怎么使用？

ThinkImage的使用比较简单，你只需要引入ThinkImage类，实例化一个ThinkImage的对象并传入要使用的图片处理库类型和要处理的图片，就可以对图片进行操作了。关键代码如下：（以ThinkPHP为例，非ThinkPHP框架请使用PHP原生的文件引入方法）

	//引入图片处理库
	import('ORG.ThinkImage.ThinkImage'); 
	//使用GD库来处理1.gif图片
	$img = new ThinkImage(THINKIMAGE_GD, './1.gif'); 
	//将图片裁剪为440x440并保存为corp.gif
	$img->crop(440, 440)->save('./crop.gif');
	//给裁剪后的图片添加图片水印，位置为右下角，保存为water.gif
	$img->water('./11.png', THINKIMAGE_WATER_SOUTHEAST)->save("water.gif");
	//给原图添加水印并保存为water_o.gif（需要重新打开原图）
	$img->open('./1.gif')->water('./11.png', THINKIMAGE_WATER_SOUTHEAST)->save("water_o.gif");

## 有哪些可以使用的常量？

ThinkImage提供了部分常量，方便记忆，在使用的过程中，可以直接使用常量或对应的整型值。

	/* 驱动相关常量定义 */
	define('THINKIMAGE_GD',      1); //常量，标识GD库类型
	define('THINKIMAGE_IMAGICK', 2); //常量，标识imagick库类型

	/* 缩略图相关常量定义 */
	define('THINKIMAGE_THUMB_SCALING',   1); //常量，标识缩略图等比例缩放类型
	define('THINKIMAGE_THUMB_FILLED',    2); //常量，标识缩略图缩放后填充类型
	define('THINKIMAGE_THUMB_CENTER',    3); //常量，标识缩略图居中裁剪类型
	define('THINKIMAGE_THUMB_NORTHWEST', 4); //常量，标识缩略图左上角裁剪类型
	define('THINKIMAGE_THUMB_SOUTHEAST', 5); //常量，标识缩略图右下角裁剪类型
	define('THINKIMAGE_THUMB_FIXED',     6); //常量，标识缩略图固定尺寸缩放类型

	/* 水印相关常量定义 */
	define('THINKIMAGE_WATER_NORTHWEST', 1); //常量，标识左上角水印
	define('THINKIMAGE_WATER_NORTH',     2); //常量，标识上居中水印
	define('THINKIMAGE_WATER_NORTHEAST', 3); //常量，标识右上角水印
	define('THINKIMAGE_WATER_WEST',      4); //常量，标识左居中水印
	define('THINKIMAGE_WATER_CENTER',    5); //常量，标识居中水印
	define('THINKIMAGE_WATER_EAST',      6); //常量，标识右居中水印
	define('THINKIMAGE_WATER_SOUTHWEST', 7); //常量，标识左下角水印
	define('THINKIMAGE_WATER_SOUTH',     8); //常量，标识下居中水印
	define('THINKIMAGE_WATER_SOUTHEAST', 9); //常量，标识右下角水印