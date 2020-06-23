<template>
	<view>
		<view class="zp">
			<view class="zp-xj">
				<view>
					{{item.condition}}
				</view>
				<view class="u-f ">
					<view class="u-f-ajc">
						<view class="icon iconfont icon-togo"></view>
						<text>{{item.place}}</text>
					</view>
					<view class="u-f-ajc">
						<view class="icon iconfont icon-history"></view>
						<text>{{item.date}}</text>
					</view>
				</view>
				<view class="u-f-jsb jk">
					<view class="u-f">
						<view> <text>{{item.money}}</text> 元/次</view>
						<view class="zj u-f-ajc">{{item.way}}</view>
					</view>
					<view @tap="gotoDetail">
						待处理
					</view>
				</view>	
			</view>
			<view class="u-f-ajc btn">
				<view >取消报名</view>
				<view class="line"></view>
				<view @tap="hidePopup">投诉职位</view>
			</view>
		</view>
		
		<!-- 弹出层 -->
		<uni-popup :show="showpopup" position="middle" mode="fixed" @hidePopup="hidePopup" class="u-f-ac">
			<view class="popup">
				<view>
					<view class="">拨打客服电话投诉</view>
					<view class="">19862559117</view>
				</view>
				<view class="btn1 u-f">
					<view @tap="hidePopup">取消</view>
					<view>拨打客服电话</view>
				</view>
			</view>
		</uni-popup>
		
	</view>
</template>

<script>
import uniPopup from '../../components/uni-popup/uni-popup.vue'
	export default {
		components:{
			uniPopup
		},
		props:{
			item:Object,
			index:Number
		},
		data() {
			return {
				showpopup:false,
			}
		},
		methods:{
			gotoDetail(){
				uni.navigateTo({
					url:'../../pages/detail/detail'
				})
			},
			hidePopup(){
				this.showpopup=!this.showpopup
			},
		}
	}
</script>

<style scoped>
	.popup{
		width: 100%;
		
	}
	.popup>view{
		
		width: 100%;
	}
	.popup>view:first-of-type>view{
		margin: 5px 0;
		font-size: 16px;
	}
	.btn1{
		width: 70%!important;
		float: right;
	}
	.btn1>view:last-child{
		color: #94c933;
	}
	
	.zp-xj{
		margin: 10px;
		border-bottom: 1PX dotted #ccc;
	}
	.zp-xj>view:first-of-type{
		font-size: 18px;
		padding: 10px 0;
	}
	.zp-xj>view:nth-of-type(2){
		color: #bfbfbf;
	}
	.jk{
		margin: 10px 0;
	}
	.jk view{
		font-size: 16px;
	}
	.jk text{
		color: #ff454a;
		margin-right: 5px;
	}
	.jk .zj{
		font-size: 12px !important;
		border: 1px solid #BFBFBF;
		color: #BFBFBF;
		height: 18px;
		width: 33px;
		line-height: 18px;
		margin: 6px 0px 0px 10px;
	}
	.zp{
		background: #fff;
	}
	
	.btn{
		padding-bottom: 5px;
	}
	.btn>view,.btn1>view{
		width: 50%;
		text-align: center;
		height: 40px;
		line-height: 40px;
		font-size: 16px;
	}
	.line{
		background: #BFBFBF;
		height: 20px !important;
		width: 1px !important;
	}
</style>
