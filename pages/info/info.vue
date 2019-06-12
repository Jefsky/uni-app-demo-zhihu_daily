<template>
	<view class="info">
		<view class="uni-title">{{title}}</view>
		<view class="content">
			<rich-text :nodes="strings">{{detail}}</rich-text>
		</view>
		 
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title : '',
				strings : '',
			}
		},
		onLoad(e) {
			var id = e.id;
			uni.request({
				url: 'http://splider.jefsky.com/index.php/api/Zhihu/news?id='+id,
				method: 'GET',
				data: {},
				success: res => {
					var data = res.data.data;
					this.title = data.title;
					this.strings = data.body;
					console.log(data)

				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {
			
		}
	}
</script>

<style>
.content image{
	width: 100vh;
	height: 56vh;
}
</style>
