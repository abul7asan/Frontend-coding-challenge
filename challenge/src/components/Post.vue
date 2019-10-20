<template>
<article>
	<div class="poster">
		<figure>
			<img :src="post.thumbnail_images.large.url" :alt="post.categories[0].title" />
		</figure>
		<div class="category" >{{ post.categories[0].title }}</div>
	</div>
	<div class="infos">
		<div class="title">
		{{ post.title }}
		</div>
		<div class="at">
		{{ getArabeDate(post.date) }}
		</div>
	</div>
</article>
</template>
<script>
export default {
	name: 'post',
	props: {
		post: Object
	},
	methods: {
		getArabeDate: function(date) {
      date = new Date(date);
      var months = ["يناير", "فبراير", "مارس", "إبريل", "مايو", "يونيو",
        "يوليو", "أغسطس", "سبتمبر", "أكتوبر", "نوفمبر", "ديسمبر"
      ];
      var days = ["اﻷحد", "اﻷثنين", "الثلاثاء", "اﻷربعاء", "الخميس", "الجمعة", "السبت"];
      var arDateString = days[date.getDay()] + ' ' + date.getDate() + ' ' + months[date.getMonth()] + ' ' + date.getFullYear();
      return arDateString;
    }
	}
}
</script>
<style>
</style>