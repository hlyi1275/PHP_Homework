<template>
	<view class="d-clo d-ai-centen">
		<view class="width100">
			<u-cell-group>
				<u-field  v-model="form.name" label="联系人" placeholder="请填写姓名" > </u-field>
				<u-field  v-model="form.age" label="年龄" placeholder="请填写年龄" > </u-field>
				
				<view class="width100 d-row d-jc-end border-bottom-1" style="margin-left: 28rpx;"></view>
				
				<view class="width95 d-row margin-center padding-10 height120 line-height120">
					<label class="width20">性别</label>
					<view class="d-row d-jc-between width60">
						<view class="width45"> <button plain :type="butt?'primary':''" @tap="butt = !butt">先生</button> </view>
						<view class="width45"> <button plain :type="butt?'':'primary'" @tap="butt = !butt">女士</button> </view>
					</view>
					
				</view>  
				
				<u-field  v-model="form.mobile" label="手机号" placeholder="请填写手机号" > </u-field>
				
			</u-cell-group>
		</view>
		
		<view class="submit" :class="{'bg-blue':isShow,colorWhite:isShow}" @tap="submit">
			提交申请
		</view>
		
		
		<!-- 提示框 -->
		<u-toast ref="uToast" />
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				butt:true,
				form:{
					name:null,
					age:null,
					mobile:null
				}
			}
		},
		watch:{
			
		},  
		computed: {
			isShow(){
				return  (this.form.name != null 
							&& this.form.age != null 
							&& this.form.mobile != null) ? true:false
			}
		},
		methods: {
			submit(){
				if(this.isShow){
					this.$refs.uToast.show({
						title: '提交成功',
						type: 'success',
						position:'center',
						duration:'1000'
					})
				}
			}
		}
	}
</script>

<style>
.submit{
	background-color: #f7f7f7;
	color: #a5a5a5;
	width: 90%;
	height: 100rpx;
	margin: 0 auto;
	border-radius: 60rpx;
	
	position: fixed;
	bottom: 30rpx;
	left: 5%;
	z-index: 1000;
	
	text-align: center;
	line-height: 100rpx;
	font-size: 32rpx;
}
</style>
