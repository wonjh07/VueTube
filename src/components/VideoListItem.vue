<template>
	<div class="card" id='videoListItem' @click='onClickVideo'>
		<div class="left">
			<img :src="video.snippet.thumbnails.high.url" alt="">
		</div>
		<div class="right">
			<h2 class="title">{{ video.snippet.title }}</h2>
			<p class="description">{{ video.snippet.discription }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'VideoList',
	props: {
		video: {
			type: Object,
			required: false,
		}
	},
	methods: {
		onClickVideo() {
			this.$emit('on-click-video', this.video)
		}
	}
}
</script>

<style scoped>
	.card {
		display: flex;
		width: 700px;
		margin: 12px 0px;
	}

	.card:hover {
		cursor: pointer;
		opacity: 0.2;
	}

	.left {
		width: 30%;
	}

	.right {
		width: 70%;
		padding-left: 16px;
	}

	.right > .title {
		margin-top: 0;
	}

	.left > img {
		width: 100%;
		height: 100%;
		object-fit: fill;
	}

	
</style>