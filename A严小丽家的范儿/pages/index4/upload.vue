<template>
	<view>
		<button @click="view">预览</button>
			<view style="width: 100%;text-align: center;">
				<image  :src="item"  v-for="item in items" mode="widthFix"></image>
			</view>
	<button @click="update">上传</button>
	</view>
	
</template>

<script>
	export default{
		data(){
			return{
				items:[]
			}
		},
		methods:{
			update(){
				uni.chooseImage({
				    success: (chooseImageRes) => {
				        const tempFilePaths = chooseImageRes.tempFilePaths;
				        uni.uploadFile({
				            url: 'https://www.example.com/upload', //仅为示例，非真实的接口地址
				            filePath: tempFilePaths[0],
				            name: 'file',
				            formData: {
				                'user': 'test'
				            },
				            success: (uploadFileRes) => {
								
				                console.log(uploadFileRes.data);
				            }
				        });
				    }
				});
			},
			view(){
				console.log("预览")
				uni.chooseImage({
				    count: 6, //默认9
				    sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
				    // sourceType: ['album'], //从相册选择
				    success:(res) => {
				        console.log(JSON.stringify(res.tempFilePaths),666);
						// this.items=res.tempFilePaths
						this.items = this.items.concat(res.tempFilePaths)
						console.log(this.items,'数据')
				    }
				});
			}
		},
		onLoad: function (option) { //option为object类型，会序列化上个页面传递的参数
		        console.log(option.id); //打印出上个页面传递的参数。
		        console.log(option.name); //打印出上个页面传递的参数。
		    }
	}
</script>

<style>
</style>
