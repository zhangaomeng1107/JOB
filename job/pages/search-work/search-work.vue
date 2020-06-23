<template>
	<view>
		<topNav :iswz="iswz" :title="title" :wz="wz"></topNav>
		

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
		<block v-for="(item,index) in list" :key="index">
			<search-recruit :item="item" :index="index"></search-recruit>
		</block>
	</view>
</template>

<script>
	import recommendWork from '../../components/recommend-work/recommend-work.vue'
	import topNav from '../../components/top-nav/top-nav.vue'
	import searchRecruit from '../../components/search-recruit/search-recruit.vue'
	export default {
		components:{
			topNav,
			searchRecruit,
			recommendWork
		},
		data() {
			return {
				title:'',
				salary:'',
				address:'',
				times:'',
				issure:'',
				type:'',
				title:"迅兔兼职",
				wz:"定位中",
				iswz:true,
				work:[
					{
						title:"高中物理教师",
						times:"长期可做",
						salary:"180元/次"
					},
					{
						title:"高中物理教师",
						times:"长期可做",
						salary:"180元/次"
					}
				],
				list:[ 
					
				]
			}
		},
		onLoad(){
			uni.request({
			    url: 'api/job_api/public/index.php/api/position/index', //仅为示例，并非真实接口地址。
				method:"POST",
			    data: { 
					"pagesize":10,
			    },
			    success: (res) => {
						// console.log(res.data);
						// this.list = res.data;
						this.list=res.data.data.data
						console.log(this.list)
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