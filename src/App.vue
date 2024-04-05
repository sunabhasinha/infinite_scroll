<script setup>
	import { ref, onMounted } from 'vue';
	import Posts from './components/Posts.vue';

	const posts = ref([]);

	const fetchPosts = async () => {
		const resJson = await fetch('https://jsonplaceholder.typicode.com/posts');
		const res = await resJson.json();
		posts.value = [...posts.value, ...res];
	};

	onMounted(async () => {
		await fetchPosts();
		window.addEventListener('scroll', handleScroll);
	});

	const handleScroll = async () => {
		if (
			window.scrollY + window.innerHeight >=
			document.body.scrollHeight - 50
		) {
			await fetchPosts();
		}
	};
</script>

<template>
	<Posts v-for="(post, i) in posts" :key="i" :post="post" />
</template>

<style scoped></style>
