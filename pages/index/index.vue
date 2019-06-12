<template>
	<view class="uni-list">
		<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in daily" :key="index" @tap="openinfo" :data-id="item.id">
			<view class="uni-media-list">
				<image class="uni-media-list-logo" :src="item.images"></image>
				<view class="uni-media-list-body">
					<view class="uni-media-list-text-top">{{item.title}}</view>
					<view class="uni-media-list-text-bottom uni-ellipsis">{{item.desc}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				daily:[],
			}
		},
		onLoad() {
			uni.request({
				url: 'http://splider.jefsky.com/index.php/api/Zhihu/zhihu_daily',
				method: 'GET',
				data: {},
				success: res => {
					this.daily = res.data.data.stories;
				}
			});
		},
		methods: {
			openinfo(e){
				var id = e.currentTarget.dataset.id;
				uni.navigateTo({
					url: '../info/info?id='+id
				});
			}
		}
	}
</script>

<style>
	
</style>
