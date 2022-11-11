<template>
	<view style="box-sizing:border-box;background-color: #f2f2f2;height: 100vh;position: relative;border-top: 15rpx solid #919191;">
		<view class="avatar">
			<image :mode="aspectFix" src="../../static/logo.png"></image>
		</view>
		<view class="name">张三</view>
		<view class="cell">
			<van-cell-group inset>
				<van-cell title="科室列表" size="large" is-link></van-cell>
			</van-cell-group>
			<van-cell-group inset>
				<van-cell title="账户设置" is-link></van-cell>
			</van-cell-group>
		</view>
		<TabBar :current="2"></TabBar>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.van-cell{
		height: 90rpx;
		margin-bottom: 30rpx;
		border-radius: 20rpx;
		.van-cell__title{
			font-size: 25rpx!important;
			line-height: 55rpx;
		}
		.van-icon{
			font-size: 25rpx;
		}
	}
	
	
	.avatar {
		margin: 70rpx auto 20rpx;
		width: 80rpx;
		height: 80rpx;
		background-color: red;
		display: flex;
		flex-direction: column;
		border-radius: 50%;
		overflow: hidden;

		image {
			width: 100%;
			height: 100%;
		}
	}

	.name {
		font-size: 25rpx;
		margin: 0 auto;
		text-align: center;
		margin-bottom: 50rpx;
	}

	.custom-class {
		height: 70rpx;
		margin-bottom: 40rpx !important;
		border-radius: 20rpx;
	}
	.van-cell{
		display: flex;
		align-items: center;
	}
	
</style>
