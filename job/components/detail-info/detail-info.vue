<template>
	<view>
		<view class="title">
			<view>{{item.title}}</view>
			<view>{{item.salary}}</view>
			<view>
				<template v-if="item.type==1">
					<text>月结</text>
				</template>
				<template v-else-if="item.type==2">
					<text>日结</text>
				</template>
				<template v-else>
					<text>周结</text>
				</template>  
				 | 
				 家庭助教
				 | 
				 6人
			</view>
		</view>
		<view class="require">
			<view>{{item.title}}</view>
			<view class="line"></view>
			<view>{{item.desc}}</view>
			<view>薪资福利</view>
			<view class="line"></view>
			<view><template v-if="item.type==1"><text>月结</text></template><template v-else-if="item.type==2"><text>日结</text></template><template v-else><text>周结</text></template>，{{item.salary}}</view>
		</view>
		<view class="time">
			<view>工作时间</view>
			<view class="line"></view>
			<view class="time-pogress u-f-ac">
				<view>
					<view>开始日期</view>
					<view>结束日期</view>
				</view>
				<view>
					<view style="height: 45px;">{{item.create_time}}</view>
					<view class="">
						<view class="small-tag">白班8:00——18:00</view>
						<view>{{item.update_time}}</view>
					</view>
				</view>
			</view>
		</view>
		
		<view class="place">
			<view>工作地点</view>
			<view class="line"></view>
			<view>地址：{{item.address}}</view>
		</view>
		<view class="information">
			<view>公司信息</view>
			<view class="line"></view>
			<view>公司名称：{{item.pid}}</view>
		</view>
		<view class="safe">
			防骗警示：未标明收费的职位不会收取任何费用，若商家要求缴纳费用的押金，请提供警惕第一时间向我们报告
		</view>
		
		
		<view class="btn u-f-ac">
				<view class="icon iconfont icon-share">分享</view>
			
			<view v-show="iszixun" class="zx" >
				<view class="icon iconfont icon-respond">咨询</view>
			</view>
			
			<view class="bm">
				<template v-if="iszhuce">
					<view @tap="hidePopup">报名参加</view>
				</template>
				<template v-else>
					<view @tap="openEnroll">报名参加</view>
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			iszixun:Boolean,
			iszhuce:Boolean
		},
		data() {
			return {
				
			};
		},
		methods:{
			hidePopup() {
				this.$emit('hidePopup');
			},
			openEnroll() {
				this.$emit('openEnroll');
			},
		}
	}
</script>

<style scoped>
.title,.require,.time,.place,.information,.safe{
		border-top: 5px solid #e9e9e9;
		padding: 10px 20px;
	}
	.title>view{
		margin: 3px 0;
	}
	.title>view:nth-of-type(1){
		font-size: 20px;
		font-weight: bold;
	}
	.title>view:nth-of-type(2){
		font-size: 18px;
		font-weight: bold;
		color: #FF444A;
	}
	.title>view:nth-of-type(3){
		color: #6A6A6A;
	}
	.require>view:nth-of-type(1),.time>view:nth-of-type(1),.place>view:nth-of-type(1),.information>view:nth-of-type(1){
		font-size: 16px;
	}
	.require>view:nth-of-type(3){
		font-size: 12px;
		color: #7a7a7a;
		padding: 5px 0 10px 0;
		border-bottom: 1px solid #C1C1C1;
	}
	.require>view:nth-of-type(4){
		font-size: 16px;
		margin-top: 10px;
	}
	.require>view:nth-of-type(6){
		height: 30px;
		line-height: 30px;
		width: 100%;
		color: #666;
		background: #eee;
		margin: 10px 0;
	}
	.line{
		margin: 5px 0;
		height: 1px;
		width: 10%;
		background: #EEEEEE;
	}
	.time-pogress>view{
		height: 100px;
	}
	.time-pogress>view>view{
		height: 50px;
		line-height: 50px;
	}
	.time-pogress>view:first-child{
		color: #8f8f8f;
		margin-right: 25px;
	}
	.small-tag{
		font-size: 6px;
		color: #8f8f8f;
	}
	.place>view:nth-of-type(3),.information>view:nth-of-type(3){
		color: #7A7A7A;
	}
	.safe{
		color: #7A7A7A;
	}
	
	.btn>view:first-child{
		width: 30%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		color: #95c936;
	}
	.btn .zx{
		width: 30%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		color: #95c936;
	}
	.bm{
		width: 40%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		color: #fff;
		background: #95c936 ;
	}
	.bm>view,.zx>view{
		height: 40px;
		line-height: 40px;	
	}
	
</style>
