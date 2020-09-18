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

```
<!-- とりあえずheadタグ内ここにソース -->
<head>
<title><?php bloginfo('name'); ?> <?php wp_title(); ?></title>
<link rel="stylesheet" href="<?php bloginfo( 'stylesheet_url' ); ?>">
<meta property="og:url" content="<?php echo home_url(); ?>"/>
<meta property="og:title" content="<?php the_title() ?>" />
<meta property="og:image" content="<?php echo get_template_directory_uri(); ?>/images/footer_logo.png"/>
<link rel="shortcut icon" href="<?php echo get_template_directory_uri(); ?>/images/logo_tate_white.png">
<meta property="og:site_name" content="<?php bloginfo('name'); ?>" />
<link rel="shortcut icon" href="<?php echo get_template_directory_uri(); ?>/images/logo_tate_white.png">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/reset.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/common.css">
<link rel="stylesheet" href="<?php echo get_template_directory_uri(); ?>/css/style.css">

<!-- wpの様々な機能を使えるようにするタグ -->
<?php wp_head(); ?>

</head>

```
