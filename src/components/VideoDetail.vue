<template>
	<div id='videoDetail'>
		<iframe width="560" height="315" :src='videoUrl' allowfullscreen></iframe>
	</div>
</template>

<script>
export default {
	name: 'VideoDetail',
	props: {
		video: {
			type: Object,
			required: false,
		}
	},
	computed: {
		videoUrl() {
			const videoId = this.video.id.videoId
			return `https://www.youtube.com/embed/${videoId}`
		}
	}
}
</script>

<style scoped>
	#videoDetail {
		margin-top: 12px;
	}
</style>