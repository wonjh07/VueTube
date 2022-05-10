<template>
	<div id="videoList">
		<VideoListItem
			v-for="video in videos"
			:key="video.id.videoId"
			:video="video"
			@on-click-video="onClickVideo => $emit('on-click-video', video)"
		/>
	</div>
</template>

<script>
import VideoListItem from '@/components/VideoListItem'

export default {
  name: 'VideoList',
  components: {
		VideoListItem,
  },
	props: {
		videos: {
			type: Array,
			required: false,
		}
	},
	methods: {
		onClickVideo(video) {
			this.$emit('on-click-video', video)
		}
	}
}
</script>

<style scoped>

</style>