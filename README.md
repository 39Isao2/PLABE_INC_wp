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
7、index.phpのheader部分を編集してcssのパスを通す。

## header.phpの作成
### 8、index.phpのために、まずはheadタグ内を書き換える

#### もともと静的HTMLのheadタグ
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

```


#### wp化したheadタグ

これがよく使うので覚えましょう。テーマのフォルダまでのパスを出力してくれます。
```
<?php echo get_template_directory_uri(); ?>

```
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

<!-- wpの様々な機能を使えるようにするタグ -->
<?php wp_head(); ?>

</head>

```


### もともとのheaderタグ
```

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

