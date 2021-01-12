<template>
	<view class="d-clo d-ai-centen">
		<view class="width100">
			<u-cell-group>
				<u-field  v-model="form.address" type="textarea" label="店铺地址" placeholder="请填写详细店铺地址" > </u-field>
				<u-field  v-model="form.name" label="联系人" placeholder="请填写姓名" > </u-field>
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
				form:{
					address:null,
					name:null,
					mobile:null
				}
			}
		},
		watch:{
			
		},
		computed: {
			isShow(){
				return  (this.form.address != null 
							&& this.form.name != null 
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
