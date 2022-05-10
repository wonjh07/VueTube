<template>
	<div id='theSearchBar'>
		<form @submit.prevent="onSearch">
			<input type="text" v-model='keyword'>
		</form>
	</div>
</template>

<script>
export default {
	name: 'TheSearchBar',
	data: function() {
		return {
			keyword: '',
		}
	},
	methods: {
		onSearch() {
			this.$emit('on-search', this.keyword)
			console.log(this.keyword)
			this.keyword = ''
		}
	}
}
</script>

<style scoped>

</style>