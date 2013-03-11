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
	$img->water('./11.png', THINKIMAGE_WATER_SOUTHEAST)->save("water{$id}.gif");