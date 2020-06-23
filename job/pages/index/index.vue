<template>
	<view class="index-work">
			<view class="search-work">
				<image src="../../static/img/z1.png" mode="widthFix"></image>
				<button type="default" @tap="searchWork">我要找工作</button>
			</view>
			<view class="index-or">
				<view class="line"></view>
				<text>或者</text>
				<view class="line"></view>
			</view>
			<view class="search-people">
				<image src="../../static/img/z2.png" mode="widthFix"></image>
				<button type="default" @tap="searchPeople">我要招人</button>
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
			//进入详情页
			searchWork(){
				// console.log(进入详情页)
				uni.reLaunch({
					url:"../search-work/search-work",
				})
			},
			searchPeople(){
				uni.navigateTo({
					url:"../search-people/search-people",
				})
			}
		}
	}
</script>

<style>
	.index-work{
		position: fixed;
		background:  #C9EA5B ;
		height: 100%;
		width: 100%;
		top: 0px;
		left: 0;
	}
	.index-work image{
		width: 250px ;
		
	}
	.search-work,.search-people{
		width: 100%;
		text-align: center;
	}
	.index-or {
		margin: 20px 0 10px 0;
		color: #fff;
		display: flex;
		justify-content: center;
	}
	.index-or text{
		font-size: 16px;
	}
	.index-or .line{
		height:1px;
		 width:35%;
		 background:#fff;
		 margin: 10px;
	}
	.index-work button{
		width: 150px; 
		height: 38px;
		line-height: 38px;
		border: 1rpx solid #5e9201;
		border-radius: 10px;
		color: #fff;
		background: linear-gradient(#5e9201,#b8dc44);
	}
</style>
