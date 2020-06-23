<template>
	<view>
		<uniNavBar fixed="true" statusBar="true" left-icon="closeempty"  shadow="true" 
		color="#fff" background-color="#95c936" right-icon="more-filled" @clickLeft="close" @clickRight="openList">
				<view slot="left" class="left">{{title}}</view>
				<template v-if="iswz">
					<view class="dw">{{wz}}</view>
				</template>
		</uniNavBar>
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
		props:{
			title:String,
			wz:String,
			iswz:Boolean
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
			openList(){
				console.log("点击了右侧按钮")
			}
		}
	}
</script>

<style scoped>
	.left{
		font-size: 18px;
	}
</style>
