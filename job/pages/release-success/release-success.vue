<template>
	<view>
		<view class="u-f-ajc"><image src="../../static/img/z7.png" mode="widthFix"></image></view>
		<view class="btn">
			<button type="default" @tap="gotocenter">返回企业中心</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			gotocenter(){
				uni.navigateTo({
				    url: '../enterprise-center/enterprise-center'
				});
			}
		}
	}
</script>

<style scoped>
	image{
		width: 250px;
		margin-top: 50px;
	}
.btn button{
	margin-top: 50px;
	width: 70%; 
	height: 38px;
	line-height: 38px;
	border: 1rpx solid #5e9201;
	border-radius: 10px;
	color: #fff;
	background: linear-gradient(#5e9201,#b8dc44);
	}
</style>
