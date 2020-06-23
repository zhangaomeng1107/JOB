<template>
	<view class="main">
		<view class="">
			<view class="u-f-ac"><view class="">姓名</view> <input type="text" value="" placeholder="请输入姓名"/></view>
		</view>
		<view class="">
			<view class="u-f-ac xian"><view class="">我的公司</view> <input type="text" value="" placeholder="请输入你的公司"/></view>
			<view class="u-f-ac"><view class="">我的职务</view> <input type="text" value="" placeholder="请输你的职务"/></view>
			
		</view>
		<view class="">
			<view class="u-f-ac xian"><view class="">公司地址</view> <input type="text" value="" placeholder="请输入你的公司地址"/></view>
			<view class="u-f-ac"><view class="">公司电话</view><input type="text" value="" placeholder="请输入固定电话/手机号"/></view>
		</view>
		
		<button type="default" @tap="gotoSignup">完成</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},

		methods: {
			gotoSignup(){
				uni.navigateTo({
					url:"../sign-up/sign-up"
				})
			}
		}
	}
</script>

<style scoped>
.main{
		position: fixed;
		background: #E9E9E9 ;
		height: 100%;
		width: 100%;
		top: 44px;
		left: 0;
		
	}
	.main>view{
		background: #fff;
		margin-bottom: 10px ;
	}
	.main>view>view{
		padding: 10px 10px;
		font-size: 16px;
		
	}
	.main view input{
		margin-left: 10px;
	}
	.main view view view{
		width: 25%;
	}
	.xian{
		border-bottom: 1px solid #E9E9E9;
	}
	.main button{
		margin-top: 50px;
		width: 150px; 
		height: 38px;
		line-height: 38px;
		border: 1rpx solid #5e9201;
		border-radius: 10px;
		color: #fff;
		background: linear-gradient(#5e9201,#b8dc44);
	}
</style>
