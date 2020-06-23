<template>
	<view class="mian">
		<form @submit="submit">
			<view class="pic">
				<view class="u-f-jsb">
					<view class="wz u-f-ac">头像</view>
					<view class=""><image src="../../static/img/20.jpg" mode="widthFix"></image> </view>
				</view>
			
				<view class="u-f-ac">
					<view class="wz">姓名</view>
					<input type="text" value="" placeholder="请输入你的姓名" name="user"/>
				</view>
			</view>
			<view class="tel">
				<view class="u-f-jsb">
					<view class="u-f-ac">
						<view class="wz">手机号</view>
						<input type="text" value="" placeholder="请输入手机号" name="tel"/>
					</view>
					<button type="default">获取短信验证码</button>
				</view>
			
					
				<view class="u-f-ac">
					<view class="wz">验证码</view>
					<input type="text" value="" placeholder="请输入验证码" name="pwd"/>
				</view>
			</view>
			<view class="btn">
				<button type="default" form-type="submit">完成并报名</button>
			</view>
		</form>
	</view>
</template>

<script>
	var  graceChecker = require("../../common/graceChecker.js");
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			submit(e){
				//定义表单规则
				var rule = [
					{name:"user", checkType : "notnull", checkRule:"",  errorMsg:"请输入姓名"},
					{name:"tel", checkType : "notnull", checkRule:"",  errorMsg:"请输入手机号"},
					{name:"pwd", checkType : "notnull", checkRule:"",  errorMsg:"请输入密码"}
				];
				//进行表单验证
				var formData = e.detail.value;
				var checkRes = graceChecker.check(formData, rule);
				if(checkRes){
					console.log(e)
					this.username =e.detail.value.user;
					this.tel =e.detail.value.tel;
					this.pwd =e.detail.value.pwd;
					uni.request({
					    url: '/api/job_api/public/api/login/register', //仅为示例，并非真实接口地址。
						method:"POST",
					    data: {
							username:this.username,
							tel:this.tel,
							password:this.pwd,
							pid:"2"
					    },
					    success: (res) => {
							console.log(res)
					       if(res.data.status==1){
							   uni.showToast({
							       title: "报名成功",
							       duration:1000
							   });
							   setTimeout(function(){
								   uni.redirectTo({
								       url:'../success/success'
								   });
							   },1000);
						   }else{
							   uni.showToast({
							       title: "报名失败",
							       duration:1000,
								   icon: "none"
							   });
						   }
					    }
					});
					
					
				 //    uni.showToast({title:"注册成功！", icon:"none"});
					// uni.reLaunch({
					//     url: '../login/login'
					// });
				}else{
				    uni.showToast({ title: graceChecker.error, icon: "none" });
				}
				
			},
		}
	}
</script>

<style scoped>
	.mian{
		
		background: #E9E9E9;
		height: 100vh;
	}
	.pic,.tel{
		background: #fff;
	}
	.pic{
		border-bottom: 5px solid #E9E9E9;
	}
	.pic image{
		border-radius: 50%;
		width: 60px;
		border: 1px solid #95C936;
	}
	.pic>view:first-child,.tel>view:first-child{
		border-bottom: 1px solid #E9E9E9;
	}
	.pic>view,.tel>view{
		padding: 10px;
	}
	.wz{
		font-size: 16px;
		width: 22%;
	}
	.tel>view:first-of-type .wz{
		width: 40%!important;
	}

	.tel button{
		height: 31px;
		line-height: 31px;
		width: 30%;
		padding: 0  !important ;
		margin: 0 !important;
		font-size: 12px;
		background: #95C936;
		color: #fff;
	}
	.btn button{
		margin-top: 80px;
		width: 50%;
		height: 40px;
		line-height: 40px;
		color: #fff;	
		background: linear-gradient(#5e9201,#b8dc44);
	}
</style>
