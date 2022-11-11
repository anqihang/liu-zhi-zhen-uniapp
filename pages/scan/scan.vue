<template>
	<view
		style="box-sizing:border-box;display:flex;flex-direction: column; #f2f2f2;height: 100vh;position: relative;border-top: 15rpx solid #919191;background-color:#f2f2f2;">
		<van-nav-bar @click-left="toHome" title="扫码" left-arrow></van-nav-bar>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		},
		onLoad(){
			uni.scanCode({
				success(res) {
					console.log(res);
					if(res.result){
						
						uni.navigateTo({
							url:"/pages/bind/bind",
							success(res0){
								res0.eventChannel.emit('getDeviceId',{id:res.result})
							}
						})
					}
				}
			})
		},
		methods: {
			scan() {
				uni.scanCode({

				})
			},
				
		}
	}
</script>

<style lang="scss">
	.custom-class {
		background-color: #c2c2c2 !important;
	}

	.van-nav-bar {
		padding: 0 !important;
		background-color: #c2c2c2 !important;
	}

	
</style>
