<template>
	<view class="main">
		<topNav :iswz="iswz" :title="title" :wz="wz"></topNav>
		
		<template v-if="isrecord">
			<block v-for="(item,index) in recordList" :key="index">
				<job-record :item="item" :index="index" ></job-record>
			</block>
			
			<view class="u-f-ajc none">
				没有更多的求职记录~
			</view>
		</template>
		<template v-else>
			<view class=" u-f-ajc">
				<image src="../../static/img/z6.png" mode="widthFix"></image>
			</view>
		</template>	
		
		
	</view>
</template>

<script>
	
	import topNav from '../../components/top-nav/top-nav.vue'
	import jobRecord from '../../components/job-record/job-record.vue'
	export default {
		components:{
			topNav,
			jobRecord,
		},
		data() {
			return {
				
				title:"求职记录",
				wz:"定位中",
				iswz:false,
				isrecord:true,
				recordList:[
					{
						condition:"诚聘高中周末数学老师",
						money:"180",
						place:"铜山",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					},
					{
						condition:"诚聘高中周末数学老师",
						money:"180",
						place:"铜山",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					},
					{
						condition:"诚聘高中周末数学老师",
						money:"180",
						place:"铜山",
						date:"长期可做",
						safe:"工作保障",
						way:"周结"
					}
				]
				
			}
		},
		methods: {
			
			
		}
	}
</script>

<style>
	
	
	.main{
		height: 100vh;
		background: #E9E9E9 ;
		
	}
	image{
		width: 200px;
		margin: 80px;
	}
	.none{
		padding-top: 20px;
		color: #5e5e5e;
		background: #E9E9E9 ;
	}
</style>
