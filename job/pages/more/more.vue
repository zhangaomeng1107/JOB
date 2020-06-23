<template>
	<view>
		<topNav :iswz="iswz" :title="title" :wz="wz"></topNav>
		<block v-for="(item,index) in list" :key="index">
			<search-recruit :item="item" :index="index"></search-recruit>
		</block>
	</view>
</template>

<script>
	import topNav from '../../components/top-nav/top-nav.vue'
	import searchRecruit from '../../components/search-recruit/search-recruit.vue'
	export default {
		components:{
			topNav,
			searchRecruit
		},
		data() {
			return {
				title:"靠谱职位",
				wz:"定位中",
				iswz:false,
				list:[]
			}
		},
		onLoad(){
			uni.request({
			    url: 'api/job_api/public/index.php/api/position/index', //仅为示例，并非真实接口地址。
				method:"POST",
			    data: { 
					"pagesize":10,
			    },
			    success: (res) => {
						// console.log(res.data);
						// this.list = res.data;
						this.list=res.data.data.data
						console.log(this.list)
			    }
			});
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
