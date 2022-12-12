Reference:
https://wordpress.stackexchange.com/questions/176804/passing-a-variable-to-get-template-part

## Passing variables to template parts

Parent template file (page.php, ...):

```php
<?php
$bar = 'bar';

// get helper-my-template.php
get_template_part(
    'template-parts/helper',
    'my-template',
    array(
        'foo' => $bar, // passing this array possible since WP 5.5
    )
);
?>
```

In the component file (helper-my-template.php):

```php
<?php

/**
 * @var array $args
 */

$foo = $args['foo'];

?>

<h1><?php echo $foo; ?></h1>

<?php // will print 'bar' ?>
```

### Real example:

page-howtosell.php

```php
<?php
/*
Template Name: How to sell
*/
get_header();
?>

<section>
	<p><?php echo ('how to sell page') ?></p>
	<?php get_template_part( '/components/process', 'title', array(
		'title' => 'お買取方法',
		'modifiers' => "test"
	));?>
		<?php get_template_part( '/components/process', 'title', array(
		'title' => '宅配買取',
		'modifiers' => ""
	));?>
</section>
```

/components/process-title.php

```php
<?php

/**
 * @var array $args
 */

$title = $args['title'];
$modifiers = $args['modifiers'];
?>
<h2 class="process__title<?php $modifiers ? print " process__title--$modifiers" :  print ''?>">
	<?php echo $title; ?>
</h2>
```
