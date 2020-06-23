<template>
	<view class="uni-tab-bar">
		<scroll-view :scroll-x="true" class="uni-swiper-tab" :style="scrollStyle">
			<block v-for="(tab,index) in tabBars" :key="tab.id">
				<view class="swiper-tab-list" :class="{'active':tabIndex==index}" @tap="tabtap(index)" :style="scrollItemStyle">
					{{tab.name}} {{tab.num?tab.num:''}}
					<view class="swiper-tab-line"></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default{
		props:{
			tabBars:Array,
			tabIndex:Number,
			scrollStyle:{
				type:String,
				default:""
			},
			scrollItemStyle:{
				type:String,
				default:""
			},
		},
		methods:{
			tabtap(index) {
				this.$emit('tabtap',index);
			},
		}
	}
</script>

<style>
	.uni-swiper-tab{
		border-bottom: none;
	}
	.swiper-tab-list{
		color: #FFFFFF;
		font-size: 16px;
		width: 80px;
		margin-right: 10upx;
	}
	.uni-tab-bar .active{
		color: #FFFFFF;
	}
	.active .swiper-tab-line{
		border-bottom: 5upx solid #f3be00;
		width: 140upx;
		margin: auto;
		border-top: 5upx solid #f3be00;
		border-radius: 20UPX;
	
	}
</style>
