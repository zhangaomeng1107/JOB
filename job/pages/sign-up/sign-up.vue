<template>
	<view class="main">
		<view class="u-f-jsb">
			<view class="">公司信息</view>
			<input type="text" value="" placeholder="公司名称" placeholder-style="color:#000;"/>
		</view>
		<view class="u-f-jsb">
			<view class="">职位描述</view>
			<view class="lv" @tap="gotoDescribe">请填写></view>
		</view>
		<view class="u-f-jsb">
			<view class="">薪资福利</view>
			<input type="text" value="" placeholder="薪资福利" placeholder-style="color:#95C936;"/>
		</view>
		<view class="u-f-jsb">
			<view class="">工作时间</view>
			<view class="">
				<picker @change="timechange" :value="index" :range="time" name="time">
					<view class="picker">
						{{index>-1?time[index]:'请选择 >'}}
					</view>
				</picker>
			</view>
		</view>
		<view class="u-f-jsb">
			<view class="">工作地点</view>
			<input type="text" value="" placeholder="工作地点" placeholder-style="color:#95C936;"/>
		</view>
		
		<view class="wz">
			<view class="">
				发布职位即表示你已同意<text>《迅免 兼职职位信息发布规则》</text>所有职位均有专人审核,禁止发布手机兼职，淘宝兼职等职位。
			</view>
			<view class="btn">
				<button type="default" @tap="gotorelease">发布</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		 // onLoad: function (option) {
		 //        console.log(option.value);
		 //    },
		data() {
			return {
				
				index:-1,
				time:["早班8：00-12：00","晚班 4：00-8：00"],
			}
		},
		methods: {
			timechange(e) {
				this.index= e.detail.value
			},
			gotoDescribe(){
				uni.navigateTo({
					url:'./describe'
				})
			},
			gotorelease(){
				uni.navigateTo({
					url:'../release-success/release-success'
				})
			}
		}
	}
</script>

<style scoped>
.main>view{
	margin:  10px;
	border-bottom: 1upx dashed #ccc ;
	padding: 10px 0;
}
.main view{
	font-size: 16px;
}
.picker,.lv{
	color:#95C936;
}
.main input{
	text-align: right;
}
.wz view,.wz{
	border: none !important;
}
.wz>view:first-child{
	font-size: 12px;
	color: #777;
}
.wz>view:first-child text{
	color: #95C936;
}
.wz button{
	margin-top: 50px;
	width: 70%; 
	height: 38px;
	line-height: 38px;
	border: 1rpx solid #5e9201;
	border-radius: 10px;
	color: #fff;
	background: linear-gradient(#5e9201,#b8dc44);
	}
</style>
