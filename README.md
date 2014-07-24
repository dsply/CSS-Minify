CSS-Minify
==========

Reducing codes css in php.

	<?php include_once('minify.php') ?>

And minify.php :

	<style media="all" rel="stylesheet" type="text/css">
	<?php ob_start("minify");
	function minify($buffer) {
	$buffer = preg_replace('!/\*[^*]*\*+([^/][^*]*\*+)*/!', '', $buffer);    		
	$buffer = str_replace(array("\r\n", "\r", "\n", "\t", '  ', '    ', '    '), '', $buffer);
	$buffer = str_replace(array(' } ',' }','} ',';}'), '}', $buffer);
	$buffer = str_replace(array(' { ',' {','{ '), '{', $buffer);
	$buffer = str_replace(array(' : ',' :',': '), ':', $buffer);
	return $buffer; }
	include('assets/css/normalize.css');
	include('assets/css/styles.css');
	ob_end_flush(); ?>
	</style>
