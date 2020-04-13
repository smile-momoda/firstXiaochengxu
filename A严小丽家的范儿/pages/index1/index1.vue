<template>
	<view>
	<view>
		<scroll-view id="example-1" :scroll-top="scrollTop" scroll-y="true" class="csroll-Y" @scrolltoupper="upper" @scroll="scroll" @scrolltolower="lower">
			<view style="margin-bottom: 50px;" v-for="item in items" id="demo1" class="">{{item.message}}</view>
		</scroll-view>
	</view>
	<view @tap="goTop" class="">点击回顶部</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				scrollTop:0,
				old:{
					scrollTop:0
				},
				items:[
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
					{message:"你好，欢迎来到严范儿"},
				]
			}
		},
		methods:{
			upper:function(e){
				console.log(e,11111)
			},
			lower:function(e){
				console.log(e,2222)
			},
			scroll:function(e){
				console.log(e,333)
				this.old.scrollTop=e.detail.scrollTop
			},
			goTop:function(e){
				this.scrollTop=this.old.scrollTop
				this.$nextTick(function(){
					this.scrollTop=0
				});
			}
		}
	}
</script>

<style>
</style>
