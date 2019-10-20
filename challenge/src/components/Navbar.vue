<template>
	<header>
		<div class="head">
			<div class="logo">
				<a href="#">
					<img :src="require('@/assets/img/logo.png')" alt="logo" />
					<div class="name">next media</div>
				</a>
			</div>
			<a href="#">
				<img class="menu" :src="require('@/assets/img/menu.png')" alt="menu" />
			</a>
		</div>
		<nav>
			<ul>
				<li><a href=""><img :src="require('@/assets/img/home.png')" alt="home page" /></a></li>
				<li v-for="item in items" :key="item.object_id"><a href="#">{{ item.label }}</a></li>
			</ul>
		</nav>
	</header>
</template>
<script>
export default {
	name: 'navbar',
	props: {
		items: Array
	}
}
</script>
<style lang="scss">
</style>