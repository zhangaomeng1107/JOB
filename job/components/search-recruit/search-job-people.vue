<template>
	<view>
		<view class="gl">
			<view class=""><image :src="item.userpic" mode="widthFix"></image></view>
			<view class="wz">
				<view class="u-f-jsb">
					<view class="name">{{item.username}}</view>
					<view class="u-f-ac">{{item.userdate}}</view>
				</view>
				<view class="u-f-jsb">
					<view class="">应聘职位:<text>{{item.postion}}</text></view>
					<view class="">手机号:<text>{{item.usertle}}</text></view>
				</view>
			</view>
			
		</view>
	</view>
</template>

<script>
	
	export default {
		props:{
			item:Object,
			index:Number,
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style scoped>
	.gl{
		height: 80px;
		margin: 0 10px;
		padding: 20px 0 0 0;
		border-bottom: 1px solid #e8e8e8;
	}
.gl image{
	width: 60px;
	border-radius: 50%;
	float: left;
	margin-right: 10px;
}
.gl view{
	font-size: 14px;
	color: #959595;
}
.gl .name{
	font-size: 20px;
	color: #000000;
}
.wz>view:last-child{
	margin: 5px 0;
}
.wz text{
	color: #000000;
}
</style>
