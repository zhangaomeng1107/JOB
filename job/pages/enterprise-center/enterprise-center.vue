<template>
	<view>
		
		
		
		
		
		<!-- 自定义导航栏 -->
		<uniNavBar fixed="true" statusBar="true" left-icon="arrowleft"  shadow="true"
		color="#fff" background-color="#95c936" @clickLeft="close">
		<view slot="right" class="right">管理</view>
				<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tab-head>
		</uniNavBar>
		
		
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" :current="tabIndex" @change="tabchange">
				<!-- 职位 -->
				<swiper-item>
					<scroll-view :scroll-y="true" class="list">
						<block v-for="(item,index) in list" :key="index">
							<search-recruit :item="item" :index="index" :isshow="isshow"></search-recruit>
						</block>
					</scroll-view>
				</swiper-item>
				<!-- 求职者管理 -->
				<swiper-item>
					<scroll-view :scroll-y="true" class="list">
						<block v-for="(item,index) in userList" :key="index">
							<search-job-people :item="item" :index="index"></search-job-people>
						</block>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>	
		
		
		
			<bottom-nav></bottom-nav>

		
		
		
	</view>
</template>

<script>
	import bottomNav from "../../components/top-nav/bottom-nav.vue"
	import searchJobPeople from "../../components/search-recruit/search-job-people.vue"
	import swiperTabHead from "../../components/top-nav/swiper-tab-head.vue";
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue'
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	import searchRecruit from '../../components/search-recruit/search-recruit.vue'
	export default {
	    components: {
	        uniNavBar,
	        uniIcons,
			swiperTabHead,
			searchRecruit,
			searchJobPeople,
			bottomNav
	    },
	    data() {
	        return {
				currentTabIndex: 1,
				swiperHeight:'',
	            tabIndex:0,
				isshow:true,
				tabBars: [
					{name: '职位管理',id: 'zhiwei'},
					{name: '求职者管理',id: 'qiuzhizhe'} 
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
				],
				userList:[
					{
						userpic:'../../static/img/20.jpg',
						username:'悦悦',
						userdate:'12-10',
						postion:'文员特助',
						usertle:'19862559117'
					},
					{
						userpic:'../../static/img/20.jpg',
						username:'悦悦',
						userdate:'12-10',
						postion:'文员特助',
						usertle:'19862559117'
					},
					{
						userpic:'../../static/img/20.jpg',
						username:'悦悦',
						userdate:'12-10',
						postion:'文员特助',
						usertle:'19862559117'
					},
					{
						userpic:'../../static/img/20.jpg',
						username:'悦悦',
						userdate:'12-10',
						postion:'文员特助',
						usertle:'19862559117'
					}
					
				],
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
			tabClick(index){
					console.log('返回tabBar索引：' + index)
					this.currentTabIndex = index
				},

			
	        ///tabbar点击事件
			tabtap(index) {
				this.tabIndex=index
			},
			//滑动切换
			tabchange(e){
				// console.log(JSON.stringify(e.detail.current))  将对象转化为字符串
				this.tabIndex=e.detail.current;
			},
	    },

	}
</script>

<style scoped>

</style>
