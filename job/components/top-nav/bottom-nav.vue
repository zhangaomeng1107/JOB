<template>
		<!-- 自定义tabbar -->
			    <view class="tab-bar">
				    <view class="tab-tabs">
						<view class="tab-main" v-for="(item,index) in tabbarlist" :key="index" @click="changeTabbar(index)">
					    	<view  class=" my-icon">
									<view class="iconfont my-icon-coco" :class="item.icon" 
									:style="{'background-color':index == 0 && tabCurrentIndex == 0 ? '#fff' : item.background, 
									'color':index != 0 && tabCurrentIndex == index ? '#a7ba47' : item.color}">

					    		</view>
					    	</view>
					    	<view class="my-text"  :style="{'color':tabCurrentIndex == index ? '#95c936' : ''}" >{{item.text}}</view>
				    	</view>
				    </view>
				</view>

</template>
<script>
    export default {
        data() {
            return {
				tabCurrentIndex: 1,
				tabbarlist: [
								{
									"id": 0,
									"icon": "icon-shouye",
									"text": "首页",
									"selectColor": '#a7ba47',
									"color": "#333",
								},
								{
									"id": 1,
									"icon": "icon-qiyezhongxin",
									"text": "企业中心",
									"selectColor": '#a7ba47',
									"color": "#333",
								}
						],
			}
        },

	   methods: {
		   
		   changeTabbar(index){
		       this.tabCurrentIndex = index;
		       if(index == 0){
		        uni.navigateTo({
		         url:'../../pages/search-work/search-work-copy'
		        })
		       }else if(index == 1){
		        uni.navigateTo({
		         url:'../../pages/enterprise-center/enterprise-center'
		        })
		       }
		      },

		},
	}
</script>
<style scoped>
	/* 底部导航栏*/
	    .tab-bar {
			border-top: 2px solid #95C936;
	    	width: 100%;
	    	height: 60px;
	    	background-color: #fff;
	    	position: fixed;
	    	left: 0;
	    	bottom: 0px;
	    	z-index: 9998;
	    	box-sizing: border-box;
	    }
	    .tab-tabs {
	    	width: 100%;
	    	height: 100upx;
	    	position: relative;
	    	display: flex;
	    	flex-wrap: nowrap;
	    	box-sizing: border-box;
	    	justify-content: space-around;
	    }
		.tab-main {
			width: 140upx;
			height: 100upx;
			background-color: #fff;
			text-align: center;
	    	box-sizing: border-box;
		}
		.my-icon {
			height: 55upx;
			box-sizing: border-box;
			
		}
		.my-icon>view{
			font-size: 18px !important;
		}
		.my-text {
			padding-top: 0px;
			width: 100%;
			height: 40upx;
			line-height: 40upx;
			color: #333;
		}
</style>
