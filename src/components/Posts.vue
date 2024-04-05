<script setup>
	const props = defineProps(['post']);
</script>

<template>
	<article>
		<h1>{{ post.title }}</h1>
		<p>{{ post.body }}</p>
	</article>
</template>

<style scoped>
	article {
		border: 1px solid aqua;
		border-radius: 16px;
		margin: 20px 0;
		width: 500px;
		padding: 20px;
	}
</style>
