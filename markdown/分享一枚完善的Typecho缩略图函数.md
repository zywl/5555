分享一枚完善的Typecho缩略图函数
***
#代码如下:

```php
<?php
if (!defined('__TYPECHO_ROOT_DIR__')) exit;
define("Yodu_Version", "1.5.0体验版");
function themeConfig($form) {  echo '<p style="font-size:16px;text-align:center;"><font color="#38b48b">我做模板就是各种复制粘贴</font></p>';
 
 $slimg = new Typecho_Widget_Helper_Form_Element_Select('slimg', array(
        'showon'=>'有图文章显示缩略图，无图文章随机显示缩略图',
        'Showimg' => '有图文章显示缩略图，无图文章只显示一张固定的缩略图',      
         
    ), 'showon',
    _t('缩略图设置'), _t('默认选择“有图文章显示缩略图，无图文章随机显示缩略图”'));
    $form->addInput($slimg->multiMode());
 
}
 
 
 
/** 输出文章缩略图 */
function showThumbnail($widget)
{ 
    // 当文章无图片时的默认缩略图
    $dir = './usr/themes/blcd/images/';
    $n=sizeof(scandir($dir))-2;
    $rand = rand(1,6); // 随机6张缩略图 图片有几张改几张
    $random = $widget->widget('Widget_Options')->themeUrl . '/images/' . $rand . '.jpg'; // 随机缩略图路径
 
if(Typecho_Widget::widget('Widget_Options')->slimg && 'Showimg'==Typecho_Widget::widget('Widget_Options')->slimg
){
  $random = $widget->widget('Widget_Options')->themeUrl . '/images/1.jpg'; //无图时只显示固定一张缩略图
}
 
$cai = '';//这里可以添加图片后缀，例如七牛的缩略图裁剪规则，这里默认为空
    $attach = $widget->attachments(1)->attachment;
    $pattern = '/\<img.*?src\=\"(.*?)\"[^>]*>/i'; 
  $patternMD = '/\!\[.*?\]\((http(s)?:\/\/.*?(jpg|png))/i';
    $patternMDfoot = '/\[.*?\]:\s*(http(s)?:\/\/.*?(jpg|png))/i';
if (preg_match_all($pattern, $widget->content, $thumbUrl)) {
$ctu = $thumbUrl[1][0].$cai;
    }
 
//如果是内联式markdown格式的图片
  else   if (preg_match_all($patternMD, $widget->content, $thumbUrl)) {
$ctu = $thumbUrl[1][0].$cai;
    }
    //如果是脚注式markdown格式的图片
    else if (preg_match_all($patternMDfoot, $widget->content, $thumbUrl)) {
$ctu = $thumbUrl[1][0].$cai;
    }
 
 else
if ($attach && $attach->isImage) {
 
$ctu = $attach->url.$cai;
    } 
else 
 
if ($widget->tags) {
foreach ($widget->tags as $tag) {
 
    $ctu = './usr/themes/blcd/images/' . $tag['slug'] . '.jpg';//图片目录 images 自行修改目录名
 
    if(is_file($ctu))
    {
$ctu = $widget->widget('Widget_Options')->themeUrl . '/images/' . $tag['slug'] . '.jpg';//图片目录  images 自行修改目录名
    }
    else
 {
       $ctu = $random;
    }
break;
}
}
else {
$ctu = $random;
}
if(Typecho_Widget::widget('Widget_Options')->slimg && 'showoff'==Typecho_Widget::widget('Widget_Options')->slimg
){
if($ctu== $random)
echo '';
else
if($widget->is('post')||$widget->is('page')){
echo $ctu;
}else{
echo '<div class="index-img"><div class="tutu"><img class="b-lazy" src="'   //图片样式 该这里
.$widget->widget('Widget_Options')->themeUrl .
'/images/load.gif" data-src="'
.$ctu.
'" itemprop="image" data-no-instant/></div></div>';
}
}else{
if(Typecho_Widget::widget('Widget_Options')->slimg && 'allsj'==Typecho_Widget::widget('Widget_Options')->slimg
){
  $ctu = $random;
}
echo $ctu;
}
}
 
?>
```

代码扣自"QQ爹主题模板"！
