<template>
	<view class="main">
		<uniNavBar fixed="true" statusBar="true" left-icon="closeempty"  shadow="true"
		color="#fff" background-color="#95c936" right-icon="checkmarkempty" @clickLeft="close" @clickRight="clickRight">
				<view slot="left" class="left">职位描述</view>
		</uniNavBar>
		
		<view class="uni-textarea">
			<view>
				0/5000
			</view>
			<textarea placeholder-style="color:#b1b1b1" maxlength=-1  @blur="bindTextAreaBlur" placeholder="填写详细,清晰的职位描述，有助于您更准确地展示招聘需求例如:
1.工作内容...
2.任职要求...
3.特别说明..." />
			<view>
				不能填写QQ、微信、电话等联系方式以及特殊符号
			</view>
		</view>
	</view>
</template>

<script>
	import uniNavBar from '../../components/uni-nav-bar/uni-nav-bar.vue'
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	export default {
		components:{
			uniNavBar,
			uniIcons,
		},
		data() {
			return {
				
				};
		},
		methods:{
			close(){
				uni.navigateBack({
				    delta: 1
				});
			},
			// bindTextAreaBlur: function (e) {
			           
			// 			var value=e.detail.value
			// 			 console.log(value)
			//         },
			clickRight(){
				uni.navigateTo({
					url:"./sign-up"
				})
				// console.log("点击了右侧按钮")
			},
			
		}
	}
</script>

<style scoped>
	.main{
		position: fixed;
		background:  #e9e9e9;
		height: 100%;
		width: 100%;
		top: 0px;
		left: 0;
	}
	.left{
		font-size: 18px;
	}
	.uni-textarea textarea{
		height: 200px;
		background-color: #fff;
	}
	.uni-textarea>view:first-child{
		background:  #e9e9e9;
		color: #95C936;
		padding: 5px 10px;
		display: flex;
		justify-content: flex-end;
	}
	.uni-textarea>view:last-child{
		background:  #e9e9e9;
		color: #686868;
		padding: 10px;
	}
</style>