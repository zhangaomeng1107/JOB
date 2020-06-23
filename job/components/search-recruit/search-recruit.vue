<template>
	<view>
		
		<view class="recruit" >
			<view class="recruit-tj  u-f-jsb" @tap="opendetail">
				<view>
					{{item.title}}
				</view>
				<view>
					{{item.salary}}
				</view>
			</view>
			<view class="recruit-zs u-f-jsb" @tap="opendetail">
				<view class="postion u-f">
					<view class="u-f-ajc">
						<view class="icon iconfont icon-togo"></view>
						<text>{{item.address}}</text>
					</view>
					<view class="u-f-ajc">
						<view class="icon iconfont icon-history"></view>
						<text>{{item.times}}</text>
					</view>
				</view>
				<view class="safe u-f-ac">
					<view class="u-f">
						<template v-if="item.issure==1">
							<view class="u-f-ajc">
								<view class="icon iconfont icon-guarantee"></view>
							</view>
							<text>安全保障</text>
						</template>
						<template v-else>
							<text>无保障</text>
						</template>
						
					</view>
					<view class="u-f-ajc">
						<template v-if="item.type==1">
							<text>月结</text>
						</template>
						<template v-else-if="item.type==2">
							<text>日结</text>
						</template>
						<template v-else>
							<text>周结</text>
						</template>
					</view>
				</view>
			</view>
			<template v-if="isshow">
				<view class="cz u-f">
					<view @tap="gotoSignup">编辑</view>
					<view @tap="gotoEdit">删除</view>
				</view>
			</template>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number,
			isshow:Boolean
		},
		data() {
			return {
				
			};
		},

		methods:{
			//进入详情页
			opendetail(){
				// console.log(进入详情页)
				uni.navigateTo({
					url:"/pages/detail/detail?id="+this.item.id,
				})
			},
			// 点击编辑按钮
			gotoSignup(){
				uni.navigateTo({
					url:'../../pages/sign-up/sign-up'
				})
			},
			//点击删除按钮
			// gotoEdit(){
			// 	uni.navigateTo({
			// 		url:'../../pages/enterprise-center/edit'
			// 	})
			// }
		}
	}
</script>

<style scoped>
.recruit{
		width: 100%;
		border-bottom: 1px dashed #c1c1c1 ;
		padding: 20px 0px;
	}
	.recruit-tj>view,.recruit-zs>view{
		margin: 0 10px;
	}
	.recruit-tj>view{
		font-size: 18px;
	}
	.recruit-tj>view:last-child{
		color: red;
	}
	.postion>view{
		color: #c1c1c1;
		font-size: 12px;
		margin-right: 5px;
	}
	.safe>view:first-child{
		border: 1px solid #B2D86F;
		height: 20px;
		font-size: 12px;
		width: 75px;
	}
	.safe>view:first-child>view{
		background: #95C936;
		height: 20px;
		width: 20px;
		color: #fff;
		margin-right: 5px;
	}
	.safe>view:first-child>text{
		color: #95C936;
	}
	.safe>view:last-child{
		border: 1px solid #c1c1c1;
		height: 20px;
		margin-left: 10px;
		font-size: 12px;
		color: #C1C1C1;
		width: 30px;
	}
	.cz{
		justify-content: flex-end;
		margin-top: 10px;
		padding: 0 10px;
	}
	.cz>view{
		height: 20px;
		line-height: 20px;
		text-align: center;
		width: 35px;
		margin-left: 5px;
		color: #a0a0a0;
		border: 1px solid #E5E5E5;
	}
</style>
