<template>
	<view>
		<topNav :iswz="iswz" :title="title" :wz="wz"></topNav>
		<scroll-view :style="{height:swiperHeight+'px'}" scroll-y>
			<view class="tu">
				<image src="../../static/img/z4.png" mode="widthFix"></image>
			</view>
			<view class="u-f-ajc">
				<block v-for="(item,index) in work" :key="index">
					<recommend-work :item="item" :index="index"></recommend-work>
				</block>
			</view>
			<view class="tu1">
				<image src="../../static/img/z3.png" mode="widthFix"></image>
			</view>
			<view class="work-title">
				<view class="work-title-text">
					<view class="selsct">
						<view class="square"></view>
						迅兔优选
					</view>
					<view class="more" @tap="gotoMore">更多</view>
				</view>
			</view>
			<block v-for="(item,index) in list" :key="index" >
				<search-recruit :item="item" :index="index"></search-recruit>
			</block>
		</scroll-view>
		
		
		<bottom-nav></bottom-nav>
	</view>
</template>

<script>
	import bottomNav from "../../components/top-nav/bottom-nav.vue"
	import recommendWork from '../../components/recommend-work/recommend-work.vue'
	import topNav from '../../components/top-nav/top-nav.vue'
	import searchRecruit from '../../components/search-recruit/search-recruit.vue'
	export default {
		components:{
			topNav,
			searchRecruit,
			recommendWork,
			bottomNav
		},
		data() {
			return {
				swiperHeight:'',
				title:"迅兔兼职",
				wz:"定位中",
				iswz:true,
				work:[
					{
						postion:"高中物理教师",
						time:"长期可做",
						money:"180元/次"
					},
					{
						postion:"高中物理教师",
						time:"长期可做",
						money:"180元/次"
					}
				],
				list:[
					{
						condition:"直招优秀派单员，只限女生",
						money:"180元/天",
						place:"云龙",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					},
					{
						condition:"直招优秀派单员，只限女生",
						money:"180元/天",
						place:"云龙",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					},
					{
						condition:"直招优秀派单员，只限女生",
						money:"180元/天",
						place:"云龙",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					},
					{
						condition:"直招优秀派单员，只限女生",
						money:"180元/天",
						place:"云龙",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					},
				]
			}
		},
		//获取屏幕高度
		onLoad() {
			uni.getSystemInfo({
			    success: (res)=> {
					let height=res.windowHeight-uni.upx2px(220) //upx 转化为px
					this.swiperHeight=height;
					// console.log(height)
			    }
			});
		},
		methods: {
			//点击跟过跳转页面
			gotoMore(){
				uni.navigateTo({
				    url: '../more/more'
				});
			}
		},
	}
</script>

<style>

	.work-title{
		width: 100%;
		height: 30px;
		line-height: 30px;
	}
	.work-title-text{
		display: flex;
		align-items: space-around;
		justify-content: space-between;
	}
	.work-title-text .more,.work-title-text .selsct{
		margin: 0 10px;
	}
	.more{
		color: #c1c1c1;
	}
	.square{
		height: 24px;
		width: 10px;
		background: #95C936;
		margin-right: 10px;
		float: left;
	}
	.tu image{
		width: 100%;
	}
	.tu1 image{
		width: 100%;
	}
	
	

</style>
