<template>
	<view>
		<topNav :iswz="iswz" :title="title" :wz="wz"></topNav>
		
		<view class="u-f-ajc tu">
			<image src="../../static/img/z5.png" mode="widthFix"></image>
		</view>
		<view class="btn u-f-ajc">
			<button type="default" @tap="gotoSeaWork">继续报名</button>
		</view>
	</view>
</template>

<script>
	import topNav from '../../components/top-nav/top-nav.vue'
	export default {
		components:{
			topNav
		},
		data() {
			return {
				title:"报名成功",
				wz:"定位中",
				iswz:false,
			}
		},
		methods: {
			gotoSeaWork(){
				uni.reLaunch({
				    url: '../search-work/search-work?data='+this.data
				});
			}
			
		}
	}
</script>

<style scoped>
	.tu image{
		width: 230px;
		margin: 80px 0;
	}
	.btn button{
		width: 50%;
		height: 40px;
		line-height: 40px;
		color: #fff;	
		background: linear-gradient(#5e9201,#b8dc44);
		
	}
</style>
