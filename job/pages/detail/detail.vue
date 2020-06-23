<template>
	<view class="mian">
		<topNav :iswz="iswz" :title="title" :wz="wz"></topNav>
		
		<!-- 详情页 -->
		<detail-info :item="detail" :iszixun="iszixun" :iszhuce="iszhuce" @hidePopup="hidePopup" @openEnroll="openEnroll"></detail-info>
	
		
		<!-- 弹出层 -->
		<uni-popup :show="showpopup" position="bottom" mode="fixed" @hidePopup="hidePopup">
			<view class="popup">
				<view class="safeK">
					正规兼职不会收取任何费用，若收费提高警惕
				</view>
				<radio-group class="group-list">
					<view class="u-f-jsb">
						<view class="">
							<view class=""><text>选择上班时间</text>  ({{detail.create_time}}) </view>
							<view class="u-f">{{detail.create_time}}</view>
						</view>
						<view class="">
							<radio value="r1" checked="true" color="red"/>
						</view>
					</view>
					<view class="u-f-jsb">
						<view class="">
							<text class="">选择工作地点</text>
							<view class="u-f">{{detail.address}}</view>
						</view>
						<view class="">
							<radio value="r2" color="red"/>
						</view>
					</view>			
				</radio-group>
				<view class="btn u-f-ac">
					<view @tap="hidePopup">取消</view>
					<view @tap="gotoBm">急速报名</view>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import uniPopup from '../../components/uni-popup/uni-popup.vue'
	import detailInfo from '../../components/detail-info/detail-info.vue'
	import topNav from '../../components/top-nav/top-nav.vue'
	export default {
		components:{
			topNav,
			detailInfo,
			uniPopup
		},
		data() {
			
			return {
				iszixun:true,
				iszhuce:false,
				isdetail:true,
				title:"职位详情",
				wz:"定位中",
				iswz:false,
				showpopup:false,
				detail:{
					desc:'',
					pid:'',
					cid:'',
					title:'',
					salary:'',
					address:'',
					times:'',
					issure:'',
					type:'',
					create_time:'',
					update_time:'',
				},
			}
		},
		onLoad(e){
			console.log(e)
			uni.request({
			    url: 'api/job_api/public/api/position/detail', //仅为示例，并非真实接口地址。
				method:"POST",
			    data: { 
					"pid":e.id,
			    },
			    success: (res) => {
					console.log(res);
					this.detail=res.data.data[0]
			    }
			});
		},
		// onLoad(e){
			
		// 	console.log(JSON.parse(e.detailData))
		// 	this.detail=JSON.parse(e.detailData)
		// 	console.log(e)
		// },
		
		methods: {
			hidePopup(){
				this.showpopup=!this.showpopup
			},
			gotoBm(){
				uni.navigateTo({
					url:"../success/success"
				})
			},
			openEnroll(){
				uni.navigateTo({
					url:'../../pages/enroll/enroll'
				})
			},
		}
	}
</script>

<style scoped>
	.safeK{
		height: 30px;
		line-height: 30px;
		border: 1px solid #ff444a;
		color: #FF444A;
		margin: 20px;
	}
	.group-list text{
		font-size: 18px;
		margin-right: 10px;
		color: #000 !important;
	}
	.group-list>view{
		border-bottom:1px solid #eaeaea ;
		padding: 10px 20px;
		color: #696969;
	}
	
	.btn>view:first-child{
		width: 40%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		color: #95c936;
	}
	.btn>view:last-child{
		width: 60%;
		height: 40px;
		line-height: 40px;
		text-align: center;
		background: #95c936;
		color: #fff;
	}
</style>
