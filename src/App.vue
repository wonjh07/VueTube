<template>
  <div id="app">
		<div class='card'>
			<h1>JJaeho-Tube</h1>
			<TheSearchBar @on-search="onSearch" />
		</div>
		<div class='card'>
			<VideoDetail v-if="Object.keys(video).length" :video="video" />
			<VideoList :videos="videos" @on-click-video="onClickVideo" />
		</div>
  </div>
</template>

<script>
import TheSearchBar from '@/components/TheSearchBar'
import VideoList from '@/components/VideoList'
import VideoDetail from '@/components/VideoDetail'
import axios from 'axios'

export default {
  name: 'App',
  components: {
		TheSearchBar,
		VideoList,
		VideoDetail,
  },
	data: function() {
		return {
			videos: [],
			video: {}, // videoListItem 에서 클릭한 비디오를 저장할 데이터
		}
	},

	methods: {
		async onSearch(keyword) {
			const YOUTUBE_SEARCH_BASE_URL = 'https://www.googleapis.com/youtube/v3/search'
			const YOUTUBE_API_KEY = 'AIzaSyCEhI_CzcD-QFutFjiYZSJeru3fsaOTIHg'
			
			let params = {
				key: YOUTUBE_API_KEY,
				part: 'snippet',
				q: keyword,
			}

			// await 이하 구문이 promise 일때만 async 사용가능,
			let result = await axios.get(YOUTUBE_SEARCH_BASE_URL, { params })
			this.videos = result.data.items
		},
		onClickVideo(video) {
			this.video = video
		}
	}
}
</script>

<style scoped>
	.card {
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin-left: 120px;
		margin-right: 120px;
	}
</style>
