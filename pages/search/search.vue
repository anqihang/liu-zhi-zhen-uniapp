<template>
	<view style="box-sizing:border-box;display:flex;flex-direction:column;background-color: #f2f2f2;height: 100vh;position: relative;border-top: 15rpx solid #919191;">
		<view class="title">
				寻房测温
				<view class="icon">
					<image  :mode="aspectFix" src="../../static/refresh0.svg"></image>
				</view>
		</view>
		<view class="refresh">
			<view class="icon"><image color="#939393" :mode="aspectFix" src="../../static/refresh0.svg"></image></view>
			<view class="text">暂无测温数据</view>
			<view class="button">
				<button style="background-color: #939393;width:100rpx;color:white;">搜索</button>
			</view>
		</view>
		<TabBar :current="1"></TabBar>
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
	.title {
		position: relative;
		height: 41rpx;
		width: 100%;
		background-color: #c2c2c2;
		text-align: center; 
		line-height: 41rpx;
		font-size:17rpx;
		.icon {
			width: 35px;
			float:left;
			height: 100%;
			image{
				width:100%;
				height:100%;
				}
			}
	}
	.refresh{
		position: relative;
		height: 100%;
		flex:1;
		width: 100%;		
		display: flex;
		justify-content: center;
		flex-direction: column;
		align-items: center;
		.icon{
			width: 100rpx;
			height: 100rpx;
			image{
				width:100%;
				height:100%;
			}
		}
		.text{
			margin-top:15rpx;
			letter-spacing: 2rpx;
			color: #7f7f7f;
		}
		.button{
			margin-top: 30rpx;
		}
		
	}
</style>
