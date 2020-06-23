<template>
	<view>
		<view class="listCount">
		    <checkbox-group @change="checkboxChange">
		        <label class="listItem" v-for="(item,index) in carArr" :key="item.value">
		            <view class="checkBox">
		                <checkbox style="transform:scale(0.9)" :value="item.value" :checked="item.checked"/>
						<search-recruit :item="item" :index="index" :isshow="isshow"></search-recruit>
		            </view>
		        </label>
		    </checkbox-group>
		</view>
		<!-- 全选按钮 -->
		<checkbox-group @change="changeBook">
		    <label>
		        <checkbox style="transform:scale(0.9)" :checked="allFlag.checked" :value="allFlag.cb"/> 全选
		    </label>
		</checkbox-group>
	</view>
</template>

<script>
	import searchRecruit from '../../components/search-recruit/search-recruit.vue'
	export default {
		components:{
			searchRecruit
		},
		data() {
			return {
				allFlag: {
				    value: 'cb',
				    checked: false,
					
				},
				isshow:true,
				carArr: [
				    {
						condition:"直招优秀派单员，只限女生",
						money:"180元/天",
						place:"云龙",
						date:"长期可做",
						safe:"工作保障",
						way:"周结",
				        whether: true,
						value: '1',
				    },
				    {
				        value: '2',
				       condition:"直招优秀派单员，只限女生",
				       money:"180元/天",
				       place:"云龙",
				       date:"长期可做",
				       safe:"工作保障",
				       way:"周结",
				       whether: true,
				    },
				    {
				        value: '3',
				       condition:"直招优秀派单员，只限女生",
				       money:"180元/天",
				       place:"云龙",
				       date:"长期可做",
				       safe:"工作保障",
				       way:"周结",
				       whether: true,
				    },
				    {
				        value: '4',
				        condition:"直招优秀派单员，只限女生",
				        money:"180元/天",
				        place:"云龙",
				        date:"长期可做",
				        safe:"工作保障",
				        way:"周结",
				        whether: true,
				    },
				    {
				        value: '5',
				       condition:"直招优秀派单员，只限女生",
				       money:"180元/天",
				       place:"云龙",
				       date:"长期可做",
				       safe:"工作保障",
				       way:"周结",
				       whether: true,
				    },
				    {
				        value: '6',
				        condition:"直招优秀派单员，只限女生",
				        money:"180元/天",
				        place:"云龙",
				        date:"长期可做",
				        safe:"工作保障",
				        way:"周结",
				        whether: true,
				    },
				    {
				        value: '7',
				        condition:"直招优秀派单员，只限女生",
				        money:"180元/天",
				        place:"云龙",
				        date:"长期可做",
				        safe:"工作保障",
				        way:"周结",
				        whether: true,
				    },
				]
			}
		},
		methods: {
			changeBook (e) {
			    if (e.detail.value.length == 0) {
			        this.carArr.map(item => this.$set(item, 'checked', false))
			        this.$set(this.allFlag, 'checked', false)
			    } else {
			        this.carArr.map(item => this.$set(item, 'checked', true))
			        this.$set(this.allFlag, 'checked', true)
			    }
			},
			// list checkbox
			checkboxChange (e) {
				var items = this.carArr,
					values = e.detail.value;
				for (var i = 0, lenI = items.length; i < lenI; ++i) {
					const item = items[i]
					if(values.includes(item.value)){
						this.$set(item,'checked',true)
					}else{
						this.$set(item,'checked',false)
					}
				}
				//  商品是否全部勾选，判断全选与否状态
				var offCarArr = []
				this.carArr.forEach(item => item.whether == true? offCarArr.push(item): '')
				let allChecks = offCarArr.every(item => item.checked == true)     
				allChecks ? this.$set(this.allFlag, 'checked', true) :this.$set(this.allFlag, 'checked', false)
			},
		}
	}
</script>

<style>

</style>
