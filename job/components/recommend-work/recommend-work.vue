<template>
	<view>
		<view class="recommend-work1" @tap="opendetail">
			<view class="good"><image src="../../static/img/good.png" mode="widthFix"></image></view>
			<view class="recommend-work-top">
				<text>{{item.title}}</text>
			</view>
			<view class="recommend-work-bottom">
				<view class="icons u-f-ajc">
					<view class="icon iconfont icon-history"></view>
					<text>{{item.times}}</text>
				</view>
				<view class=" u-f-ajc">
					<view class=" short-line"></view>
				</view>
				<view class="money">{{item.salary}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number,
		},
		data() {
			return {
			};
		},
		methods:{
			//进入详情页
			opendetail(){
				// console.log(进入详情页)
				uni.navigateTo({
					url:"/pages/detail/detail?detailData="+JSON.stringify(this.item),
				})
			}
		}
	}
</script>

<style scoped>
.recommend-work1{
		width: 140px; 
		height: 204px;
		border: 1px solid #B2D86F;
		border-radius: 10px;
		margin: 10px;
		position: relative;
	}
	.recommend-work-top{
		background: #AED941;
		background: linear-gradient(to right, #BCDF45, #94C835);
		border-radius: 10px 10px 0 0;
		color: #fff;
		font-size: 16px;
		
	}
	.recommend-work-bottom,.recommend-work-top{
		height: 102px;
		line-height: 102px;
		text-align: center;
	}
	.icons{
		color: #C1C1C1;	
	}
	.icon{
		font-size: 20px;
	}
	.icon text{
		font-size: 16px;
	}

	.short-line{
		height: 1px;
		background: #C1C1C1;
		width: 20%;
		margin: 10px 0;
	}
	.money{
		font-size: 18px;
		color: #FF454A;
		font-weight: bold;
	}
	.good{
		position: absolute;
		left: -32px;
		top: -8px;
	}
	.good image{
		width: 150px;
		z-index: 10;
	}
	
</style>
