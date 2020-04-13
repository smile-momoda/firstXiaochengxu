<template>
	<view>
		<view style="text-align: center;" >
			<image mode="aspectFit" src="@/static/image/tuxiang.png"  @click="upload">
			</image>
		</view>
		<view>
			
		</view>
		<view  style="text-align: center;">
			<audio style="text-align: center;" :src="current.src" :poster="current.poster" :name="current.name" :author="current.author" :action="audioAction" controls="true"></audio>
		    <view>听完好听的歌曲，心情美美哒</view>
		    <view>记得每天回关哦</view>
			<navigator url="../index/index?id=1&name=跳转">点击关注</navigator>
		</view>
		<!-- <div style="text-align: center;height: auto;">
			<image mode="aspectFit" src="../../static/image/welcome.gif"></image>
		</div> -->
	</view>
</template>

<script>
	export default{
		data(){
			return{
				current:{
					poster:"https://img-cdn-qiniu.dcloud.net.cn/uniapp/audio/music.jpg",
					name:"致我的粉丝们",
					author:"作者:么么哒",
					src:"https://img-cdn-qiniu.dcloud.net.cn/uniapp/audio/music.mp3",
				},
				audioAction:{
					method:"pause"
				}
			}
		},
		methods:{
			upload(){
				console.log('11');
				uni.navigateTo({
					url:'./upload?id=2&name=上传'
				})
			}
			
		},
		
	}
</script>

<style>

</style>
