# PLABE_INC_wp
PLABE_INCのwpテーマ化

1、Local by Flywheelに環境作る <br>
2、settingから日本語に<br>
3、style.cssを作成

```
/* style.css */
	
@charset "utf-8";

theme Name: PLABE_INC
Author: name
Description: PLABE_INCのWordPressテーマです。
version： 1.0.0

```
4、直下にstyle.cssを配置、topページをindex.phpに変更<br>
5、zipにしてアップ。テーマとして認識。<br>
6、直下にスクリーンショットを設置 (screenshot.png  880×660px)<br>

## まずはheader.phpの作成
7、index.phpのheader部分を編集してcssのパスを通す。<br>
8、header.phpの作成

#### もともと静的HTMLのheader部分
```

<!doctype html>
<html>
<!doctype html>
<html>
<head>
<meta charset="UTF-8">
<title>PLABE_Inc</title>
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="description" content="株式会社プレイブは「いいモノを、いい空間を」提供するデザイン会社です。">
<meta property="og:url" content="https://www.plabe.jp"/>
<meta property="og:title" content="TOP" />
<meta property="og:type" content="website">
<meta property="og:image" content="images/footer_logo.png"/>
<meta property="og:site_name" content="株式会社PLABE" />
<meta property="og:locale" content="ja_JP" />
<link rel="shortcut icon" href="images/logo_tate_white.png">
<link href="https://use.fontawesome.com/releases/v5.6.1/css/all.css" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Noto+Sans&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Open+Sans&display=swap" rel="stylesheet">
<link rel="stylesheet" href="css/reset.css">
<link rel="stylesheet" href="css/common.css">
<link rel="stylesheet" href="css/style.css">
</head>

<body>
	<header>
		<div class="navigation">
			<img src="images/header_mark_and_name.png" width="8%" alt="plabe_logo">
			<ul class="menu">
				<li class="menu_item"><a href="index.html">HOME</a></li>
				<li class="menu_item"><a href="about/index.html">ABOUT US</a></li>
				<li class="menu_item"><a href="company/index.html">COMPANY</a></li>
				<li class="menu_item"><a href="mailto:info@plabe.jp?subject=%8c%8f%96%bc&amp;body=%96%7b%95%b6">CONTACT</a></li>
			</ul>
			<div class="navigation_col">
				<a href="https://www.instagram.com/plabe_inc/?hl=ja" target="_blank"><i class="fab fa-instagram"></i></a>
				<a href="https://www.facebook.com/PLABEinc/" target="_blank"><i class="fab fa-facebook-f"></i></a>
				<a class="online-store-btn" href="https://theshop.plabe.jp/" target="_blank"><p>ONLINE STORE</p></a>
			</div>
		</div>
	</header>

```


#### wp化したheader部分 (ここまでをheader.phpにする)

このページで出てくるWPのタグ<br>
```

<!-- この2つはすごくよく使います！ -->

<!-- テーマのフォルダまでのパスを出力してくれます。-->
<?php echo get_template_directory_uri(); ?>
<!-- トップページのURLを表示 -->
<?php echo home_url() ?>


<!-- 主にheadタグで使用 -->

<!-- ブログ名(サイト名)を表示 -->
<?php bloginfo('name'); ?> 

<!-- 現在のページ名を表示 -->
<?php wp_title(); ?>

<!-- ブログのdescriptionを表示 -->
<?php bloginfo( 'description' ); ?>

<!-- 直下のcss読み込む(テーマ名などの情報) -->
<?php bloginfo( 'stylesheet_url' ); ?>


```

### header.phpの完成

```

<!doctype html>
<html>
<head>
<meta charset="UTF-8">
<!-- ブログ名、各ページの記事やタイトル-->
<title><?php bloginfo('name'); ?> <?php wp_title(); ?></title>
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="description" content="<?php bloginfo( 'description' ); ?>">
<link rel="shortcut icon" href="<?php echo get_template_directory_uri(); ?>/images/logo_tate_white.png">
<!-- テーマのディレクトリ内のstyle.css読み込み -->
<link rel="stylesheet" href="<?php bloginfo( 'stylesheet_url' ); ?>">

<!-- ディスクリプションの設定 -->
<meta property="og:type" content="website">
<meta property="og:title" content="<?php the_title() ?>" />
<meta property="og:image" content="<?php echo get_template_directory_uri(); ?>/images/footer_logo.png"/>
<meta property="og:site_name" content="<?php bloginfo('name'); ?>" />

<!-- google フォント-->
<link href="https://use.fontawesome.com/releases/v5.6.1/css/all.css" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Noto+Sans&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css?family=Open+Sans&display=swap" rel="stylesheet">


<!-- css読み込み -->
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/reset.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/common.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/style.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/about.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/company.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/policy.css">

<!-- wpの様々な機能を使えるようにするタグ -->
<?php wp_head(); ?>

</head>

<body>
	<header>
		<div class="navigation">
			<img src="<?php echo get_template_directory_uri(); ?>/images/header_mark_and_name.png" width="8%" alt="plabe_logo">
			<ul class="menu">
				<li class="menu_item"><a href="<?php echo home_url() ?>">HOME</a></li>
				<li class="menu_item"><a href="<?php echo home_url() ?>/about">ABOUT US</a></li>
				<li class="menu_item"><a href="<?php echo home_url() ?>/company">COMPANY</a></li>
				<li class="menu_item"><a href="<?php echo home_url() ?>/contact">COMPANY</a>CONTACT</a></li>
			</ul>
			<div class="navigation_col">
				<a href="https://www.instagram.com/plabe_inc/?hl=ja" target="_blank"><i class="fab fa-instagram"></i></a>
				<a href="https://www.facebook.com/PLABEinc/" target="_blank"><i class="fab fa-facebook-f"></i></a>
				<a class="online-store-btn" href="https://theshop.plabe.jp/" target="_blank"><p>ONLINE STORE</p></a>
			</div>
		</div>
	</header>

```

9、header.phpとして保存して、index.phpにインクルードする。

<img src="https://github.com/55Kaerukun/PLABE_INC_wp/blob/master/img/header.png" width="800px">

```
<!-- header.phpを読み込むタグ-->
<?php get_header(); ?>
```

### footer.phpの作成

```

<footer>
	<div class="footer_nav">
		<ul class="footer_menu">
			<li class="menu_item"><a href="<?php echo home_url() ?>/about">ABOUT US</a></li>
			<li class="menu_item"><a href="<?php echo home_url() ?>/company"></li>
			<li class="menu_item"><a href="mailto:info@plabe.jp?subject=%8c%8f%96%bc&amp;body=%96%7b%95%b6">CONTACT</a></li>
			<li class="menu_item"><a href="<?php echo home_url() ?>/policy">PRIVACY POLICY</a></li>
		</ul>
		<a href="index.html"><img src="<?php echo get_template_directory_uri(); ?>/images/footer_logo.png" alt="footer_logo"></a>
		<p>© 2020 PLABE Inc. All rights reserved.</p>
	</div>
</footer>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/2.0.1/TweenMax.min.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/85188/jquery.wavify.js"></script>
<script>
	$(function(){
// 設定
var $width ='100%'; // 横幅
var $height =1000; // 高さ
var $interval = 3000; // 切り替わりの間隔（ミリ秒）
var $fade_speed = 2000; // フェード処理の早さ（ミリ秒）
$("#slide ul li").css({"position":"relative","overflow":"hidden","width":$width,"height":$height});
$("#slide ul li").hide().css({"position":"absolute","top":0,"left":0});
$("#slide ul li:first").addClass("active").show();
setInterval(function(){
var $active = $("#slide ul li.active");
var $next = $active.next("li").length?$active.next("li"):$("#slide ul li:first");
$active.fadeOut($fade_speed).removeClass("active");
$next.fadeIn($fade_speed).addClass("active");
},$interval);
});
	
//	$(function() {
//	setTimeout(function(){
//		$('.start p').fadeIn(2000);
//	},800); //0.5秒後にロゴをフェードイン!
//	setTimeout(function(){
//		$('.start').fadeOut(1500);
//	},3000); //2.5秒後にロゴ含め真っ白背景をフェードアウト！
//});
	</script>
	
</body>
</html>

```

10、footer.phpとして保存して、index.phpにインクルードする。

<img src="https://github.com/55Kaerukun/PLABE_INC_wp/blob/master/img/footer.png" width="600px">


11、index.phpの仕上げで他の部分も各所、WPのタグに書き換えましょう<br>
```
<!-- これしか使いません。-->
<?php echo get_template_directory_uri(); ?>

<?php echo home_url() ?>

```
index.phpのソース<br>
https://gist.github.com/55Kaerukun/585068d5c4c371af4d7cbd2882bf8570

### 管理画面から固定ページ制作の準備
WPでは、下層ページのことを（固定ページ）と呼びます。<br>

<img src="https://github.com/55Kaerukun/PLABE_INC_wp/blob/master/img/kanri.png" width="600px">

12、パーマリンク設定(URLのルールを設定します)

<img src="https://github.com/55Kaerukun/PLABE_INC_wp/blob/master/img/permalink.png" alt="600px">

```
カスタム構造 : /%category%/%postname%
```
参考 : https://liginc.co.jp/web/wp/customize/148458

現状このような感じなので、下層ページを固定ページにしていきましょう！


<img src="https://github.com/55Kaerukun/PLABE_INC_wp/blob/master/img/directory.png" width="600px">

13、下層ページ(固定ページ)テンプレートの作成

### page.php
```

<!-- header.phpの読み込み -->
<?php get_header(); ?>
 
  <!-- 固定ページのタイトルが表示されます。 -->
  <h1><?php the_title(); ?></h1>

  
  <!-- 投稿があるかifで判断してあったら表示する、wpのおまじない的な書き方-->
  <?php if(have_posts()): while(have_posts()):the_post(); ?>
  
  	<!-- 固定ページのエディタ内の内容表示 -->
  	<?php the_content(); ?>
  
  <?php endwhile; endif; ?>

 
<!-- footer.phpの読み込み -->
<?php get_footer(); ?>

```

固定ページに書き写す。（画像URLの置き換えがちょっと大変）

